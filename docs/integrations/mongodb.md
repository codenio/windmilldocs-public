---
description: How do I connect MongoDB to Windmill? Query and manage MongoDB databases from scripts and flows using the official drivers.
---

# MongoDB integration

[MongoDB](https://www.mongodb.com/) is a NoSQL document-oriented database.

This guide shows how to create a connection from your Windmill instance to a
MongoDB database (self-hosted or [MongoDB Atlas][mongodb-atlas]), then use it to
make queries with the official MongoDB drivers.

:::caution Atlas Data API deprecation

Previous versions of this guide relied on the MongoDB Atlas Data API through the
`mongodb_rest` resource type. MongoDB [shut down the Atlas Data API][mongo-data-api-eol]
on September 30, 2025, so that resource type no longer works. Use the `mongodb`
resource type with the official drivers as shown below instead.

:::

![Integration between MongoDB and Windmill](../assets/integrations/0-header.png.webp 'Connect a MongoDB database with Windmill')

## Create resource

Windmill provides integration with many different apps and services with the use
of [Resources][docs-resources]. Each Resource has a **Resource type**, which
controls the shape of it. To be able to connect to a MongoDB instance, we'll
need to define a Resource with the [mongodb](https://hub.windmill.dev/resource_types/22/mongodb) Resource Type.

:::tip

You can find a list of all the officially supported Resource types on
[Windmill Hub][hub-resources].

:::

Head to the Resources page in the Windmill app, click on
"Add resource" in the top right corner and select the `mongodb` type, then
provide the following parameters:

| Property           | Type    | Description                | Default     | Required | Where to Find           | Additional Details                                  |
| ------------------ | ------- | -------------------------- | ----------- | -------- | ----------------------- | --------------------------------------------------- |
| db                 | string  | Database name              |             | true     | MongoDB Atlas Dashboard | Name of the database you want to connect to         |
| tls                | boolean | Use TLS for connections    | true        | false    | Your own preference     | Set to true for secure connections                  |
| servers            | array   | Array of server objects    |             | true     | MongoDB Atlas Dashboard | Each server object should contain `host` and `port` |
| host (nested)      | string  | Server address             |             | true     | MongoDB Atlas Dashboard | Hostname of the MongoDB instance                    |
| port (nested)      | integer | Port number                | 27017       | false    | MongoDB Atlas Dashboard | Default MongoDB port is `27017`                     |
| credential         | object  | Authentication information |             | true     | MongoDB Atlas Dashboard | Contains `username`, `password`, `db`, `mechanism`  |
| username (nested)  | string  | Database username          |             | true     | MongoDB Atlas Dashboard | Your database user's username                       |
| password (nested)  | string  | Database password          |             | true     | MongoDB Atlas Dashboard | Your database user's password                       |
| db (nested)        | string  | Authentication database    |             | true     | MongoDB Atlas Dashboard | The database used for authentication                |
| mechanism (nested) | string  | Authentication mechanism   | SCRAM-SHA-1 | false    | Your own preference     | Default authentication mechanism is `"SCRAM-SHA-1"` |

On MongoDB Atlas, you can find the hostnames of your cluster from the Atlas
dashboard under "Connect" > "Drivers": they are the hosts listed in the
connection string.

## Create script

Next, let's create a Script that uses the newly created Resource. Head on to
the [Home][wm-app-home] page, click **New** and select **Script**. The examples
below query a collection and return the matching documents, with support for
querying by `_id` (which is stored as an ObjectId, a special type in MongoDB
that needs an explicit conversion).

In TypeScript (Bun), using the official [mongodb npm driver](https://www.npmjs.com/package/mongodb):

```typescript
import { MongoClient, ObjectId } from 'mongodb';

type Mongodb = {
	db: string;
	tls: boolean;
	servers: { host: string; port: number }[];
	credential: { username: string; password: string; db: string; mechanism: string };
};

export async function main(
	auth: Mongodb,
	collection: string,
	filter: Record<string, any>
) {
	const hosts = auth.servers.map((s) => `${s.host}:${s.port ?? 27017}`).join(',');
	const client = new MongoClient(`mongodb://${hosts}`, {
		tls: auth.tls,
		auth: {
			username: auth.credential.username,
			password: auth.credential.password
		},
		authSource: auth.credential.db
	});

	try {
		if ('_id' in filter) {
			filter['_id'] = new ObjectId(filter['_id']);
		}
		const documents = client.db(auth.db).collection(collection);
		return await documents.find(filter).toArray();
	} finally {
		await client.close();
	}
}
```

Or in Python, using [PyMongo](https://pypi.org/project/pymongo/):

```python
from pymongo import MongoClient
from bson.objectid import ObjectId

mongodb = dict


def main(auth: mongodb, collection: str, filter: dict):
    hosts = ",".join(
        f"{s['host']}:{s.get('port', 27017)}" for s in auth["servers"]
    )
    client = MongoClient(
        f"mongodb://{hosts}",
        tls=auth["tls"],
        username=auth["credential"]["username"],
        password=auth["credential"]["password"],
        authSource=auth["credential"]["db"],
    )
    try:
        if "_id" in filter:
            filter["_id"] = ObjectId(filter["_id"])
        documents = client[auth["db"]][collection]
        return [{**doc, "_id": str(doc["_id"])} for doc in documents.find(filter)]
    finally:
        client.close()
```

In case you are using the [sample dataset][mongo-sample-data] of MongoDB Atlas,
you'll have a `sample_restaurants` database filled with restaurants. To make a
query for a specific restaurant name, the arguments of the Script would look
like the following (**casing matters**):

- **auth** - select the Resource we created in the previous step
  (`my_mongodb`)
- **collection** - `restaurants`
- **filter** - `{ "name": "Nordic Delicacies" }` (or by ID:
  `{ "_id": "5eb3d668b31de5d588f4293b" }`)

After filling the inputs, try running the Script by clicking "Test" or pressing
`Ctrl` + `Enter`. You should see exactly one restaurant returned.

:::tip

You can find more Script examples related to MongoDB on
[Windmill Hub][hub-mongo].

:::

Once you're done, click on "Save", which will save it to your workspace. You can
now use this Script in your [Flows][docs-flows], [Apps][docs-apps] or as
standalone.

<!-- Links -->

[wm-app-resources]: https://app.windmill.dev/resources
[wm-app-home]: https://app.windmill.dev
[hub-resources]: https://hub.windmill.dev/resource_types
[hub-mongo]: https://hub.windmill.dev/?app=mongodb
[docs-resources]: /docs/core_concepts/resources_and_types
[docs-path]: /docs/core_concepts/roles_and_permissions#path
[docs-flows]: /docs/getting_started/flows_quickstart
[docs-apps]: /docs/getting_started/apps_quickstart
[mongodb-atlas]: https://www.mongodb.com/atlas/database
[mongo-data-api-eol]: https://www.mongodb.com/docs/atlas/app-services/data-api/data-api-deprecation/
[mongo-sample-data]: https://www.mongodb.com/docs/atlas/sample-data/

---
description: How do I connect Airtable to Windmill? Manage and organize data in Airtable from scripts and flows.
---

import ResourceUsage from './_resource_usage.mdx';

# Airtable integration

[Airtable](https://www.airtable.com/) is a cloud collaboration platform for organizing and managing data.

There are two resources associated with Airtable. Both are required to use Airtable's API from Windmill.

## Airtable account

<video
 className="border-2 rounded-xl object-cover w-full h-full dark:border-gray-800"
  autoPlay
  loop
  controls
  src="/videos/adding_airtable_resource.mp4"
/>
<br/>

Airtable authenticates with personal access tokens (legacy API keys were removed in February 2024). Create a token on Airtable's <a href="https://airtable.com/create/tokens" rel="nofollow">Builder hub</a>, grant it the scopes you need (e.g. `data.records:read`, `data.records:write`) and access to the bases you want to use, then paste it on Windmill as the `apiKey` field of the resource.

| Property | Type   | Description                    | Default           | Required | Where to find                                        |
| -------- | ------ | ------------------------------ | ----------------- | -------- | ---------------------------------------------------- |
| apiKey   | string | Airtable personal access token | patXXXXXXXXXXXXXX | true     | airtable.com/create/tokens > Create token            |

## Airtable table

<video
    className="border-2 rounded-xl object-cover w-full h-full dark:border-gray-800"
    autoPlay
    loop
    controls
    src="/videos/adding_airtable_table.mp4"
/>
<br/>

Now specify Airtable which database and table you want to interact with:

- **Database ID** can be found on the URL of the page. It starts with "app" and ends before the next "/". e.g. appcy7pfdzgJIhto.
- **Table name** is the name of the tab. By default it is called "Table 1".

| Property  | Type   | Description                                    | Required | Where to find                              |
| --------- | ------ | ---------------------------------------------- | -------- | ------------------------------------------ |
| baseId    | string | Unique identifier for a specific Airtable base | True     | Page URL                                   |
| tableName | string | Name of an individual table within that base   | True     | In Airtable. Name of the tab of a database |

<ResourceUsage name="Airtable" hub="airtable" />


---
description: FaunaDB integration is deprecated. The Fauna cloud service was shut down in May 2025.
---

# FaunaDB integration (deprecated)

:::caution Fauna service shutdown

The Fauna cloud service was [shut down at the end of May 2025](https://www.infoq.com/news/2025/03/fauna-shuts-down/). The `faunadb` resource type only worked with the hosted service and can no longer be used. The core database was [released as open source](https://github.com/fauna/faunadb), but it does not expose the same hosted API this integration relied on.

If you are migrating off Fauna, you can connect Windmill to alternatives such as [PostgreSQL](../getting_started/0_scripts_quickstart/5_sql_quickstart/index.mdx), [MongoDB](./mongodb.md) or [Supabase](./supabase.md).

:::

FaunaDB was a serverless, document-oriented database. The integration relied on a [resource](../core_concepts/3_resources_and_types/index.mdx) with a `region` and a `secret` API key, both obtained from the Fauna dashboard, which no longer exists.

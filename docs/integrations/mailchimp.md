---
description: How do I connect Mailchimp to Windmill? Manage email campaigns and audiences from scripts and flows.
---

import ResourceUsage from './_resource_usage.mdx';

# Mailchimp integration

[Mailchimp](https://mailchimp.com/) is an all-in-one marketing platform for small businesses.

:::info Using emails to trigger scripts & flows

To trigger scripts and flows by emails using Mailchimp, refer to the [Mailchimp Mandrill Integration](./mailchimp_mandrill.md) for seamless integration.

:::

To integrate Mailchimp to Windmill, you need to save the following elements as a [resource](../core_concepts/3_resources_and_types/index.mdx).

![Add Mailchimp Resource](../assets/integrations/add-mailchimp.png.webp)

| Property | Type   | Description                                             | Default | Required | Where to Find                                          |
| -------- | ------ | ------------------------------------------------------- | ------- | -------- | ------------------------------------------------------ |
| api_key  | string | Mailchimp API key                                       |         | false    | Mailchimp > Account > Extras > API keys > Create A Key |
| server   | string | The data center for your Mailchimp account (e.g., us12) |         | false    | Found in your API key (e.g., "us12" in "123abc-us12")  |

<ResourceUsage name="Mailchimp" hub="mailchimp" />


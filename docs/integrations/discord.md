---
description: How do I connect Discord to Windmill? Send messages and automate Discord webhooks from scripts and flows.
---

import ResourceUsage from './_resource_usage.mdx';

# Discord integration

[Discord](https://discord.com/) is a voice, video, and text communication platform.

<video
    className="border-2 rounded-xl object-cover w-full h-full dark:border-gray-800"
    autoPlay
    loop
    controls
    id="main-video"
    src="/videos/adding_discord_resource.mp4"
/>
<br/>

To integrate Discord to Windmill, you need to save the following elements as a [resource](../core_concepts/3_resources_and_types/index.mdx).

| Property    | Type   | Description             | Default | Required | Where to Find                                                                               |
| ----------- | ------ | ----------------------- | ------- | -------- | ------------------------------------------------------------------------------------------- |
| webhook_url | string | The Discord webhook URL |         | true     | Discord Server > Server Settings > Integrations > Webhooks > Create Webhook or Edit Webhook |

<br/>

Windmill also defined a [resource type](https://hub.windmill.dev/resource_types/104/discord_bot_configuration) for Discord bots. An example is given by our [Documentation Discord bot using Supabase and OpenAI's GPT to help support teams](/blog/knowledge-base-discord-bot) tutorial.


:::tip Windmill Discord

Windmill has its own Discord server for its community, questions and collaborations.

Join following [this link](https://discord.com/invite/V7PM2YHsPB).

:::

<ResourceUsage name="Discord" hub="discord" />


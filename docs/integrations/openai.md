---
description: How do I connect OpenAI to Windmill? Use OpenAI APIs for text generation and AI tasks from scripts and flows.
---

import ResourceUsage from './_resource_usage.mdx';

# OpenAI integration

[OpenAI](https://openai.com/) is an artificial intelligence service provider.

<video
    className="border-2 rounded-xl object-cover w-full h-full dark:border-gray-800"
    autoPlay
    loop
    controls
    id="main-video"
    src="/videos/adding_openai_resource.mp4"
/>

<br/>

:::info Windmill AI

An OpenAI resource can also power [Windmill AI](../core_concepts/22_ai_generation/index.mdx) (AI chat in the code and flow editors) and [AI agent steps](../core_concepts/22_ai_generation/index.mdx) in flows. OpenAI is one of the supported AI providers, alongside Anthropic, Google AI, Mistral, Groq, OpenRouter and others.

:::

To integrate OpenAI to Windmill, you need to save the following elements as a [resource](../core_concepts/3_resources_and_types/index.mdx).

| Property        | Type   | Description                                                                                                    | Default | Required | Where to Find                                                          |
| --------------- | ------ | -------------------------------------------------------------------------------------------------------------- | ------- | -------- | ---------------------------------------------------------------------- |
| api_key         | string | API key for OpenAI                                                                                             |         | true     | OpenAI Dashboard > API Keys > Create new key or view existing keys     |
| organization_id | string | Only needed for users who belong to multiple organizations and want to use an organization other than default  |         | false    | OpenAI Dashboard > Account Settings > Organizations > Organization ID  |
| base_url        | string | Custom API base URL, for OpenAI-compatible endpoints (Azure OpenAI, local models, proxies)                     | `https://api.openai.com/v1` | false    | Your OpenAI-compatible provider's documentation                        |

<ResourceUsage name="OpenAI" hub="openai" />


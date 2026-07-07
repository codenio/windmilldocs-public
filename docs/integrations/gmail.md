---
description: How do I connect Gmail to Windmill? Send and read emails via the Gmail API from scripts and flows.
---

import ResourceUsage from './_resource_usage.mdx';

# Gmail integration

[Gmail](https://mail.google.com/mail/) is a free email service provided by Google.

<video
    className="border-2 rounded-xl object-cover w-full h-full dark:border-gray-800"
    autoPlay
    loop
    controls
    id="main-video"
    src="/videos/adding_gmail_resource.mp4"
/>

<br/>

The Gmail integration is done through OAuth. You just need to sign in from your Google account on your browser. The access will be automatically saved to the workspace as a [resource](../core_concepts/3_resources_and_types/index.mdx).

On [self-hosted instances](../advanced/1_self_host/index.mdx), integrating an OAuth API will require [Setup OAuth and SSO](../advanced/27_setup_oauth/index.mdx).

<ResourceUsage name="Gmail" hub="gmail" />


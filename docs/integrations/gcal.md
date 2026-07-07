---
description: How do I connect Google Calendar to Windmill? Manage events and schedules via the Google Calendar API.
---

import ResourceUsage from './_resource_usage.mdx';

# Google Calendar integration

[Google Calendar](https://calendar.google.com/)  is a time-management and scheduling web application.

<video
    className="border-2 rounded-xl object-cover w-full h-full dark:border-gray-800"
    autoPlay
    loop
    controls
    id="main-video"
    src="/videos/adding_gcal_resource.mp4"
/>

<br/>

The Google Calendar integration is done through OAuth. You just need to sign in from your Google account on your browser. The access will be automatically saved to the workspace as a [resource](../core_concepts/3_resources_and_types/index.mdx).

On [self-hosted instances](../advanced/1_self_host/index.mdx), integrating an OAuth API will require [Setup OAuth and SSO](../misc/2_setup_oauth/index.mdx).

<ResourceUsage name="Google Calendar" hub="gcal" />

## Native triggers

You can use [native triggers](../core_concepts/66_native_triggers/index.mdx) to automatically run scripts or flows when calendar events are created, updated, or deleted. Native triggers receive real-time push notifications so your runnables execute as soon as events occur.


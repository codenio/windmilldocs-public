---
description: How do I connect Google Workspace to Windmill? Manage users, groups, org units and security via the Google Admin Directory API.
---

import ResourceUsage from './_resource_usage.mdx';

# Google Workspace integration

[Google Workspace](https://workspace.google.com/) is Google's suite of cloud collaboration tools. The `gworkspace` resource type provides OAuth access to the Google Admin Directory API for managing users, groups, org units, and security settings.

The Google Workspace integration is done through OAuth. You just need to sign in from your Google account on your browser. The access will be automatically saved to the workspace as a [resource](../core_concepts/3_resources_and_types/index.mdx).

The default OAuth scopes are:

- `https://www.googleapis.com/auth/admin.directory.group`
- `https://www.googleapis.com/auth/admin.directory.user`
- `https://www.googleapis.com/auth/admin.directory.user.security`
- `https://www.googleapis.com/auth/admin.directory.orgunit`

On [self-hosted instances](../advanced/1_self_host/index.mdx), integrating an OAuth API will require [Setup OAuth and SSO](../misc/2_setup_oauth/index.mdx).

<ResourceUsage name="Google Workspace" hub="gworkspace" />

## Native triggers

The `gworkspace` resource type is also used by Google [native triggers](../core_concepts/52_native_triggers/index.mdx) to watch for changes in Google Drive and Google Calendar. When configured through the native triggers workspace integration, the resource is created with different scopes (`drive.readonly`, `calendar.readonly`, `calendar.events`) tailored to receiving push notifications.


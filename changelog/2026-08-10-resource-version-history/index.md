---
slug: resource-version-history
title: Version history for resource values
tags: ['Resources', 'Workspace']
description: Editing a resource no longer destroys the value it replaced. Every change to a resource's value is now kept as a version, browsable from a History drawer in the resource editor with a diff against the current value and a one-click restore. Recording happens at the database level, so it covers writes from the UI, the CLI, setResource, workspace forks and trashbin restores alike. Past values stay readable to anyone who can read the resource, so after rotating a credential that was inlined into a resource value rather than kept in a variable, follow the rotation with "Clear past versions".
features:
  [
    'History drawer in the resource editor: versions newest first, each with its author and date, a JSON value view and a "Diff with current" view',
    'Restore any version with write access to the resource. The old value is written forward as a new version, so the history stays append-only and the restore is itself attributable',
    'A version referencing a $var: or $res: path that no longer exists is flagged before you restore it',
    'Recorded by a database trigger, so CLI pushes, setResource calls, workspace forks and trashbin restores all produce versions, not just edits made in the editor',
    'Up to 100 versions per resource, trimmed in the background. Renaming carries the history along, deleting a resource takes it with it',
    'state and cache resources are not versioned: every job that uses them rewrites them',
    '"Clear past versions" drops every version but the current value for one resource, for owners of its path. On cloud, workspace admins can prune every resource history at once from the quotas page',
    'Four API endpoints: getResourceHistory, getResourceVersion, restoreResourceVersion and clearResourceHistory',
  ]
docs: /docs/core_concepts/resources_and_types#version-history
---

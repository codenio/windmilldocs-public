---
slug: merge-into-any-workspace
title: Compare & Deploy into any workspace
tags: ['Workspace']
description: Compare & Deploy now accepts an arbitrary target workspace, not just the parent. Pick it from the destination badge in the merge header, compute a full diff over both workspaces, and deploy the items you select one way into the target. Requires being an admin of both workspaces. The Deployment UI settings tab is now part of Dev workspace.
features:
  [
    'Pick any workspace you administer as the deployment target from the destination badge, or with /forks/compare?target=<workspace id>',
    'A pair outside the fork lineage has no continuously tracked diff: compute one explicitly, then Recompute to refresh it - the card shows when it was last computed',
    'Comparisons outside the lineage are one-way (current workspace into the target), so the update direction and conflicts are hidden',
    'Items that exist only in the target are flagged "Removes in target" and must be selected one by one',
    'A workspace with no parent lands directly on the target picker',
    'The Deployment UI settings tab, with its deployable-item filters, moved under Dev workspace',
  ]
docs: /docs/advanced/workspace_forks#merging-into-a-workspace-outside-the-lineage
---

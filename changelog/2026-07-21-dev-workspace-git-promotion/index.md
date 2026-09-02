---
slug: dev-workspace-git-promotion
title: Promote to prod via Git from dev workspaces
tags: ['Git sync', 'Workspace', 'Enterprise']
description: Dev workspaces can now promote to prod through Git. A "Promote to prod via Git" toggle on the repository inherited from prod switches deploys from the dev branch to per-item wm_deploy branches off the prod workspace's tracked branch, ready to merge as pull requests. Enterprise Edition only, and the dev workspace must use the same repository and branch as its prod workspace.
features:
  [
    '"Promote to prod via Git" toggle on the repository a dev workspace inherited from its prod workspace, no separate promotion repository to configure',
    'Deploys create per-item wm_deploy/<dev-workspace-id>/<type>/<path> branches off the branch tracked by the prod workspace',
    'Optional "One pull request per folder" sub-toggle to open one branch per folder instead of per item',
    'On GitHub App-backed repositories, Windmill can open the pull request automatically after each deploy, without any CI action or webhook',
    'The dev workspace''s own branch keeps tracking the workspace while promotion is on',
  ]
docs: /docs/advanced/dev_workspaces#promote-to-prod-via-git
---

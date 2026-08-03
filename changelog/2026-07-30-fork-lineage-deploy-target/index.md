---
slug: fork-lineage-deploy-target
title: One deployment target, derived from the workspace lineage
tags: ['Workspace']
description: The workspace-level "deploy to" setting is gone. A workspace now deploys into its parent - the workspace it was forked from, or the prod workspace its dev workspace is paired with - so the deployment target has a single definition instead of two that could disagree. There is nothing to do on upgrade to Windmill 1.776.0, since a staging workspace that was the only one deploying into prod simply becomes prod's dev workspace. Only two shapes need a look, and both are named in the migration logs. Job tags became lineage-aware at the same time, so $workspace in a tag resolves to the nearest ancestor workers are actually provisioned for.
features:
  [
    'A workspace deploys into its parent: a fork into the workspace it was forked from, a dev workspace into the prod workspace it is paired with. There is no longer a setting linking two otherwise unrelated workspaces',
    'The Deployment UI settings tab is gone. Its deployable-item filters live under Workspace settings -> Dev workspace, alongside the now read-only target',
    "Nothing to do on upgrade for the usual setup: a staging workspace that was the only one deploying into prod becomes prod's dev workspace and keeps its own job tags and promotion mode",
    'Only two shapes need a look, both named individually in the migration logs: several workspaces pointing at one target (only one can be its dev workspace, the rest become plain forks), and a link the lineage cannot express at all (target missing or archived, self-reference, source already a fork of something else, cycle), which is dropped',
    'Either way the fix is a single attach of the staging workspace as the dev workspace of the prod workspace - there is no other setting to reproduce',
    '$workspace in a job tag, and per-workspace default tags, now resolve to the nearest ancestor an admin would provision workers for, instead of a generated fork id no worker serves',
    'For a one-off deploy into an unrelated workspace, pick an explicit target from Compare & Deploy instead',
    'The wmill settings.yaml no longer carries deploy_to; an older file that still has it is ignored rather than rejected',
  ]
docs: /docs/core_concepts/staging_prod#upgrading-from-the-deploy-target-setting
---

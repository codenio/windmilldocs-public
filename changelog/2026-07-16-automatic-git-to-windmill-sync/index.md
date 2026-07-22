---
slug: automatic-git-to-windmill-sync
version: v1.761.0
title: Automatic git-to-Windmill sync
tags: ['Git sync', 'Enterprise']
description: The Git to Windmill direction of git sync now works fully in-app, making the documented GitHub Actions optional. Enable 'Automatically deploy changes from Git' on a repository and new commits to the tracked branch deploy into the workspace, instantly via webhooks for GitHub App repositories (with polling as a safety net) or by polling about every minute for token repositories. Windmill can also open pull requests for promotion and fork deploy branches, post a 'Windmill diff' check and managed comment on pull requests showing what merging would deploy, post a deploy status check on synced commits, and automatically deploy fork branch changes into fork workspaces from a single parent-level toggle.
features:
  [
    "Per-repository 'Automatically deploy changes from Git' toggle: new commits on the tracked branch deploy into the workspace, no CI/CD pipeline needed.",
    'GitHub App repositories (managed and GHES self-managed) sync instantly via an HMAC-verified webhook that Windmill registers itself; polling stays on as a safety net.',
    'Token-based repositories sync via polling, checking the tracked branch about every minute; commits made by Windmill ([WM] prefix) are skipped to prevent loops.',
    "In-app pull request creation: 'Open a pull request for each deploy branch' on promotion repositories and 'Open a pull request when an item is deployed in a fork' on the parent sync repository, replacing the gh pr create GitHub Actions.",
    "Pull requests targeting the tracked branch get a 'Windmill diff' check run and a managed comment showing what merging would deploy, updated on each push.",
    "Tracked-branch deploys post a 'Windmill' check run on the commit that flips from 'Deploying…' to 'Deployed N changes'.",
    "Parent-level 'Automatically sync forks with git branches' toggle deploys changes on each fork's wm-fork/** branch into the matching fork workspace, replacing the push-on-merge-to-forks action.",
  ]
docs: /docs/advanced/git_sync#automatic-sync-from-git
---

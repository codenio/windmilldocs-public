---
slug: gitlab-git-sync-parity
version: v1.806.0
title: GitLab repositories reach parity for git sync
tags: ['Git sync', 'Enterprise']
description: Git sync's managed features were available only to GitHub App repositories. Hand a GitLab project access token to Windmill with the GitLab button in the git_repository resource form, and the repository gets instant pull over a webhook, merge requests opened on deploy, a diff preview note on the merge request, and automatic token renewal. The token is stored encrypted on the workspace, keyed by the repository it was issued for, and workspace forks read that one copy. A token written into a repository URL is unchanged, still a plain git remote that syncs on deploy and by polling only.
features:
  [
    'GitLab button in the git_repository resource form: paste the instance URL and a project access token, pick the project, and Windmill stores the token and fills in a credential-free remote URL',
    'GitLab repositories sync instantly through a project hook Windmill registers itself, with polling as a fallback',
    'Merge requests opened on deploy for promotion wm_deploy/** and fork wm-fork/** branches, from the same per-repository toggles as GitHub',
    'A merge request targeting the tracked branch gets a Windmill note with the sync status and what merging would deploy, updated in place on each push',
    'Windmill renews the token within three weeks of expiry, and a Replace token control on the resource swaps it by hand',
    'One credential per repository: workspace forks read the parent copy, so a renewal reaches the whole fork chain at once',
  ]
docs: /docs/integrations/git_repository#gitlab
---

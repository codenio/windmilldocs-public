---
slug: windmill-ci-tests-pr-check
version: v1.812.0
title: Gate GitHub pull requests on Windmill CI tests
tags: ['Git sync', 'Enterprise']
description: Fork and dev workspace pull requests get a 'Windmill CI tests' check on GitHub, which can be made a required status check to block merge until tests pass.
features:
  [
    "A 'Windmill CI tests' check run on pull requests targeting the tracked branch, concluding failure as soon as a test fails and success once all tests pass.",
    'Requires a repository connected through the GitHub App with automatic sync from Git enabled, and no GitHub Action on the repository side.',
    'Every push to the pull request runs the whole CI suite again on the new head, in the fork or dev workspace the branch syncs to.',
    'Pull requests from other branches get the check posted as skipped, so requiring it does not block them.',
    'A check that has not concluded after 30 minutes fails, so a hung test cannot leave a required check pending.',
  ]
docs: /docs/advanced/git_sync#ci-tests-check
---

---
slug: asset-freshness
title: Asset freshness with fresh/stale badge and automatic watchdog
version: v1.748.0
tags: ['Data pipelines', 'Enterprise']
description: The `// freshness <window>` annotation on pipeline scripts now shows a live fresh/stale verdict on the pipeline graph, emerald when the last successful run completed within the window and amber when it is stale or has never run. On Enterprise Edition, a freshness watchdog re-runs stale unpartitioned scripts automatically with exponential backoff capped at the window; watchdog runs skip the downstream cascade, are attributed to pseudo-user freshness-<path> with the new freshness trigger kind, and can be disabled instance-wide with DISABLE_FRESHNESS_WATCHDOG.
features:
  [
    'Freshness badge on pipeline graph nodes: emerald when the last successful root run completed within the declared window, amber when stale or never run, with tooltips showing the last successful run',
    'Badges re-evaluate every 30 seconds on an open graph and turn fresh shortly after a successful run in the session',
    'EE freshness watchdog checks deployed pipeline scripts about once a minute and re-runs stale unpartitioned scripts as a backstop; any successful run resets the window',
    'Watchdog re-runs back off exponentially (capped at the window) while a script stays stale, and skip scripts with a run already queued or running',
    'Watchdog runs never fire the downstream cascade and are attributed to pseudo-user freshness-<path> with the new freshness trigger kind, filterable on the Runs page',
    'DISABLE_FRESHNESS_WATCHDOG environment variable turns the watchdog off instance-wide',
  ]
docs: /docs/core_concepts/pipelines#freshness
image: ./freshness_badges.png
---

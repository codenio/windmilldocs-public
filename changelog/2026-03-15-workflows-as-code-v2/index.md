---
slug: workflows-as-code-v2
title: Workflows as code v2
tags: ['Script editor', 'Flow editor']
description: Workflows as code v2 introduces checkpoint-based orchestration with <code>workflow()</code>, <code>task()</code>, <code>step()</code>, <code>sleep()</code>, <code>waitForApproval()</code>, and <code>parallel()</code> primitives. The workflow fully suspends between tasks, releasing its worker slot, eliminating deadlocks and enabling unlimited parallelism on any number of workers. Also adds script modules (<code>__mod/</code> folders), CLI sync support, and a timeline UI for visualizing task execution.
features:
  [
    'Checkpoint/replay orchestration: workflows suspend between tasks, releasing worker slots entirely — zero worker waste during sleeps, approvals, or child task execution.',
    'task() dispatches functions as separate child jobs with own logs and timeline.',
    'step() persists lightweight inline results for replay determinism (timestamps, random IDs).',
    'sleep() and waitForApproval() for server-side delays and human-in-the-loop approvals — the worker is fully released until the event fires.',
    'parallel() utility with optional concurrency control for batched processing.',
    'taskScript() and taskFlow() to dispatch to existing Windmill scripts and flows by path.',
    'Script modules: companion files in __mod/ folders with per-module dependency tracking and separate lockfiles.',
    'Full CLI sync support with per-module hash tracking and selective lock regeneration.',
    'Task options: timeout, tag, cache_ttl, priority, concurrency_limit, concurrency_key.',
    'Workflow timeline UI showing each task as a separate entry with duration bars.',
    'Error propagation with TaskError for structured try/catch error handling.',
  ]
docs: /docs/core_concepts/workflows_as_code
---

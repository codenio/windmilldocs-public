---
slug: pipeline-schema-contracts
title: Schema contracts for pipeline consumers
version: v1.748.0
tags: ['Data pipelines']
description: Consumer scripts referencing materialized DuckLake tables are now validated against the captured producer schemas at save time. Missing columns, dropped lineage sources and mismatched relationship types surface as warnings (never errors) after deploy, as live editor squiggles, and column names autocomplete with their types when typing `.` after a `ducklake://` reference on annotation lines. Producers can declare a deliberately unstable schema with `on_schema_change=ignore` on the `// materialize` line to collapse downstream warnings into a single note.
features:
  [
    'Save-time check: deploying a consumer script diffs its `ducklake://` references (body column reads, `// column` lineage sources, `// data_test relationships` refs) against the latest captured schema and toasts warnings',
    'Warnings never block a save or deploy: a deliberate upstream reshape does not fail every consumer',
    'Live editor squiggles anchor the same warnings to the offending column read or annotation line as you type',
    'Typing `.` after a `ducklake://…` reference on an annotation line autocompletes column names with their captured types',
    'Column names compare case-insensitively, `{partition}` tokens are stripped, `_wm_partition` is always accepted, and a `<table>_current` view checks against its SCD2 base table',
    '`// materialize … on_schema_change=ignore` marks a producer schema as deliberately unstable and collapses downstream warnings into one informational note',
    'Each warning cites the schema version and capture time it was checked against',
  ]
docs: /docs/core_concepts/pipelines/materialization#schema-contracts
---

---
slug: ducklake-scheduled-maintenance
title: Scheduled Ducklake maintenance
version: v1.748.0
tags: ['Data pipelines', 'Enterprise']
description: Ducklakes can now run scheduled maintenance to keep growth in check - snapshot expiry with a configurable retention window (default 7 days), compaction of adjacent small parquet files, and orphaned file cleanup. Configured per lake in the workspace Ducklake settings with a cron cadence (default daily at 03h UTC) and executed as observable jobs whose run history is the audit trail. Enterprise feature.
features:
  [
    'Per-lake maintenance settings in workspace Ducklake settings - enable toggle, snapshot retention in days (default 7), cron cadence (default daily at 03h UTC with a per-lake minute offset), and individual toggles for compaction and orphaned file cleanup',
    'Snapshot expiry reclaims files referenced only by snapshots older than the retention window; compaction merges adjacent small parquet files; orphaned file cleanup deletes files no longer referenced by the catalog',
    'Runs execute as normal jobs on the duckdb tag via a managed schedule at the reserved path f/ducklake_maintenance/<lake>, with run history as audit trail and a one-row summary result (expired snapshots, compacted file groups, cleaned and orphaned files deleted, remaining snapshots)',
    'Expired snapshots become non-queryable via time-travel (AT (VERSION => n)), so size the retention window to the history you need',
    'Safety margins - physical file deletion lags expiry by one day so long-running readers are not interrupted, and orphan cleanup never deletes files younger than one day; lake names are validated as [A-Za-z0-9_-]+',
  ]
docs: /docs/core_concepts/persistent_storage/ducklake#scheduled-maintenance
image: ./ducklake_maintenance.png
---

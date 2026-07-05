---
slug: fork-ducklake-data-environments
title: Fork data environments for DuckLake materialization
tags: ['Data pipelines', 'Workspace']
description: Workspace forks now get an isolated data environment per DuckLake by default. Materializing pipelines in a fork write to a fork-scoped metadata schema and bucket prefix instead of the parent's tables, and tables the fork has not materialized yet are read from the parent through read-only defer views, so one node can be iterated on without rebuilding upstream. The fork-creation dialog adds a per-lake Isolated / Shared with parent choice, the pipeline graph shows deferred vs fork chips on DuckLake assets, and deleting a fork can drop its forked namespaces.
features:
  [
    'Forks default to an isolated data environment per lake: a fork-scoped metadata schema and a __wm_forks/<fork id>/ bucket prefix, with unchanged ducklake:// URIs and annotations',
    'Read-defer to the parent: tables the fork has not materialized are read through read-only views over the parent data, including the <table>_current companion view of SCD2 targets',
    'Parent lakes are attached read-only in forks, so a fork job cannot write parent data through DuckLake',
    'Fork-creation dialog gains a Ducklake data environment section with a per-lake Isolated (default) or Shared with parent choice; shared forks read and write the parent lake directly',
    'Pipeline graph marks each DuckLake asset in a fork with an amber deferred or emerald fork chip, with a matching banner in the details pane',
    'Fork deletion offers to drop forked DuckLake namespaces; also available as POST /w/<workspace>/workspaces/drop_forked_ducklake_namespaces',
  ]
docs: /docs/advanced/workspace_forks#fork-data-environments-for-ducklake
---

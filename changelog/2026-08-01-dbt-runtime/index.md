---
slug: dbt-runtime
title: Run dbt projects as a first-class Windmill runtime
version: v1.776.0
tags: ['Script editor', 'Data pipelines', 'CLI']
description: An unmodified dbt project now runs as a Windmill script. Copy the project into a `<script>__dbt/` folder, `wmill sync push`, and Windmill runs `dbt build` on your own workers with live per-model progress, per-model results, `dbt retry` and row previews. Since v1.777.0, dbt is in the new-script language picker and opens in an editor of its own - the project's file tree, its descriptor, the run form and a model graph that `Refresh models` redraws from a `dbt parse` of the files as they are in the editor, labelled with where it came from. Its models, sources, seeds and snapshots become `dbt://warehouse/schema/model` assets with their `ref()` lineage, so a Python or DuckDB script reading a mart appears on the same graph. Warehouses are configured once per workspace and named from the optional `wm_dbt.yaml` descriptor, so the project carries no connection and stays runnable locally. Three engines are selectable (dbt Core 1.x by default, dbt Core 2.x, dbt Fusion), all fetched or built on first use and cached per worker. Everything is in the community edition except the mssql and oracle adapters.
features:
  [
    'One dbt project is one Windmill script: the project rides with it as its module bundle, copied in verbatim and never cloned at run time',
    'Models, sources, seeds and snapshots become dbt:// assets with ref() lineage, materialization, tags and data tests, parsed at deploy',
    'A dbt editor (v1.777.0): project file tree, descriptor, run form and a model graph refreshed on demand from a dbt parse of the buffer, scriptable from a flow, the CLI or the API',
    'Live per-model progress during a run, structured per-model results, dbt retry from the run page and dbt show row previews',
    'Warehouses configured once per workspace and named by the optional wm_dbt.yaml descriptor, or bring the project its own profiles.yml',
    'Engine toggle between dbt Core 1.x (default), dbt Core 2.x and dbt Fusion, with dependencies resolved and pinned at deploy',
  ]
docs: /docs/getting_started/scripts_quickstart/dbt
---

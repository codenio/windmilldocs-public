---
slug: ai-agent-evals
title: AI agent evals (beta)
tags: ['AI', 'Flow editor']
version: v1.796.0
description: Reusable AI agents can now be measured against a dataset of cases. Evals open from the agent card in the flow editor or from the ai_agent row on the resources page, and let you curate cases, score every answer with AI judges or code scorers, and compare two runs cell by cell. A run measures one state of the agent - what is deployed, an earlier version, or the unsaved edits in the step - fixed once when the run starts, and is kept so the next run has something to be compared against.
features:
  [
    'Datasets of cases (a question and an expected answer) belong to a reusable ai_agent resource, so they outlive the flow step and two runs of the same agent are comparable.',
    'Scorers are ordinary runnables: an AI judge handed the whole run, or a script created from a template. Each returns a number between 0 and 1, with an optional pass threshold that is applied when a score is read.',
    'A scorer sees the whole trajectory: the case, the answer, every tool call with its arguments, result, error and duration, the tools that were called with their schemas, and the run metrics.',
    'Run against the latest deployed agent, a pinned past version, or the unsaved edits the flow step is holding; the configuration is read once when the run starts, so every case runs the same one.',
    'A run is one flow job that outlives the tab that started it: a parallel loop over the cases, each answered and then scored by one branch per scorer.',
    'The run history lists every run of an agent with a score badge per scorer, and opening one gives a table of cases by scorer with per-cell and per-column deltas against any other run of that dataset.',
  ]
docs: /docs/core_concepts/ai_agent_evals
---

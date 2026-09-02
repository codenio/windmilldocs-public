---
slug: ai-usage-and-cost
title: AI usage and cost tracking
tags: ['AI']
description: Windmill now records the tokens every AI chat spends, per user, model and provider, and prices them. Workspace admins get an "AI usage" panel in the Windmill AI settings, grouped by day, user or model; every member sees their own spend under "Your AI usage" in user settings. Costs are estimates marked with a leading ~, except where the provider bills back an exact figure (OpenRouter).
features:
  [
    'Token spend from AI sessions and the AI chat is recorded per workspace, user, provider and model.',
    'An admin-only "AI usage" panel in the workspace Windmill AI settings, over the last 7, 30 or 90 days, grouped by day, user or model.',
    'A self-scoped "Your AI usage" panel in user settings, open to every member.',
    'Costs marked with ~ are estimated from a built-in price table; a cost the provider billed back is shown as is. A model with no known rate is reported as unpriced rather than guessed at.',
    'A "Model pricing" panel to override rates per model in USD per million tokens (input, output, cache read, cache write), on the workspace or instance AI config.',
    'GET and POST /w/{workspace}/ai/usage expose the same data over the API.',
  ]
docs: /docs/core_concepts/ai_generation#ai-usage-and-cost
---

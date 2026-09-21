---
slug: ai-agent-enabled-tools
version: v1.812.0
title: Enabled tools for AI agent steps
tags: ['AI', 'Flow editor']
description: AI agent steps have a new enabled_tools input that picks which of the agent's tools a run can call, as a static selection or an expression evaluated per run. Leaving it unset keeps every tool, an empty list gives the agent none, and flows reusing a saved agent can each enable a different set.
features:
  [
    'The enabled_tools step input is a multiselect of the step tools, or a JavaScript expression that returns a list of tool names on each run.',
    'Unset keeps every tool, an empty list runs the agent with no tools, and a list keeps only the tools it names.',
    'Script, flow and nested agent tools are named by their tool name, MCP servers by their resource path, and web search by the reserved name __wm_web_search.',
    'A disabled MCP server is never contacted, and names that match no tool are ignored and counted in the job logs.',
  ]
docs: /docs/core_concepts/ai_agents#enabled-tools
---

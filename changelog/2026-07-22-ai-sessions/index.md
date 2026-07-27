---
slug: ai-sessions
title: AI sessions (beta)
tags: ['AI']
version: v1.766.0
video: https://www.youtube.com/watch?v=yjNHwHBkbyE
description: AI sessions are now in beta and enabled by default. Each session ties an AI chat to a workspace or fork with a live preview panel; the AI builds scripts, flows and apps as drafts you review in a unified diff drawer and deploy. Run many sessions in parallel; a banner switches back to the legacy chat.
features:
  [
    'Enabled by default during the beta: a banner under the session chat switches back to the legacy side panel chat (stored per browser), and a matching banner in the legacy chat reactivates sessions. Operators keep the legacy chat.',
    'Each session is tied to a workspace or fork, picked before the first message; forks are only created when the conversation actually starts.',
    'The preview panel opens edited items as live editors and workspace pages (runs, schedules, settings) as tabs, refreshing only what the AI touched.',
    'A chat-scoped edits bar and unified diff drawer track what the conversation changed, with per-item deploy and discard, and fork promotion via the compare page.',
    'Jobs the AI runs detach to a background jobs tray with live status, cancel and approval actions, and survive page reloads.',
    'The AI writes plans and specs as markdown artifacts that open in the preview panel with copy and download actions.',
    'With a full-code app preview open, the AI debugs the running app: console logs, job runs, live DOM queries (search_dom, read_dom), screenshots, and a click-to-attach element inspector.',
    'Slash commands: /compact summarizes the conversation in place, /clear starts a fresh chat, and workspace AI skills appear as commands.',
    'Sessions are grouped by workspace family in the sidebar, with unread badges and parallel draft sessions persisted in the browser.',
  ]
docs: /docs/core_concepts/ai_sessions
---

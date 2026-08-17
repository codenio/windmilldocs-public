---
slug: ai-sessions-plan-mode
title: Plan mode for AI sessions
tags: ['AI']
version: v1.790.0
description: Plan mode is a read-only autonomy posture for AI sessions, picked from the chat footer. The assistant can only investigate; anything that writes, runs or deploys is refused until it hands over a plan and you approve it, which restores the posture you were in before. Session chats only, and never persisted.
features:
  [
    'Plan (read-only) joins Ask permission and Yolo in the autonomy picker of a session chat.',
    'Only read-only tools run while planning; writes, job runs and deploys are refused with a "Blocked in plan mode" row.',
    'You enter plan mode from the picker, or by accepting the "Start planning?" card the assistant raises on open-ended tasks.',
    'The proposed plan is shown for approval with "Approve and implement" or "Keep planning"; approving restores the exact posture that preceded plan mode.',
    'One versioned plan document per session, pinned to the top of the artifacts list, with the approved version marked and unapproved revisions labeled as drafts.',
  ]
docs: /docs/core_concepts/ai_sessions#plan-mode
---

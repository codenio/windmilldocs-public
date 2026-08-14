---
slug: ai-artifact-version-history
version: v1.784.0
title: Version history for AI session artifacts
tags: ['AI Chat', 'Windmill AI']
description: Every revision of an AI session artifact is now saved as a version, labelled with a short note describing what changed. A picker in the artifact viewer header lets you read an earlier version, with a banner marking the view as stale and a button back to the latest. The AI can list and read past versions too, so you can ask it to restore earlier wording instead of rewriting it. History is capped per artifact, and larger documents keep fewer versions.
features:
  [
    'Each content change to an artifact is saved as a version with a short change note written by the AI.',
    'The artifact viewer header gains a version picker once an artifact has more than one version; viewing a past version shows a stale banner with a "Back to latest" button.',
    'The AI can list artifact versions and read any of them, so it can restore earlier wording on request rather than rewriting from memory.',
    'The artifacts list above the chat input shows an artifact version number once it has been revised.',
    'History is bounded per artifact: up to 20 versions, fewer for large documents, so browser storage stays in check.',
  ]
docs: /docs/core_concepts/ai_sessions#artifacts
---

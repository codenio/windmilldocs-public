---
slug: ai-chat-text-file-attachments
title: Attach text files to AI chat messages
tags: ['AI', 'AI Chat']
version: v1.765.0
description: Text files can now be attached to individual AI chat messages via picker, drag and drop, or paste. They show as chips in the input box and are sent with the next message. Content is read on demand by the AI through file tools instead of being inlined, so it is never resent with the conversation history.
features:
  [
    'Attach text files to a chat message via the attach button, drag and drop, or paste',
    'Up to 8 files per message, 1 MB per file',
    'Files appear as chips in the input box, sent with the next message and cleared after send',
    'The AI reads file content on demand via read_file and search_files tools, keeping the conversation history small',
    'Linked folders remain session-wide assets, shown in the footer next to the mode picker',
  ]
docs: /docs/core_concepts/ai_generation#attaching-files
---

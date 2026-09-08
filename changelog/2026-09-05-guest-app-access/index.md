---
slug: guest-app-access
title: Guest access for apps
tags: ['App editor', 'Security']
version: v1.804.0
description: A fourth app access mode sits between members-only and public. Opening an app set to Guests requires signing in through your identity provider, but not a Windmill account and not workspace membership. Runnables execute on behalf of the publisher exactly as they do for a member, and the visitor is confined to that one app. Because a guest leaves no user row behind they take no seat. The first 100 distinct guest emails over a trailing 30 days are free on any instance, and past that an instance holding an Enterprise Edition license meters them at four guests to one seat while an instance without one admits no new guest email until the count drops back under 100. Off by default, behind three independent switches.
features:
  [
    "The app editor's Public URL toggle becomes an Access control with three options: Members, Guests and Public. Guests reach the app through the same secret URL or custom URL as a public app, but are asked to sign in first.",
    'Signing in as a guest provisions nothing: no user row, no invite, no workspace membership. It goes through the instance SSO or SAML providers, and someone who already has an account anywhere on the instance is never admitted as a guest.',
    'The session is pinned to one workspace, scoped to the one app, and expires after 8 hours by default (GUEST_SESSION_VALIDITY_SECONDS). Listing jobs, scripts, flows, apps or variables, reading resource values, another workspace and another guest app are all refused.',
    'Three gates, all off by default: the app mode, a workspace switch under workspace settings > Advanced > Apps, and a superadmin switch under instance settings > Users > Guests. The two switches are re-read on every guest request, so turning either off stops guests already signed in on their next request; flipping an app back to Members closes it to its existing guests just as immediately.',
    'A superadmin Guests tab lists the distinct guest emails of the trailing 30 days with the workspaces they opened and when they were first and last seen, next to the instance standing against the allowance.',
    'Opening an app to guests can be reserved to workspace admins and bypass users with the "Restrict guest app access" protection ruleset rule (Enterprise Edition).',
    'Tracked app files carry the access mode as a tri-state - public: true, guests: true, or neither - so a CLI pull followed by a push, and git sync, keep the mode an app was deployed with.',
  ]
docs: /docs/apps/guest_apps
---

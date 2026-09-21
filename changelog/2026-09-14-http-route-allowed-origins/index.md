---
slug: http-route-allowed-origins
version: v1.812.0
title: Allowed origins for HTTP routes
tags: ['Triggers', 'Security']
description: HTTP routes can restrict which origins may call them from a browser. The allowlist is enforced on both the OPTIONS preflight and the response, so a disallowed origin cannot read the result, and a request that needs a preflight never reaches the runnable. Superadmins can set an instance-wide default on Enterprise Edition.
features:
  [
    'New "Allowed origins" option in the route editor, under Advanced > Request Options.',
    'A matching Origin is echoed in Access-Control-Allow-Origin; other origins get no header, on the preflight and the response.',
    'New "HTTP route default allowed origins" instance setting governs routes that set no list of their own (Enterprise Edition); a route opts out with *.',
    'When an allowlist applies, it overrides Access-Control-Allow-Origin set through wm_headers. Static websites are exempt.',
  ]
docs: /docs/triggers/http_routing#allowed-origins
---

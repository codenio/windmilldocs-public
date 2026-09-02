---
slug: gcp-pubsub-application-default-credentials
version: v1.794.0
title: Application default credentials for GCP Pub/Sub triggers
tags: ['GCP', 'Triggers', 'Enterprise']
description: GCP Pub/Sub triggers can now authenticate as the Windmill server itself through application default credentials (GKE Workload Identity, the metadata server or GOOGLE_APPLICATION_CREDENTIALS) instead of a gcloud resource, by leaving the resource unset. Selecting this mode requires workspace admin. Workload Identity Federation credential files are supported.
features:
  [
    "Authenticate GCP Pub/Sub triggers with the instance's application default credentials by leaving the gcloud resource unset (workspace admins only).",
    "New GOOGLE_APPLICATION_CREDENTIALS server environment variable, with Workload Identity Federation files supported through the file, url and aws credential sources (executable is not supported).",
    "Optional project ID to list and create topics and subscriptions in another project than the credentials' own.",
  ]
docs: /docs/triggers/gcp_triggers
---

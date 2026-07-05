---
slug: ce-workspace-storage-quota
version: v1.746.0
title: 10GiB workspace storage quota replaces 50MB upload cap on Community Edition
tags: ['S3', 'Persistent storage', 'Workspace']
description: The Community Edition 50MB per-file upload cap on workspace object storage is replaced by a 10GiB total storage quota per workspace. Files of any individual size can be uploaded up to the quota, usage is shown in the workspace settings under S3 Storage with a recount button, and reads and deletes are never blocked even when over quota. Enterprise Edition remains unlimited.
features:
  [
    'Upload files of any individual size to workspace object storage on Community Edition, up to 10GiB of total workspace storage.',
    'Storage usage meter in workspace settings under S3 Storage, with a button to recount usage by listing the storage.',
    'Writes exceeding the quota are rejected, but reads and deletes are never blocked, so an over-quota workspace can always free up space.',
    'The quota counts all objects under the configured storages except the reserved volumes/ prefix; Enterprise Edition remains unlimited.',
  ]
docs: /docs/core_concepts/object_storage_in_windmill#workspace-object-storage
---

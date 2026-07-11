---
slug: iam-rds-auth
title: IAM authentication for RDS PostgreSQL resources
tags: ['PostgreSQL', 'Resources']
description: PostgreSQL resources can now use AWS IAM authentication instead of static passwords. Workers generate short-lived tokens automatically using IRSA, EKS Pod Identity, or EC2 Instance Profiles.
features:
  [
    'IAM authentication for PostgreSQL resources: enable use_iam_auth on a resource to replace static passwords with short-lived IAM tokens.',
    'Supports all AWS credential methods: IRSA, EKS Pod Identity, and EC2 Instance Profiles — auto-detected by the worker.',
    'SSL is enforced automatically for IAM connections.',
    'Optional region field on the resource, falls back to AWS_REGION env var.',
  ]
docs: /docs/integrations/postgresql
ee: true
---

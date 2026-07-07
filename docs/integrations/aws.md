---
description: How do I connect AWS to Windmill? Use AWS services from scripts and flows with access keys or OIDC.
---

import ResourceUsage from './_resource_usage.mdx';

# AWS integration

[AWS](https://aws.amazon.com/) is a cloud computing platform offering various services like computing, storage and databases.

To integrate AWS with Windmill, you can configure either a classic **AWS resource** using access keys, or a more secure **AWS OIDC resource**, which assumes IAM roles via OpenID Connect.

These should be saved as a [resource](../core_concepts/3_resources_and_types/index.mdx).

:::info Self-host

If you're looking for a way to self-host Windmill using AWS, see [Self-Host Windmill](../advanced/1_self_host/index.mdx).

:::

---

## AWS Resource

| Property           | Type   | Description                        | Default | Required | Where to Find                                                             |
| ------------------ | ------ | ---------------------------------- | ------- | -------- | ------------------------------------------------------------------------- |
| awsAccessKeyId     | string | AWS Access Key ID for your account |         | true     | AWS Management Console > IAM > Users > [Your User] > Security Credentials |
| awsSecretAccessKey | string | AWS Secret Access Key for account  |         | true     | AWS Management Console > IAM > Users > [Your User] > Security Credentials |
| region             | string | AWS Region for your resources      |         | false    | AWS Management Console > Top Right Corner (e.g., "N. Virginia")           |

---

## AWS OIDC Resource

| Property | Type   | Description                                         | Default | Required | Where to Find / Define                                                                 |
|----------|--------|-----------------------------------------------------|---------|----------|-----------------------------------------------------------------------------------------|
| roleArn  | string | ARN of the IAM role to assume using OIDC            |         | true     | AWS Management Console > IAM > Roles > [Your Role] > ARN                               |
| region   | string | AWS Region for your resources                       |         | false    | AWS Management Console > Top Right Corner (e.g., "us-west-2")                          |

> ℹ️ Ensure the IAM role trusts Windmill's OIDC provider and has sufficient permissions for the services you intend to use.

---

## Usage

<ResourceUsage name="AWS" hub="aws_ecr" />

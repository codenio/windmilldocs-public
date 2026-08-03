---
description: How do I connect PostgreSQL to Windmill? Query and manage Postgres databases from scripts and flows.
---

# PostgreSQL integration

[PostgreSQL](https://www.postgresql.org/) is an open-source object-relational database management system.

Windmill provides a framework to support PostgreSQL databases, either with native SQL scripts or through TypeScript for raw queries.

![Integration between PostgreSQL and Windmill](../assets/integrations/psql-0-header.png.webp 'Connect a PostgreSQL instance with Windmill')

Please refer to the [SQL Getting started section](../getting_started/0_scripts_quickstart/5_sql_quickstart/index.mdx).

---

## IAM authentication for AWS RDS and Aurora

:::info Enterprise

This feature is available on [Windmill Enterprise Edition](/pricing) only.

:::

Instead of using static passwords, you can authenticate to AWS RDS or Aurora PostgreSQL databases using [IAM database authentication](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAMDBAuth.html). Windmill workers generate short-lived authentication tokens automatically, so no database password needs to be stored in the resource.

This works with any of the standard AWS credential methods:

- [IRSA](https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts.html) (IAM Roles for Service Accounts)
- [EKS Pod Identity](https://docs.aws.amazon.com/eks/latest/userguide/pod-identities.html)
- [EC2 Instance Profiles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2_instance-profiles.html)

### Setup

1. **Enable IAM authentication on your RDS instance.** In the AWS console, go to your RDS instance settings and enable IAM database authentication.

2. **Create a database user with the `rds_iam` role:**

```sql
CREATE USER myuser WITH LOGIN;
GRANT rds_iam TO myuser;
```

3. **Grant IAM permissions to your worker.** The IAM principal attached to your Windmill worker (via IRSA, Pod Identity, or Instance Profile) needs the `rds-db:connect` action. Example IAM policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "rds-db:connect",
      "Resource": "arn:aws:rds-db:<region>:<account-id>:dbuser:<dbi-resource-id>/<db-user-name>"
    }
  ]
}
```

4. **Create a PostgreSQL resource with IAM auth enabled.** Set `use_iam_auth` to `true` and fill in `host`, `user`, and `dbname`. The `password` field is ignored when IAM auth is enabled.

```json
{
  "host": "mydb.cluster-abc123.us-east-1.rds.amazonaws.com",
  "port": 5432,
  "user": "myuser",
  "dbname": "mydb",
  "sslmode": "require",
  "use_iam_auth": true,
  "region": "us-east-1"
}
```

The `region` field is optional if the `AWS_REGION` environment variable is set on the worker. SSL is enforced automatically for IAM connections.

---

## Azure workload identity for Azure Database for PostgreSQL

:::info Enterprise

This feature is available on [Windmill Enterprise Edition](/pricing) only.

:::

On AKS, workers can authenticate to [Azure Database for PostgreSQL Flexible Server](https://learn.microsoft.com/en-us/azure/postgresql/flexible-server/concepts-azure-ad-authentication) as their own [workload identity](https://learn.microsoft.com/en-us/azure/aks/workload-identity-overview) instead of with a password. The pod's projected service account token is exchanged with Microsoft Entra ID for a short-lived access token, so no database password is stored in the resource.

### Setup

1. **Give the worker a workload identity.** Enable the OIDC issuer and the workload identity add-on on the cluster, create a user-assigned managed identity, and add a federated credential binding it to the worker's Kubernetes service account:

```bash
az identity federated-credential create \
  --name windmill-worker \
  --identity-name <managed-identity-name> \
  --resource-group <resource-group> \
  --issuer "$(az aks show -n <cluster> -g <resource-group> --query oidcIssuerProfile.issuerUrl -o tsv)" \
  --subject "system:serviceaccount:<namespace>:<worker-service-account>" \
  --audience api://AzureADTokenExchange
```

Annotate the service account with `azure.workload.identity/client-id: <client-id>` and label the worker pods with `azure.workload.identity/use: "true"`. The webhook then injects `AZURE_TENANT_ID`, `AZURE_CLIENT_ID`, `AZURE_FEDERATED_TOKEN_FILE` and `AZURE_AUTHORITY_HOST` into the worker, which is where Windmill reads the identity from. Nothing about the identity is configured on the resource, so a worker reaching two databases as two different identities needs two [worker groups](../core_concepts/9_worker_groups/index.mdx).

2. **Create the database principal.** Connect as the server's Entra administrator and map the managed identity:

```sql
SELECT * FROM pgaadauth_create_principal('<managed-identity-name>', false, false);
```

3. **Create a PostgreSQL resource with `ms_entraid` as the password.** That value is a sentinel rather than a real password: it tells the worker to authenticate as its workload identity. `user` must be the Entra principal name created above.

```json
{
  "host": "myserver.postgres.database.azure.com",
  "port": 5432,
  "user": "<managed-identity-name>",
  "dbname": "mydb",
  "sslmode": "require",
  "password": "ms_entraid"
}
```

SSL is enforced automatically for these connections, and the job logs state `Using Azure Workload Identity` whenever the sentinel takes effect. A resource whose password happens to be literally `ms_entraid` is treated the same way, so pick a different password if that ever collides.

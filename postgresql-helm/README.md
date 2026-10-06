# PostgreSQL on Rancher Desktop with Helm

This chart creates a simple PostgreSQL database with persistent storage.

## Install

```bash
helm upgrade --install postgresql . \
  --namespace langflow \
  --create-namespace
```

## What it creates

- one PostgreSQL pod
- one ClusterIP service
- one PVC for database files
- one secret for the database password

## Default connection values

- host: `postgresql`
- port: `5432`
- database: `langflow`
- user: `langflow`

Use the same values in the Langflow chart so both charts connect correctly.
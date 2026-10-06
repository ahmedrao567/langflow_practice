# Langflow and PostgreSQL on Rancher Desktop

This workspace now has two separate Helm charts:

- [Langflow chart](langflow-helm)
- [PostgreSQL chart](postgresql-helm)

## Install order

1. Install PostgreSQL first.
2. Install Langflow second.

## PostgreSQL values used by Langflow

Langflow is configured to connect with these defaults:

- host: `postgresql`
- port: `5432`
- database: `langflow`
- user: `langflow`
- secret name: `postgresql-secret`
- secret key: `password`

## Quick install

From this folder:

```bash
helm upgrade --install postgresql ./postgresql-helm --namespace langflow --create-namespace
helm upgrade --install langflow ./langflow-helm --namespace langflow
```

## Access Langflow

```bash
kubectl port-forward -n langflow svc/langflow-langflow 7860:7860
```

Open:

```text
http://127.0.0.1:7860
```

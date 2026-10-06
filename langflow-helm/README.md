# Langflow on Rancher Desktop with Helm

This chart deploys Langflow only.
Use the PostgreSQL chart in the sibling folder to provide the database and PVC.

## Prerequisites

- Rancher Desktop with Kubernetes enabled
- Helm 3

## Install

Install PostgreSQL first, then Langflow.

From the PostgreSQL chart directory:

```bash
helm upgrade --install postgresql ../postgresql-helm \
  --namespace langflow \
  --create-namespace
```

Then install Langflow:

```bash
helm upgrade --install langflow . \
  --namespace langflow \
  --create-namespace
```

## Access the app

For local access on Rancher Desktop, the simplest option is port-forwarding:

```bash
kubectl port-forward -n langflow svc/langflow-langflow 7860:7860
```

Then open:

```text
http://127.0.0.1:7860
```

## Use LoadBalancer instead

If your Rancher Desktop setup supports LoadBalancer services, install with:

```bash
helm upgrade --install langflow . \
  --namespace langflow \
  --create-namespace \
  --set service.type=LoadBalancer
```

## Database persistence

The database connection values used by Langflow are:

- host: `postgresql`
- port: `5432`
- database: `langflow`

If you change the PostgreSQL release name or service name, update `values.yaml` in the Langflow chart so the host matches.

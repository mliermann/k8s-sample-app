# Kubernetes Manifests

This directory contains plain Kubernetes manifests for deploying:

- **Frontend web UI** (`web-ui/`)
- **Backend API** (`web-app/`)
- **Postgres database** (`database/`)

## Usage

Apply all manifests using Kustomize:

```sh
kubectl apply -k .
```

Or apply individual manifests as needed.

## Secrets

Database credentials are managed via Kubernetes Secrets.  
See the workflows and manifest examples for details.

## Monitoring

ServiceMonitor manifests are provided for Prometheus integration.
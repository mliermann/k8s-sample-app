# Kubernetes Manifests

This directory contains plain Kubernetes manifests for deploying:

- **Frontend web UI** (`web-ui/`)
- **Backend API** (`web-app/`)
- **Postgres database** (`database/`)

**Prerequisites:**  
- Kubernetes cluster  
- `kubectl` installed
- Kubernetes secret `db-secret` created in target namespace as follows:
```sh
kubectl create secret generic db-secret \
  --from-literal=DB_NAME=sampledb \
  --from-literal=DB_USER=sampleuser \
  --from-literal=DB_PASS=samplepass
```
- TLS secret `frontend-tls` created in target namespace as follows:
```sh
kubectl create secret tls frontend-tls \
  --cert=path/to/tls.crt \
  --key=path/to/tls.key

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
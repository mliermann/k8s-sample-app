# Helm Charts

This directory contains Helm charts for the frontend and backend components.

## Structure

- `web-ui/` — Frontend Helm chart
- `backend/` — Backend Helm chart

## 

Create a Kubernetes secret `db-secret` in your target namespace as follows:
```sh
kubectl create secret generic db-secret \
  --from-literal=DB_NAME=sampledb \
  --from-literal=DB_USER=sampleuser \
  --from-literal=DB_PASS=samplepass
```

Package and push charts to your OCI registry, then deploy:

```sh
helm registry login <oci-registry> --username <username> --password <password>
helm upgrade --install frontend oci://<oci-registry>/frontend --version 0.1.0 --namespace <namespace>
helm upgrade --install backend oci://<oci-registry>/backend --version 0.1.0 --namespace <namespace>
helm upgrade --install postgres bitnami/postgresql --namespace <namespace> -f values-postgres.yaml
```

## Values

See each chart’s `values.yaml` for configuration options. If desired, create a custom values file and use the `-f <filename>` flag to have Helm use it.

## Monitoring

Charts expose a metrics endpoint on port `9100` for Prometheus scraping.
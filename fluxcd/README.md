# FluxCD GitOps Manifests

This directory contains FluxCD resources for deploying the sample application stack in **dev** and **prod** environments.

## Structure

- `dev/` — Manifests for the development environment
- `prod/` — Manifests for the production environment

## Usage

Apply the desired environment’s kustomization:

```sh
kubectl apply -f dev/kustomization.yaml
kubectl apply -f prod/kustomization.yaml
```

Or apply HelmRelease manifests for GitOps deployments.

## Notes

- Update repository URLs and chart versions as needed.
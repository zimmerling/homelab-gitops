# Homelab GitOps Repository

This repository contains Kubernetes manifests managed by Flux CD for the homelab cluster.

## Structure

```
homelab-gitops/
├── clusters/homelab/          # Cluster-specific configuration
│   ├── flux-system/           # Flux CD system components
│   └── apps/                  # Application deployments for this cluster
└── apps/                      # Shared application definitions
```

## Flux CD

This repository is automatically synchronized to the Kubernetes cluster using Flux CD.

- **Cluster**: homelab
- **Sync Interval**: 1 minute
- **Auto-reconciliation**: Enabled

## Adding a New Application

1. Create application manifests in `apps/<app-name>/`
2. Create a Kustomization in `clusters/homelab/apps/<app-name>.yaml`
3. Commit and push - Flux will automatically deploy

## Monitoring

```bash
# Check Flux status
flux get all -A

# Check Kustomizations
flux get kustomizations

# Check Git sources
flux get sources git
```

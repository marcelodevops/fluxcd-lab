# fluxcd-lab

Flux CD bootstrap manifests for the `lab` cluster configuration.

## Bootstrap

Point `kubectl` at the cluster to manage, then install the Flux controllers and apply the manifests:

```sh
flux install
kubectl apply -k clusters/lab
```

Flux will read the `main` branch of this repository and reconcile `./clusters/lab` every 10 minutes. Update the branch or repository URL in `clusters/lab/flux-system/gotk-sync.yaml` if needed.

The Git repository is configured for unauthenticated HTTPS access. For a private repository, create a Git authentication Secret in the `flux-system` namespace and set `secretRef.name` on the `GitRepository` resource; do not commit credentials to this repository.

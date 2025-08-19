# Migration Notes

## Current State
- Installed with: <describe how you installed originally (e.g., kubectl apply -f ... )>
- Current version (from `argocd version`):  
  - Client: v2.14.11  
  - Server: v2.14.6

## Target State
- Managed via GitOps in this repository
- Pinned Argo CD version: v2.14.6
- Bootstrap path: `clusters/local/bootstrap/`

## Differences Identified
- [ ] Namespace definition differences  
- [ ] Service type (ClusterIP/LoadBalancer/NodePort)  
- [ ] Ingress/Route config  
- [ ] RBAC / argocd-cm tweaks  
- [ ] Any custom health checks or exclusions

## Migration Plan
1. Vendor manifests into repo (done).
2. Render and diff against live cluster:
  ```bash
  kustomize build clusters/local/bootstrap | kubectl diff -f -
  ```
3. Label all Git-tracked resources with app.kubernetes.io/managed-by=gitops.
4. Apply manifests with prune disabled.
5. Once aligned, introduce root Application in clusters/local/root/.
6. Enable automated sync + prune only when safe.

## Known Risks / TODOs

- <list any concerns you see during diff>
- <future work e.g., repo-creds secrets, AppSet introduction>
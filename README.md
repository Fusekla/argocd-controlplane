# argocd-controlplane

GitOps-managed installation and configuration of Argo CD control plane.

This repository contains the bootstrap manifests for deploying Argo CD into a cluster, along with configuration and migration notes.

---

## 📂 Structure
```
clusters/local/bootstrap/ # namespace + Argo CD install (vendored manifests)
clusters/local/root/ # (future) root Application / App of Apps
docs/ # migration notes, references
```

---

## 🚀 Quickstart

### Requirements
- `kubectl` installed and pointed at your cluster
- `kustomize` (or `kubectl kustomize`) available

### Render manifests
```bash
kustomize build clusters/local/bootstrap
```
### Apply manifests (⚠️ not yet)
```bash
kubectl apply -k clusters/local/bootstrap
```

## 📌 Versioning
- Pinned Argo CD version: **v2.14.6**
- Current live version: **v2.14.6**

## 📝 Notes
- See [docs/migration-notes.md](./docs/migration-notes.md) for details on differences between the current live setup and this Git-tracked configuration.
- Do **not** store sensitive information (repo credentials, tokens) in this repo.
# argocd-controlplane

GitOps-managed installation and configuration of Argo CD control plane.

This repository contains the bootstrap manifests for deploying Argo CD into a cluster, along with configuration and migration notes.

---

## 📂 Structure
```
clusters/local/bootstrap/ # namespace + Argo CD install (vendored manifests) + patches + AppProjects
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
### Apply manifests
```bash
kubectl apply -k clusters/local/bootstrap
```

## 📌 Versioning
- Current version : **v3.1.0**

## 📝 Notes
- Do **not** store sensitive information (repo credentials, tokens) in this repo.
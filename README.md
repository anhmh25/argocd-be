# ArgoCD

```
---
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: media-be
  namespace: argocd
  annotations:
    argocd-image-updater.argoproj.io/image-list: anhmhtera/media-be:~v0.1
  # finalizers:
  #   - resources-finalizer.argocd.argoproj.to
spec:
  project: default
  source:
    repoURL: https://github.com/anhmh25/argocd-be.git
    targetRevision: main
    path: media-be
    helm:
      parameters:
        - name: "image.repository"
          value: anhmhtera/media-be
        - name: "image.tag"
          value: v0.1.17
  destination:
    server: https://kubernetes.default.svc
    namespace: myapp
```

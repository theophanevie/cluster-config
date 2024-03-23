# Cluster config

The umbrella charts for my personal Kubernetes cluster.

### TODO

#### Argocd

- docs/operator-manual/declarative-setup.md
app.kubernetes.io/part-of: argocd
argo cd application helm chart configuration specifique 


metadata:
  finalizers:
    - resources-finalizer.argocd.argoproj.io

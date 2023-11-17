# ARGOCD CLI

- Connect to argocd server
```bash
kubectl -n argocd port-forward svc/argocd-server --address 0.0.0.0 8091:443
```
```bash
argocd login <ARGOCD_SERVER> --username <ARGOCD_USERNAME> --password <ARGOCD_PASSWORD> --insecure
argocd login localhost:8091 --insecure --username admin --password $(kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d)
```

- List Argocd Projects
```bash
argocd proj list
```

- List argocd projects with kubect
```bash
kubectl get appproj -n argocd
```
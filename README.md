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

- Argocd project create
```bash
argocd proj create <PROJECT_NAME> --description <PROJECT_DESCRIPTION> --dest <DESTINATION_CLUSTER> --src <SOURCE_CLUSTER>
```

- Argocd create sample project
```bash
argocd proj create <PROJECT_NAME> --description "<DESCRIPTION>" --src "<REPO_URL>" --dest "<CLUSTER_URL>,<NAMESPACE>"
```

- Argocd project yaml
```bash
argocd proj get <PROJECT_NAME> -o yaml
argocd proj get <PROJECT_NAME> -o json
argocd proj get argocd-example -o yaml
```

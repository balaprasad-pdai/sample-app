ArgoCD Application for `sample-app`

- Edit `argocd/application.yaml` and set `spec.source.repoURL` to your Git repository that contains this project.
- `spec.source.path` points to the `k8s` directory and will sync those manifests into the cluster namespace `sample-app`.

To create the app (when ArgoCD is running):

```bash
# Apply the Application CR in the argocd namespace
kubectl apply -f argocd/application.yaml -n argocd
```

Notes:
- If ArgoCD is configured with Git credentials you may need to use a repo URL with credentials or configure a Git credential in ArgoCD UI/secret.
- The Application uses `CreateNamespace=true` so ArgoCD will create the `sample-app` namespace when it syncs.

Kubernetes manifests for the sample-app

Files:
- namespace.yaml  : Namespace `sample-app`
- deployment.yaml : Deployment with 2 replicas (placeholder image)
- service.yaml    : ClusterIP service mapping port 80 -> container 5173
- ingress.yaml    : Ingress using host `sample-app.example.com` (replace host)

- Quick customize:
- If you're using the Docker Hub image you mentioned, the manifest already references:
-
- ```yaml
- image: populardigitalai/sample-app:latest
- ```
-
- To use a different tag (recommended for releases), update the tag portion, e.g.
- `populardigitalai/sample-app:v1.2.3`.
- Update `ingress.yaml` host to your real domain and TLS if needed.

Apply to cluster:

```bash
kubectl apply -f k8s/namespace.yaml
kubectl apply -f k8s/deployment.yaml -n sample-app
kubectl apply -f k8s/service.yaml -n sample-app
kubectl apply -f k8s/ingress.yaml -n sample-app
```

Or apply the whole folder:

```bash
kubectl apply -k k8s/   # if you add kustomization.yaml
# or
kubectl apply -R -f k8s/
```

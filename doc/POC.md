# AsciiArtify — GitOps PoC using k3d + ArgoCD

## 1. Pre-requisites

- `git`
- `docker`
- `k3d`
- `kubectl`

Check installations:

```bash
docker ps
k3d version
kubectl version --client
```

## 2. Create a k3d cluster

```bash
k3d cluster create asciiartify-argo
kubectl cluster-info
kubectl get all -A
```

## 3. Install ArgoCD

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl get all -n argocd
```

## 4. Access ArgoCD UI
```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

Open your browser and navigate to `https://localhost:8080`. Accept the rist and continue.
- Username: `admin`
- Password: (open new terminal and run the following command)
```bash
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d; echo
```

## Demo:

Link: [demo](https://asciinema.org/a/nwa6gGH9TN42yTLhfUFxITB3P)

![alt text](./media/demo4_2.gif)


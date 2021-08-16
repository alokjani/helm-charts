# helm-charts

# Install

To install a chart from this repository, first add the repo to helm configuration

```
$ helm repo add alokjani https://alokjani.github.io/helm-charts/
$ helm repo update
$ helm install my-nginx alokjani/nginx
```

To uninstall the repo

```
$ helm repo remove alokjani
```

# Development

```
HOMEBREW_NO_AUTO_UPDATE=1 \
  brew install k3d helm@3 kubectl
```

```
k3d cluster create k3s-rancher \
  --api-port 6550 \
  --servers 1 \
  --agents 3 \
  --port 443:443@loadbalancer
```

```
kubectl get nodes,all
```

Install Cert-Manager

```
kubectl create namespace cert-manager
helm repo add jetstack https://charts.jetstack.io
helm repo update
```

```
helm install \
  cert-manager jetstack/cert-manager \
  --namespace cert-manager \
  --version v0.12.0
```

```
kubectl -n cert-manager rollout status deploy/cert-manager        # should show "successfully rolled out"
kubectl get pods --namespace cert-manager                         # should show 3 running pods
```

With `cert-manager` installed, Use `Helm` to install `Rancher`

```
helm repo add rancher-latest https://releases.rancher.com/server-charts/latest && \
helm repo update && \
kubectl create namespace cattle-system && \
helm install rancher rancher-latest/rancher \
  --namespace cattle-system \
  --set hostname=rancher.k3d.localhost
```

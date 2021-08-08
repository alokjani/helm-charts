# helm-charts

# Install

To install a chart from this repository, first add the repo to helm configuration

$ helm repo add alokjani https://alokjani.github.io/helm-charts/
$ helm repo update
$ helm install my-nginx alokjani/nginx

To uninstall the repo

$ helm repo remove alokjani

# Development

HOMEBREW_NO_AUTO_UPDATE=1 \
  brew install k3d helm@3 kubectl

k3d cluster create k3s-rancher \
  --api-port 6550 \
  --servers 1 \
  --agents 3 \
  --port 443:443@loadbalancer

kubectl get nodes,all

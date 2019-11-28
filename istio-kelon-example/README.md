# Istio Kelon Example

This example will help, deploying Istio, Prometheus, Grafana and Kelon to test Kelons capabilities combined with Istio.

1. Install istio to Kubernetes

```sh
helm repo add istio https://storage.googleapis.com/istio-release/releases/1.4.0/charts/

kubectl apply -f ./istio-ns.yaml

helm install -f ./istio-init-values.yaml --namespace istio-system istio-init  istio/istio-init

helm install -f ./istio-values.yaml --namespace istio-system istio istio/istio

kubectl -n istio-system port-forward svc/grafana 3000:3000
```

2. Install Kelon and example app with Istio Injection

```sh
kubectl create namespace kelon
kubectl label namespace kelon istio-injection=enabled
```

Clone and follow the instructions inside the Kelon example folder.

3. Deploy Istio External Auth rule to combine Istio and Kelon


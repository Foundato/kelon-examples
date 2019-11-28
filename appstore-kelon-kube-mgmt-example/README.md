# Installation

```bash
# Create namespace
kubectl create namespace appstore
kubectl create namespace kelon

# Load configmaps
kubectl apply -f ./manifests/configmaps-appstore.yml
kubectl apply -f ./manifests/configmaps-kelon.yml

# Start PostgreSQL
helm install -n appstore -f ./manifests/postgres-values.yml postgres stable/postgresql

# Start Appstore
kubectl apply -f ./manifests/appstore-deployment.yml

# Start Kelon
kubectl apply -f ./manifests/kube-mgmt-deployment.yml
```

# Shutdown
```bash
kubectl delete namespace kelon
kubectl delete namespace appstore
```

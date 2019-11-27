# Installation

```bash

helm repo add stable https://kubernetes-charts.storage.googleapis.com/
helm repo update

# Create namespace
kubectl create namespace kelon

# Load configmaps
kubectl apply -f ./manifests/configmaps.yml

# Start MongoDB
helm install -n kelon -f ./manifests/mongo-values.yml --set persistence.enabled=false mongo stable/mongodb

# Start PostgreSQL
helm install -n kelon -f ./manifests/postgres-values.yml --set persistence.enabled=false postgres stable/postgresql

# Start MySQL
helm install -n kelon -f ./manifests/mysql-values.yml --set persistence.enabled=false mysql stable/mysql

# Start Kelon
kubectl apply -f ./manifests/kube-mgmt-deployment.yml
```

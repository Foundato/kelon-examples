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

# Test

```bash
# Forward UI from appstore to local machine
kubectl -n appstore port-forward svc/appstore-service 8080
````

After the Web-UI of the appstore is forwarded to your local machine, you should be able to connect [here](http://localhost:8080/)

# Shutdown
```bash
kubectl delete namespace kelon
kubectl delete namespace appstore
```

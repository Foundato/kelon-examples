# Installation

```bash
# Create namespace
kubectl create namespace appstore
kubectl create namespace kelon

# Load configmaps
kubectl apply -f ./manifests/configmaps-appstore.yml
kubectl apply -f ./manifests/configmaps-kelon.yml
kubectl apply -f ./manifests/configmaps-envoy.yml

# Start PostgreSQL
helm install -n appstore -f ./manifests/postgres-values.yml postgres stable/postgresql

# Start Kelon
kubectl apply -f ./manifests/kelon-deployment.yml

# Start Appstore
kubectl apply -f ./manifests/appstore-deployment.yml

# Start Envoy
kubectl apply -f ./manifests/envoy-deployment.yml
```

# Test

```bash
# Forward envoy to local machine
kubectl -n appstore port-forward svc/envoy-proxy-service 8080:8000 8081:8001
# Forward UI from appstore to local machine
kubectl -n appstore port-forward svc/appstore-frontend-service 8082:80
````

After the Web-UI of the appstore is forwarded to your local machine, you should be able to connect [here](http://localhost:8082/)

# Shutdown
```bash
kubectl delete namespace kelon
kubectl delete namespace appstore
```

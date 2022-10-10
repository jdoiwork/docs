# Step 1 Create a new service

```bash
kubectl get pods
```

```bash
kubectl expose deployment/kubernetes-bootcamp --type="NodePort" --port 8080
```

```bash
kubectl get pods
```

```bash
kubectl describe services/kubernetes-bootcamp
```

```bash
export NODE_PORT=$(kubectl get services/kubernetes-bootcamp -o go-template='{{(index .spec.ports 0).nodePort}}')
echo NODE_PORT=$NODE_PORT
```

```bash
curl $(minikube ip):$NODE_PORT
```

# Step 2: Using labels

```bash
kubectl describe deployment
```

```bash
kubectl get pods -l app=kubernetes-bootcamp
```

```bash
kubectl get services -l app=kubernetes-bootcamp
```

```bash
export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}')
echo Name of the Pod: $POD_NAME
```

```bash
kubectl label pods $POD_NAME version=v1
```

```bash
kubectl describe pods $POD_NAME
```

```bash
kubectl get pods -l version=v1
```

# Step 3 Deleting a service

```bash
kubectl delete service -l app=kubernetes-bootcamp
```

```bash
kubectl get services
```

```bash
# Failed to connect
curl $(minikube ip):$NODE_PORT
```

```bash
kubectl exec -ti $POD_NAME -- curl localhost:8080
```


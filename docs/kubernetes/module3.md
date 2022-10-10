# Step 1 Check application configuration

```bash
kubectl get pods
```

```bash
kubectl describe pods
```

# Step 2 Show the app in the terminal

```bash
# 別ターミナルで実行
kubectl proxy
```

```bash
# 元のターミナルで実行
export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}')
echo Name of the Pod: $POD_NAME
```

```bash
curl http://localhost:8001/api/v1/namespaces/default/pods/$POD_NAME/proxy/
```

# Step 3 View the container logs

```bash
kubectl logs $POD_NAME
```

# Step 4 Executing command on the container

```bash
kubectl exec $POD_NAME -- env
```

```bash
kubectl exec -ti $POD_NAME -- bash
cat server.js
curl localhost:8080
exit
```

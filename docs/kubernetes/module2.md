# kubectl basics

コマンドのあとに `--help` をつけると利用可能な追加のパラメーターが表示される

```bash
kubectl version
```

```bash
kubectl get nodes
```
# Deploy our app

```bash
kubectl create deployment kubernetes-bootcamp --image=gcr.io/google-samples/kubernetes-bootcamp:v1
```

```bash
kubectl get deployments
```

# View our app

```bash
# 別のターミナルで実行する
kubectl proxy
```

```bash
# 元のターミナルで実行する
curl http://localhost:8001/version
```

```bash
export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.mtadata.name}}{{"\n"}}{{end}}')
echo Name of the Pod: $POD_NAME
```

```bash
curl http://localhost:8001/api/v1/namespaces/default/pods/$POD_NAME/
```

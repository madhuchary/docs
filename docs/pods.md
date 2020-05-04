---
id: pods
title: Pods
---

Pod is a kubernetes object which runs one or more containers and pod spec is written is YAML file

Example of POD with http container

[pod-ex1.yaml](/pod-ex1.yaml)

```yml
---
apiVersion: v1
kind: Pod
metadata:
   name: pod-example
spec:
   containers:
   - name: web
    image: httpd
```

API Version depends on Kind of Object. Pod comes under v1

For more info on api click [here](https://kubernetes.io/docs/reference/using-api/api-overview/)

Kind difines kubernetes object. Container is a object of pod kind

Spec is a specifiation of container like image name, container name, container port, volumes etc..

To create a pod use 

```bash
cat <<EOF > pod-ex1.yaml
---
apiVersion: v1
kind: Pod
metadata:
   name: pod-example
spec:
   containers:
   - name: web
    image: httpd
EOF

kubectl create -f pod-ex1.yaml
```
To check if pod is created 

```
kubectl get pods
```

```bash
kubectl describe pod
kubectl delete pod pod-name
kubectl logs -f pod-name
```

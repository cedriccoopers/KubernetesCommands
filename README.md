## Get nodes and Deploy service
```
kubectl get nodes
kubectl get deployments
kubectl expose deployment hello-minikube --type=NodePort --port=8080
kubectl delete services hello-minikube
kubectl delete deployment hello-minikube
kubectl get nodes
```

## RUN PODS
```
kubectl get pods
kubectl describe pod nginx
kubectl get pods -o wide
```

## YAML
### Create a POD using YAML based configuration
### POD definition minimum fields
```
 apiVersion: v1
 kind: POD / Service / ReplicaSet / Deployment
 metadata:
   name: myapp-pod
   labels:
      app: myapp
      type: front-end
 spec:
  containers:
      - name: nginx-container
        image: nginx
```
### To execute the above file run
```
kubectl create -f "name-of-file.yaml"
```
### To see the POD execute
```
kubectl get pods
```
### To describe the POD execute
```
kubectl describe pod myapp-pod
```
### pod.yaml
```
apiVersion: v1
kind: Pod
metadata:
  name: cedric
  labels:
    app: nginx
    tier: frontend
spec:
  containers:
  -  name: cedric
     image: nginx
```
### To create the pod on the above yaml file execute
```
kubectl apply -f pod.yaml
```



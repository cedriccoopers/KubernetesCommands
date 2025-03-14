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
    - name: cedric
      image: nginx
```
### To create the pod on the above yaml file execute
```
kubectl apply -f pod.yaml
```
## ReplicaSet
```
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: myapp-replicaset
  labels:
    app: myapp
spec:
  selector:
    matchLabels:
      app: myapp
  replicas: 3
  template:
    metadata:
      name: nginx
      labels:
        app: myapp
    spec:
      containers:
        - name: ngix
          image: ngix
```
### To make sure the file is correc, execute
```
cat replicaSet.yaml
```
### To create the ReplicaSet, execute
```
kubectl create -f replicaSet.yaml
```
### To view the status of the ReplicaSet, execute
```
kubectl get replicaset
kubectl get rs
```
## Deployments
### Rolling Upgrades - Deploy one after another
### Deployment is higher than Replica Set
### Create a new Deployment
#### Name: httpd-frontend
#### Replicas: 3
#### Image: httpd:2.4-alpine
```
kubectl create deployment httpd-frontend --image=httpd:2.4-alpine --replicas=3 
```






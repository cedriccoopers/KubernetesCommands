CedricMaluleka@CMAC-J2YG7597HH ~ % minikube status
zsh: command not found: minikube
CedricMaluleka@CMAC-J2YG7597HH ~ % kubectl get nodes
NAME                   STATUS   ROLES                  AGE   VERSION
lima-rancher-desktop   Ready    control-plane,master   45h   v1.31.5+k3s1
CedricMaluleka@CMAC-J2YG7597HH ~ % kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.10
deployment.apps/hello-minikube created
CedricMaluleka@CMAC-J2YG7597HH ~ % kubectl get deployments
NAME             READY   UP-TO-DATE   AVAILABLE   AGE
hello-minikube   0/1     1            0           27s
CedricMaluleka@CMAC-J2YG7597HH ~ % kubectl expose deployment hello-minikube --type=NodePort --port=8080
service/hello-minikube exposed
CedricMaluleka@CMAC-J2YG7597HH ~ % minikube service hello-minikube --url
zsh: command not found: minikube
CedricMaluleka@CMAC-J2YG7597HH ~ % kubectl get service -n hello-minikube
No resources found in hello-minikube namespace.
CedricMaluleka@CMAC-J2YG7597HH ~ % minikube service --all               
zsh: command not found: minikube
CedricMaluleka@CMAC-J2YG7597HH ~ % minikube start        
zsh: command not found: minikube
CedricMaluleka@CMAC-J2YG7597HH ~ % kubectl delete services hello-minikube
service "hello-minikube" deleted
CedricMaluleka@CMAC-J2YG7597HH ~ % kubectl delete deployment hello-minikube
deployment.apps "hello-minikube" deleted
CedricMaluleka@CMAC-J2YG7597HH ~ % kubectl get nodes
NAME                   STATUS   ROLES                  AGE   VERSION
lima-rancher-desktop   Ready    control-plane,master   45h   v1.31.5+k3s1
CedricMaluleka@CMAC-J2YG7597HH ~ % kubectl run nginx --image=nginx
pod/nginx created
CedricMaluleka@CMAC-J2YG7597HH ~ % kubectl get pods
NAME    READY   STATUS              RESTARTS   AGE
nginx   0/1     ContainerCreating   0          14s
CedricMaluleka@CMAC-J2YG7597HH ~ % kubectl get pods
NAME    READY   STATUS              RESTARTS   AGE
nginx   0/1     ContainerCreating   0          27s
CedricMaluleka@CMAC-J2YG7597HH ~ % kubectl describe pod nginx
Name:             nginx
Namespace:        default
Priority:         0
Service Account:  default
Node:             lima-rancher-desktop/192.168.5.15
Start Time:       Thu, 13 Mar 2025 09:10:13 +0200
Labels:           run=nginx
Annotations:      <none>
Status:           Running
IP:               10.42.0.15
IPs:
  IP:  10.42.0.15
Containers:
  nginx:
    Container ID:   docker://eeb2b3ce76bdc4d3a0fe553ed6e76b7d79fa57d38e63d79767a7a9cd27db3ed1
    Image:          nginx
    Image ID:       docker-pullable://nginx@sha256:9d6b58feebd2dbd3c56ab5853333d627cc6e281011cfd6050fa4bcf2072c9496
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Thu, 13 Mar 2025 09:11:58 +0200
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-csk9s (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True 
  Initialized                 True 
  Ready                       True 
  ContainersReady             True 
  PodScheduled                True 
Volumes:
  kube-api-access-csk9s:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age    From               Message
  ----    ------     ----   ----               -------
  Normal  Scheduled  5m18s  default-scheduler  Successfully assigned default/nginx to lima-rancher-desktop
  Normal  Pulling    5m19s  kubelet            Pulling image "nginx"
  Normal  Pulled     3m34s  kubelet            Successfully pulled image "nginx" in 1m44.248s (1m44.248s including waiting). Image size: 197285467 bytes.
  Normal  Created    3m34s  kubelet            Created container nginx
  Normal  Started    3m34s  kubelet            Started container nginx
CedricMaluleka@CMAC-J2YG7597HH ~ % 

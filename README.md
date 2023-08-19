# Node.js-App-with-K8s-yaml
Running Nodejs application using K8s declarative approach

## 1. k8s-web-hello-single-deployment
C:\Users\naz\docker_playground\k8s> ls


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         8/18/2023  12:23 PM                k8s-web-hello
-a----         8/18/2023   5:48 PM              0 deployment.yaml
-a----         8/19/2023   6:39 AM            460 service.yaml


PS C:\Users\naz\docker_playground\k8s> kubectl apply -f C:\Users\naz\docker_playground\k8s\deployment.yaml
Error from server (BadRequest): error when creating "C:\\Users\\naz\\docker_playground\\k8s\\deployment.yaml": Deployment in version "v1" cannot be handled as a DepPS C:\Users\naz\docker_playground\k8s> kubectl apply -f deployment.yaml
ield "spec.template.kind"
// solution : removed second trace of kind in yaml

PS C:\Users\naz\docker_playground\k8s> kubectl apply -f deployment.yaml
deployment.apps/k8s-web-hello created
PS C:\Users\naz\docker_playground\k8s> kubectl get  deployment
NAME            READY   UP-TO-DATE   AVAILABLE   AGE
k8s-web-hello   1/1     1            1           39s
NAME                             READY   STATUS    RESTARTS   AGE
k8s-web-hello-59fd9b4b7f-dwqp7   1/1     Running   0          61s
deployment.apps/k8s-web-hello configured
PS C:\Users\naz\docker_playground\k8s> kubectl get pods
NAME                             READY   STATUS              RESTARTS   AGE
k8s-web-hello-59fd9b4b7f-4f5g7   0/1     ContainerCreating   0          2s
k8s-web-hello-59fd9b4b7f-dwqp7   1/1     Running             0          3m43s
k8s-web-hello-59fd9b4b7f-gh6xx   0/1     ContainerCreating   0          2s
k8s-web-hello-59fd9b4b7f-thfzl   0/1     ContainerCreating   0          2s
NAME            READY   UP-TO-DATE   AVAILABLE   AGE
k8s-web-hello   5/5     5            5           3m49s
PS C:\Users\naz\docker_playground\k8s> kubectl get pods       
k8s-web-hello-59fd9b4b7f-4f5g7   1/1     Running   0          11s
k8s-web-hello-59fd9b4b7f-dwqp7   1/1     Running   0          3m52s
k8s-web-hello-59fd9b4b7f-gh6xx   1/1     Running   0          11s
k8s-web-hello-59fd9b4b7f-thfzl   1/1     Running   0          11s
PS C:\Users\naz\docker_playground\k8s> kubectl apply -f service.yaml   
service/k8s-web-hello created
🤷  This control plane is not running! (state=Stopped)
👉  To start a cluster, run: "minikube start"
PS C:\Users\naz\docker_playground\k8s> kubectl get svc
NAME            TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
kubernetes      ClusterIP      10.96.0.1       <none>        443/TCP          13h
PS C:\Users\naz\docker_playground\k8s> kubectl get svc
NAME            TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
kubernetes      ClusterIP      10.96.0.1       <none>        443/TCP          13h
PS C:\Users\naz\docker_playground\k8s> kubectl apply -f service.yaml 
service/k8s-web-hello unchanged
PS C:\Users\naz\docker_playground\k8s> kubectl get svc
NAME            TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
k8s-web-hello   LoadBalancer   10.107.158.41   <pending>     3030:32713/TCP   2m6s
kubernetes      ClusterIP      10.96.0.1       <none>        443/TCP          13h
PS C:\Users\naz\docker_playground\k8s> minikube service k8s-web-hello
|-----------|---------------|-------------|-----------------------------|
| NAMESPACE |     NAME      | TARGET PORT |             URL             |
|-----------|---------------|-------------|-----------------------------|
| default   | k8s-web-hello |        3030 | http://172.20.168.192:32713 |
|-----------|---------------|-------------|-----------------------------|
* Opening service default/k8s-web-hello in default browser...

PS C:\Users\naz\docker_playground\k8s>
## 2. k8s-web-hello-multiple-deployment



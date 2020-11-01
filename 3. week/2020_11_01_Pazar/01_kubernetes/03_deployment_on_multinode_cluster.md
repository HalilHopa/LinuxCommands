## Demo on 4-nodes Kubernetes Cluster

- get nodes
```
[root@kubernetes1 ~]# kubectl get nodes
NAME                        STATUS   ROLES    AGE   VERSION
kubernetes1.datalonga.com   Ready    master   51d   v1.19.1
kubernetes3.datalonga.com   Ready    <none>   51d   v1.19.1
kubernetes4.datalonga.com   Ready    <none>   51d   v1.19.1
kubernetes5.datalonga.com   Ready    <none>   51d   v1.19.1
```

- Deployment file (nginx-deployment.yaml)
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

- Apply deployment
```
[root@kubernetes1 ~]# kubectl apply -f /home/murat/nginx-deployment.yaml
deployment.apps/nginx-deployment created
```

- Get pods
```
[root@kubernetes1 ~]# kubectl get pods
NAME                                READY   STATUS    RESTARTS   AGE
nginx-deployment-66b6c48dd5-jrwzr   1/1     Running   0          2m18s
nginx-deployment-66b6c48dd5-q6rwz   1/1     Running   0          2m18s
nginx-deployment-66b6c48dd5-z6dr8   1/1     Running   0          2m18s
```

- get all
```
[root@kubernetes1 ~]# kubectl get all
NAME                                    READY   STATUS    RESTARTS   AGE
pod/nginx-deployment-66b6c48dd5-jrwzr   1/1     Running   0          3m2s
pod/nginx-deployment-66b6c48dd5-q6rwz   1/1     Running   0          3m2s
pod/nginx-deployment-66b6c48dd5-z6dr8   1/1     Running   0          3m2s

NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   51d

NAME                               READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/nginx-deployment   3/3     3            3           3m2s

NAME                                          DESIRED   CURRENT   READY   AGE
replicaset.apps/nginx-deployment-66b6c48dd5   3         3         3       3m2s
```

- Scale up the deployment
`kubectl scale deployment.v1.apps/nginx-deployment --replicas=5`

- Get replicasets
```
[root@kubernetes1 ~]# kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-66b6c48dd5   5         5         5       5m19s
```

- Autoscale a deployment
```
[root@kubernetes1 ~]# kubectl autoscale deployment.v1.apps/nginx-deployment --min=2 --max=6 --cpu-percent=80
horizontalpodautoscaler.autoscaling/nginx-deployment autoscaled
```

- Get all pods in detail
```
[root@kubernetes1 ~]# kubectl get all -o wide
NAME                                    READY   STATUS    RESTARTS   AGE     IP                NODE                        NOMINATED NODE   READINESS GATES
pod/nginx-deployment-66b6c48dd5-cnt2q   1/1     Running   0          2m45s   192.168.197.66    kubernetes4.datalonga.com   <none>           <none>
pod/nginx-deployment-66b6c48dd5-jrwzr   1/1     Running   0          7m54s   192.168.12.199    kubernetes5.datalonga.com   <none>           <none>
pod/nginx-deployment-66b6c48dd5-q6rwz   1/1     Running   0          7m54s   192.168.197.65    kubernetes4.datalonga.com   <none>           <none>
pod/nginx-deployment-66b6c48dd5-sg52p   1/1     Running   0          2m45s   192.168.196.194   kubernetes3.datalonga.com   <none>           <none>
pod/nginx-deployment-66b6c48dd5-z6dr8   1/1     Running   0          7m54s   192.168.196.193   kubernetes3.datalonga.com   <none>           <none>

NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE   SELECTOR
service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   51d   <none>

NAME                               READY   UP-TO-DATE   AVAILABLE   AGE     CONTAINERS   IMAGES         SELECTOR
deployment.apps/nginx-deployment   5/5     5            5           7m54s   nginx        nginx:1.14.2   app=nginx

NAME                                          DESIRED   CURRENT   READY   AGE     CONTAINERS   IMAGES         SELECTOR
replicaset.apps/nginx-deployment-66b6c48dd5   5         5         5       7m54s   nginx        nginx:1.14.2   app=nginx,pod-template-hash=66b6c48dd5

NAME                                                   REFERENCE                     TARGETS         MINPODS   MAXPODS   REPLICAS   AGE
horizontalpodautoscaler.autoscaling/nginx-deployment   Deployment/nginx-deployment   <unknown>/80%   2         6         5          83s
```

- update a deployment (update image)
```
[root@kubernetes1 ~]# kubectl set image deployment.v1.apps/nginx-deployment nginx=nginx:1.16.1
```

- get replicasets
```
[root@kubernetes1 ~]# kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-559d658b74   3         3         0       44s
nginx-deployment-66b6c48dd5   4         4         4       9m38s

[root@kubernetes1 ~]# kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-559d658b74   4         4         1       68s
nginx-deployment-66b6c48dd5   3         3         3       10m

[root@kubernetes1 ~]# kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-559d658b74   4         4         1       70s
nginx-deployment-66b6c48dd5   3         3         3       10m

[root@kubernetes1 ~]# kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-559d658b74   4         4         1       75s
nginx-deployment-66b6c48dd5   3         3         3       10m

[root@kubernetes1 ~]# kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-559d658b74   4         4         1       76s
nginx-deployment-66b6c48dd5   3         3         3       10m

[root@kubernetes1 ~]# kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-559d658b74   5         5         2       87s
nginx-deployment-66b6c48dd5   2         2         2       10m

[root@kubernetes1 ~]# kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-559d658b74   5         5         3       90s
nginx-deployment-66b6c48dd5   1         1         1       10m

[root@kubernetes1 ~]# kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-559d658b74   5         5         3       92s
nginx-deployment-66b6c48dd5   1         1         1       10m

[root@kubernetes1 ~]# kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-559d658b74   5         5         3       93s
nginx-deployment-66b6c48dd5   1         1         1       10m

[root@kubernetes1 ~]# kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-559d658b74   5         5         4       94s
nginx-deployment-66b6c48dd5   0         0         0       10m
```

- get rs in detail
```
[root@kubernetes1 ~]# kubectl get rs -o wide
NAME                          DESIRED   CURRENT   READY   AGE     CONTAINERS   IMAGES         SELECTOR
nginx-deployment-559d658b74   5         5         5       2m47s   nginx        nginx:1.16.1   app=nginx,pod-template-hash=559d658b74
nginx-deployment-66b6c48dd5   0         0         0       11m     nginx        nginx:1.14.2   app=nginx,pod-template-hash=66b6c48dd5
```

- open a port to outside
```
[root@kubernetes1 ~]# kubectl create service nodeport nginx --tcp=80:80
service/nginx created
```

- get services and learn port number
```
[root@kubernetes1 ~]# kubectl get services
NAME         TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
kubernetes   ClusterIP   10.96.0.1       <none>        443/TCP        51d
nginx        NodePort    10.102.50.212   <none>        80:31673/TCP   53s
```

- Open browser and try 
http://kubernetes3.datalonga.com:31673/  
http://kubernetes4.datalonga.com:31673/  
http://kubernetes5.datalonga.com:31673/

You must see the nginx wellcome page.

- shutdown k85 machine and get pods

```
[root@kubernetes1 ~]# kubectl get nodes
NAME                        STATUS     ROLES    AGE   VERSION
kubernetes1.datalonga.com   Ready      master   51d   v1.19.1
kubernetes3.datalonga.com   Ready      <none>   51d   v1.19.1
kubernetes4.datalonga.com   Ready      <none>   51d   v1.19.1
kubernetes5.datalonga.com   NotReady   <none>   51d   v1.19.1
```

You see k85 node is not ready. But we can still reach nginx from other servers.

- Start k85 server again and check nodes.

```
[root@kubernetes1 ~]# kubectl get nodes
NAME                        STATUS     ROLES    AGE   VERSION
kubernetes1.datalonga.com   Ready      master   51d   v1.19.1
kubernetes3.datalonga.com   Ready      <none>   51d   v1.19.1
kubernetes4.datalonga.com   Ready      <none>   51d   v1.19.1
kubernetes5.datalonga.com   NotReady   <none>   51d   v1.19.1

[root@kubernetes1 ~]# kubectl get nodes
NAME                        STATUS     ROLES    AGE   VERSION
kubernetes1.datalonga.com   Ready      master   51d   v1.19.1
kubernetes3.datalonga.com   Ready      <none>   51d   v1.19.1
kubernetes4.datalonga.com   Ready      <none>   51d   v1.19.1
kubernetes5.datalonga.com   NotReady   <none>   51d   v1.19.1

[root@kubernetes1 ~]# for i in {1..10}; do sleep 1; kubectl get nodes; done
NAME                        STATUS   ROLES    AGE   VERSION
kubernetes1.datalonga.com   Ready    master   51d   v1.19.1
kubernetes3.datalonga.com   Ready    <none>   51d   v1.19.1
kubernetes4.datalonga.com   Ready    <none>   51d   v1.19.1
kubernetes5.datalonga.com   Ready    <none>   51d   v1.19.1
```

- get rs 
```
[root@kubernetes1 ~]# kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-559d658b74   5         5         5       14m
nginx-deployment-66b6c48dd5   0         0         0       23m
```

- Autoscale a deployment
```

```
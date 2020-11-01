- nginx deployment yaml file

```
[train@localhost play]$ cat nginx-deployment.yaml
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

- Create a deploymet

`[train@localhost play]$ kubectl apply -f nginx-deployment.yaml`

- Get pods
```
[train@localhost play]$ kubectl get pods
NAME                                READY   STATUS    RESTARTS   AGE
nginx-deployment-66b6c48dd5-4f8hv   1/1     Running   0          33s
nginx-deployment-66b6c48dd5-7p96h   1/1     Running   0          33s
nginx-deployment-66b6c48dd5-bd5gq   1/1     Running   0          33s
```

- get all
```
[train@localhost play]$ kubectl get all
NAME                                    READY   STATUS    RESTARTS   AGE
pod/nginx-deployment-66b6c48dd5-4f8hv   1/1     Running   0          63s
pod/nginx-deployment-66b6c48dd5-7p96h   1/1     Running   0          63s
pod/nginx-deployment-66b6c48dd5-bd5gq   1/1     Running   0          63s

NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   16d

NAME                               READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/nginx-deployment   3/3     3            3           63s

NAME                                          DESIRED   CURRENT   READY   AGE
replicaset.apps/nginx-deployment-66b6c48dd5   3         3         3       63s
```

- Scale up the deployment

`kubectl scale deployment.v1.apps/nginx-deployment --replicas=5`

```
[train@localhost play]$ kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-66b6c48dd5   5         5         5       36m
```

- Autoscale a deployment 
```
[train@localhost play]$ kubectl autoscale deployment.v1.apps/nginx-deployment --min=2 --max=6 --cpu-percent=80
horizontalpodautoscaler.autoscaling/nginx-deployment autoscaled
```

- Get all 
```
[train@localhost play]$ kubectl get all
NAME                                    READY   STATUS    RESTARTS   AGE
pod/nginx-deployment-66b6c48dd5-2qsrx   1/1     Running   0          2m39s
pod/nginx-deployment-66b6c48dd5-4f8hv   1/1     Running   0          38m
pod/nginx-deployment-66b6c48dd5-7p96h   1/1     Running   0          38m
pod/nginx-deployment-66b6c48dd5-bd5gq   1/1     Running   0          38m
pod/nginx-deployment-66b6c48dd5-vfz2n   1/1     Running   0          2m39s

NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   16d

NAME                               READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/nginx-deployment   5/5     5            5           38m

NAME                                          DESIRED   CURRENT   READY   AGE
replicaset.apps/nginx-deployment-66b6c48dd5   5         5         5       38m

NAME                                                   REFERENCE                     TARGETS         MINPODS   MAXPODS   REPLICAS   AGE
horizontalpodautoscaler.autoscaling/nginx-deployment   Deployment/nginx-deployment   <unknown>/80%   2         6         5          35s
```

- update a deployment (update image)
```
[train@localhost play]$ kubectl set image deployment.v1.apps/nginx-deployment nginx=nginx:1.16.1
deployment.apps/nginx-deployment image updated

[train@localhost play]$ kubectl get deploy
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
nginx-deployment   4/5     3            4           41m
````

- get replicasets
```
[train@localhost play]$ kubectl get rs
NAME                          DESIRED   CURRENT   READY   AGE
nginx-deployment-559d658b74   5         5         5       69s
nginx-deployment-66b6c48dd5   0         0         0       43m
```

- open a port to outside
```
[train@localhost play]$ kubectl create service nodeport nginx --tcp=80:80
service/nginx created

[train@localhost play]$ kubectl get service -o wide
NAME         TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE   SELECTOR
kubernetes   ClusterIP   10.96.0.1        <none>        443/TCP        17d   <none>
nginx        NodePort    10.104.245.100   <none>        80:32356/TCP   49s   app=nginx
```

- Connect minikube and see the result with curl
```
# Connect to minikube (docker container)
[train@localhost play]$ minikube ssh

# reach to nginx (it is like browsing)
docker@minikube:~$ curl localhost:32356
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

- Check if docker is running

`[train@localhost advanced_ds_bigdata]$ sudo systemctl status docker`

`[train@localhost ~]$ minikube start`

- From the terminal inside virtual machine

`[train@localhost ~]$ minikube dashboard`  

http://127.0.0.1:43644/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/

It will open automatically. Ctrl+C to stop.

- Cluster info 
```
[train@localhost play]$ kubectl cluster-info
Kubernetes master is running at https://172.17.0.2:8443
KubeDNS is running at https://172.17.0.2:8443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

- List nodes
```
[train@localhost play]$ kubectl get nodes
NAME       STATUS   ROLES    AGE   VERSION
minikube   Ready    master   17d   v1.19.0
```

- Create hello-minikube deployment

`[train@localhost ~]$ kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4`

- Exposing a service as a NodePort

`[train@localhost ~]$ kubectl expose deployment hello-minikube --type=NodePort --port=8080`  

minikube makes it easy to open this exposed endpoint in your browser:

```
[train@localhost ~]$ minikube service hello-minikube
|-----------|----------------|-------------|-------------------------|
| NAMESPACE |      NAME      | TARGET PORT |           URL           |
|-----------|----------------|-------------|-------------------------|
| default   | hello-minikube |        8080 | http://172.17.0.2:30640 |
|-----------|----------------|-------------|-------------------------|
🎉  Opening service default/hello-minikube in default browser...
This tool has been deprecated, use 'gio open' instead.
See 'gio help open' for more info.
```

- To connect minikube docker `minikube ssh`
```
(venvspark) [train@localhost advanced_ds_bigdata]$ minikube ssh
docker@minikube:~$ exit
logout
(venvspark) [train@localhost advanced_ds_bigdata]$
```



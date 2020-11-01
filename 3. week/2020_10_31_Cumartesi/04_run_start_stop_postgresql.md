## run a postgresql-10 container

```
[train@localhost play]$ docker run --name postgresql -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=Ankara06 -d postgres:10
Unable to find image 'postgres:10' locally
10: Pulling from library/postgres
75cb2ebf3b3c: Downloading [======>                                            ]  2.993MB/22.52MB
3ca6415d2bca: Downloading [=================================================> ]  4.479MB/4.502MB
ac08e6372a7b: Download complete
b4394fce95ce: Download complete
6edcd5da08e3: Downloading [======================>                            ]  2.788MB/6.183MB
3380dcb7db08: Waiting
c7c147d9c90d: Waiting
08ae47fef758: Waiting
600fb961b7b5: Waiting
370a6d5f1feb: Waiting
5ea1202ea159: Waiting
7eb7385d875e: Waiting
9635213da414: Waiting
eb56cef8815a: Waiting
```

- --name: Assign a name to the container (easier to use than container_id)  
- -e (--env): Set environment variables  
- -d (--detach): Run container in background and print container ID 

## Check if it is running   (list running containers)
```
[train@localhost play]$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
b6916c4245b8        postgres:10         "docker-entrypoint.s…"   5 minutes ago       Up 5 minutes        5432/tcp            postgresql
```
## stop postgresql-10 container by name and container_id   
- stop by name  
```
[train@localhost play]$ docker stop postgresql
postgresql

[train@localhost play]$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```
- stop by container_id 
``` 
[train@localhost play]$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
b6916c4245b8        postgres:10         "docker-entrypoint.s…"   7 minutes ago       Up 6 seconds        5432/tcp            postgresql

[train@localhost play]$ docker container stop b6916c4245b8
b6916c4245b8

[train@localhost play]$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```
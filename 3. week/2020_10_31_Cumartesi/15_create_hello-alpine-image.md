In this demo we will make a simple Dockerfile, create container from it and push image to dockerhub.    

## Create a Docker file
```
[train@localhost images]$ pwd
/home/train/advanced_ds_bigdata/docker/play/images


[train@localhost images]$ cat Dockerfile
FROM alpine:3.11

CMD ["echo", "Hello, I am a container created by alpine:3.11 base image"]
```

## Build docker image
```
[train@localhost images]$ docker image build -t erkansirin78/hello-alpine:1.0 .
Sending build context to Docker daemon  3.072kB
Step 1/2 : FROM alpine:3.11
 ---> f70734b6a266
Step 2/2 : CMD ["echo", "Hello, I am a container created by alpine:3.11 base image"]
 ---> Running in 7cabc8a09ba3
Removing intermediate container 7cabc8a09ba3
 ---> 456785928537
Successfully built 456785928537
Successfully tagged erkansirin78/hello-alpine:1.0
```

## Create and start container from image
```
[train@localhost images]$ docker run --rm erkansirin78/hello-alpine:1.0
Hello, I am a container created by alpine:3.11 base image
```

## Push image to Dockerhub
- Get login from terminal
```
[train@localhost images]$ docker login
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username: erkansirin78
Password:
WARNING! Your password will be stored unencrypted in /home/train/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
```

- Push image
```
[train@localhost images]$ docker image push erkansirin78/hello-alpine:1.0
The push refers to repository [docker.io/erkansirin78/hello-alpine]
3e207b409db3: Mounted from library/alpine
1.0: digest: sha256:92898f96201d7346f70703f9f793f7df0054d5c32aed25b20dc31da4a189430c size: 528
```

- Go to dockerhub and see your image  




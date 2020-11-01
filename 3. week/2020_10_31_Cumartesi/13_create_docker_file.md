- Dockerfile enables us to create our own images.  
- Creating a Dockerfile  
Specify base image -> Run some commands to additional intallations -> Specify a command on container start up  

- create tourself an empty folder and inside create a file named `Dockerfile` no extention and same exact name.  

- Inside `Dockerfile`  
```
# Use an existing image as base image
FROM alpine

# Donwload and install a dependency
RUN apk add --update redis

# Tell the image what to do when it starts as container
CMD ["redis-server"]
```

Run the following command where the same directory with Dockerfile  
```
[train@localhost redis-image]$ docker image build .
Sending build context to Docker daemon  2.048kB
Step 1/3 : FROM alpine
latest: Pulling from library/alpine
df20fa9351a1: Pull complete
Digest: sha256:185518070891758909c9f839cf4ca393ee977ac378609f700f60a771a2dfe321
Status: Downloaded newer image for alpine:latest
 ---> a24bb4013296
Step 2/3 : RUN apk add --update redis
 ---> Running in 0931b9b71a1a
fetch http://dl-cdn.alpinelinux.org/alpine/v3.12/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.12/community/x86_64/APKINDEX.tar.gz
(1/1) Installing redis (5.0.9-r0)
Executing redis-5.0.9-r0.pre-install
Executing redis-5.0.9-r0.post-install
Executing busybox-1.31.1-r16.trigger
OK: 7 MiB in 15 packages
Removing intermediate container 0931b9b71a1a
 ---> a18d0c17ddb9
Step 3/3 : CMD ["redis-server"]
 ---> Running in 942ff7b4454e
Removing intermediate container 942ff7b4454e
 ---> 0423698cd215
Successfully built 0423698cd215
```

Now we can create a container from newly created image.  
```
[train@localhost redis-image]$ docker run 0423698cd215
1:C 04 Sep 2020 20:29:07.480 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
1:C 04 Sep 2020 20:29:07.480 # Redis version=5.0.9, bits=64, commit=869dcbdc, modified=0, pid=1, just started
1:C 04 Sep 2020 20:29:07.480 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
1:M 04 Sep 2020 20:29:07.485 * Running mode=standalone, port=6379.
1:M 04 Sep 2020 20:29:07.485 # WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
1:M 04 Sep 2020 20:29:07.485 # Server initialized
1:M 04 Sep 2020 20:29:07.485 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
1:M 04 Sep 2020 20:29:07.486 # WARNING you have Transparent Huge Pages (THP) support enabled in your kernel. This will create latency and memory usage issues with Redis. To fix this issue run the command 'echo never > /sys/kernel/mm/transparent_hugepage/enabled' as root, and add it to your /etc/rc.local in order to retain the setting after a reboot. Redis must be restarted after THP is disabled.
1:M 04 Sep 2020 20:29:07.487 * Ready to accept connections
```

We see redis ready.  


Most important Dockerfile instructions are **FROM RUN** and **CMD**  


Another way to create redis on CenOS7 base image  
```
# Use an existing image as base image
FROM centos:7

# Donwload and install a dependency
RUN yum install epel-release -y && \
    yum update -y && \
    yum install redis -y && \
    yum clean all


# Tell the image what to do when it starts as container
CMD ["/usr/bin/redis-server"]
```
`docker image build .`

```
[train@localhost redis-image]$ docker image build .
Sending build context to Docker daemon  2.048kB
Step 1/3 : FROM centos:7
 ---> 7e6257c9f8d8
Step 2/3 : RUN yum install epel-release -y &&     yum update -y &&     yum install redis -y &&     yum clean all
 ---> Using cache
 ---> 569b6f87a4b0
Step 3/3 : CMD ["/usr/bin/redis-server"]
 ---> Using cache
 ---> 5e9859244365
Successfully built 5e9859244365
```

- If you name Dockerfile another name than Dockerfile you have to specify `-f OtherDockerName`    
`docker image -f OtherDockerFile -t erkansirin78/myDocker:1.0 build . `  

You have to prefix your image tag. Only official images don't have prefix like redis, postgres etc.  

- Do not use your root directory, /, as the PATH as it causes the build to transfer the entire contents of your hard drive to the Docker daemon.
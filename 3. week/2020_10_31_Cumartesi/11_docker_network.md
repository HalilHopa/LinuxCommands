- Docer containers can connect them each other, or non-Docker workloads.

- Docker network system pluggable. Several drivers exist by default.

# Existing Docker Network Drivers
- Bridge  
    Default
    Bridge networks are usually used when your applications run in standalone containers that need to communicate. 

- Host  
    For standalone containers, remove network isolation between the container and the Docker host, and use the host’s networking directly.

- Macvlan  
    Macvlan networks allow you to assign a MAC address to a container, making it appear as a physical device on your network.  
	
- None  
- Overlay  
    Overlay networks connect multiple Docker daemons together and enable swarm services to communicate with each other.

- Network plugins   
    You can install and use third-party network plugins with Docker. These plugins are available from Docker Hub or from third-party vendors. 


## List network objects
`docker network ls`  

from linux terminal run `docker network inspect bridge` and  `ifconfig`  

See the gateway and host `docker0` ip is the same.  

## Create a network
`docker network create my-net`

## Why create user defined bridge network?
- Isolate networks. e.g. DB from others.
- Container on the same network can communicate by name 

- Create two container and try to ping inside alpine to nginx by container name. It won't reach.
```
[train@localhost play]$ docker run --rm --name nginx -p 8081:80 -d nginx

[train@localhost play]$ docker run --rm --name alpine alpine
```

- Create a bridge network 
```
[train@localhost play]$ docker network create my-net
afc66531ce5adb093941b8cae8596ee7104847ea8da56d4ae0741ff803053dfa

[train@localhost play]$ docker network ls
NETWORK ID          NAME                DRIVER              SCOPE
5b704d87edf2        bridge              bridge              local
d48d70437c1c        host                host                local
afc66531ce5a        my-net              bridge              local
0f35a48ac22f        none                null                local
```

- Now create with network attached and ping nginx from alpine
```
[train@localhost play]$ docker run --rm --name nginx -p 8081:80 -d --net my-net nginx
9e7613cae7d856edd1f7c90dd1d6f2f910aeb5462afe28c7ebb0bdfca8446a45

[train@localhost play]$  docker container run --rm --net my-net -it alpine /bin/sh

/ # ping nginx
PING nginx (172.18.0.2): 56 data bytes
64 bytes from 172.18.0.2: seq=0 ttl=64 time=0.136 ms
64 bytes from 172.18.0.2: seq=1 ttl=64 time=0.178 ms
64 bytes from 172.18.0.2: seq=2 ttl=64 time=0.178 ms
^C
--- nginx ping statistics ---
3 packets transmitted, 3 packets received, 0% packet loss
round-trip min/avg/max = 0.136/0.164/0.178 ms
```


- Image name/tag tells us where it is located in registiry.  

- Image address 
`docker.io/erkansirin78/merhabajava:latest`  

`docker.io` -> url this is default url  
`erkansirin78/merhabajava` -> repository  
`latest` -> tag latest is default tag  

- `latest` tag doesn't mean image is the latest version of that app.  

- Docker hub menu  
Docker, Containers, Plugins  

- If an image name doesn't contain **/** that means image is official docker image.  


# FROM 
- The FROM instruction initializes a new build stage and sets the Base Image for subsequent instructions. As such, a valid Dockerfile must start with a FROM instruction

- example:
`FROM alpine:latest`  

# RUN
- The RUN instruction will execute any commands in a new layer on top of the current image and commit the results. The resulting committed image will be used for the next step in the Dockerfile.

- use `\` to continue new line  

- example: 
```
RUN /bin/bash -c 'source $HOME/.bashrc; echo $HOME'

or
RUN ["/bin/bash", "-c", "echo hello"]
```

# CMD  
- The main purpose of a CMD is to provide defaults for an executing container.   
- There can only be **one CMD instruction in a Dockerfile.**  
- Do not confuse RUN with CMD. RUN actually runs a command and commits the result; CMD does not execute anything at build time, but specifies the intended command for the image.
- We can change cmd command while executing docker run command.

# ENV
- `ENV <key>=<value>`  

- example:
```
ENV JAVA_HOME="/usr/lib/jvm/java-1.8.0-openjdk/"
ENV SPARK_HOME="/opt/manual/spark/"
```

# ADD
- The ADD instruction copies new files, directories or remote file URLs from `<src>` and adds them to the filesystem of the image at the path `<dest>`.  

# COPY
- The COPY instruction copies new files or directories from <src> and adds them to the filesystem of the container at the path <dest>.

Multiple <src> resources may be specified but the paths of files and directories will be interpreted as relative to the source of the context of the build.

# ENTRYPOINT
- It is like CMD but we cannot change ENTRYPOINT  while executing docker run command.
- Every docker image must have at least one CMD or ENTRYPOINT. Both can be use at the same time.
- If you use both Docker will consider CMD as an argument of ENTRYPOINT  



# ADD vs. COPY (Always use COPY, unless you have to use ADD)
-------------------------
The major difference is that ADD can do more than COPY:
- ADD allows `<src>` to be a URL
- ADD can extract tar and zipped files 
- COPY suggested: using COPY where the magic of ADD is not required. Otherwise, you (since you had to look up this answer) are likely to get surprised someday when you mean to copy keep_this_archive_intact.tar.gz into your container, but instead, you spray the contents onto your filesystem.

# ENTRYPOINT vs CMD 
-------------------------------
Each image will be either CMD or ENTRYPOINT (at least one of them)
ENTRYPOINT can not be changed at runtime, but the CMD may change.
CMD becomes parameter to ENTRYPOINT if ENTRYPOINT and CMD are used together
For example, if ENTRYPOINT is ping, it will be CMD ip address. 


# EXEC AND SHELL FORM
Exec form is in json array  
`CMD["echo","Hello world"]`  

Shell form  
`CMD echo "Hello World" `  

Shell form runs the command on a shell iside docker. So it can read variables.  

Exec for runs the command as process so it cannot read variables.

If you use ENTRYPOINT and CMD together you cannot use Shell form. In this case you must use exec form.   

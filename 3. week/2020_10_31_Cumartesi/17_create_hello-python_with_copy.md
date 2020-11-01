This time we won't create hello.py file with RUN command. Instead we will COPY inside to image.  
- Create `hello.py` file on linux machine  and write inside the following 
`print("Hello I am copied to container.")`  

- Dockerfile
```
[train@localhost hello-python-image]$ cat Dockerfile_copy
FROM python:3.6

RUN mkdir /app

WORKDIR /app

COPY ./hello.py /app

CMD ["python","hello.py"]
```

- Build
```
[train@localhost hello-python-image]$ docker build -t erkansirin78/hello-python:1.0 -f Dockerf
Sending build context to Docker daemon  4.096kB
Step 1/5 : FROM python:3.6
 ---> 25bb503fe8c4
Step 2/5 : RUN mkdir /app
 ---> Using cache
 ---> 59d54e6089bb
Step 3/5 : WORKDIR /app
 ---> Using cache
 ---> c48684282f7c
Step 4/5 : COPY ./hello.py /app
 ---> 8bcab884f9d9
Step 5/5 : CMD ["python","hello.py"]
 ---> Running in 6475453f1b78
Removing intermediate container 6475453f1b78
 ---> 398de68cd819
Successfully built 398de68cd819
Successfully tagged erkansirin78/hello-python:1.0
```

- Run docker container
```
[train@localhost hello-python-image]$ docker run --rm erkansirin78/hello-python:1.0
Hello I am copied to container.
```

- COPY whole app folder to image  

- Docker file
```
[train@localhost hello-python-image]$ cat Dockerfile_copy_app_folder
FROM python:3.6

COPY ./app /app

WORKDIR /app

CMD ["python","hello.py"]
```
- Build
```
[train@localhost hello-python-image]$ docker image build -t python_app_folder -f Dockerfile_copy_app_folder  .
Sending build context to Docker daemon  6.656kB
Step 1/4 : FROM python:3.6
 ---> 25bb503fe8c4
Step 2/4 : COPY ./app /app
 ---> 02fe66f54275
Step 3/4 : WORKDIR /app
 ---> Running in a99a8d752402
Removing intermediate container a99a8d752402
 ---> 49232c2ce3bb
Step 4/4 : CMD ["python","hello.py"]
 ---> Running in 1f5fe7b83ce9
Removing intermediate container 1f5fe7b83ce9
 ---> 7fc7e1416602
Successfully built 7fc7e1416602
Successfully tagged python_app_folder:latest
```

- Run
```
[train@localhost hello-python-image]$ docker run --rm python_app_folder
Hello I am copied to container with app folder and I was written on linux machine outside the docker container.
```

- We can override CMD command
```
[train@localhost hello-python-image]$ docker run --rm python_app_folder hostname                            
ecd1b1a80330

[train@localhost hello-python-image]$ docker run --rm python_app_folder echo "Hello"
Hello
```

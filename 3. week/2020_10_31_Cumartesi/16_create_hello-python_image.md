
- Dockerfile
```
FROM python:3.6

RUN mkdir /app; touch /app/hello.py

WORKDIR /app

RUN echo "print(\"Hello I am a container from python base image\")" \
> hello.py

CMD ["python","hello.py"]
```

- Build image
```
[train@localhost hello-python-image]$ docker image build -t erkansirin78/hello-python:1.0 .
Sending build context to Docker daemon  2.048kB
Step 1/5 : FROM python:3.6
 ---> 25bb503fe8c4
Step 2/5 : RUN mkdir /app; touch /app/hello.py
 ---> Using cache
 ---> 20e6c9eab97b
Step 3/5 : WORKDIR /app
 ---> Using cache
 ---> 01248514eaed
Step 4/5 : RUN echo "print(\"Hello I am a container from python base image\")" > hello.py
 ---> Running in 7cffe721fec8
Removing intermediate container 7cffe721fec8
 ---> e54667c80a27
Step 5/5 : CMD ["python","hello.py"]
 ---> Running in 7a3b229b8360
Removing intermediate container 7a3b229b8360
 ---> 98f278d8d19d
Successfully built 98f278d8d19d
Successfully tagged erkansirin78/hello-python:1.0
```
- Run a container
```
[train@localhost hello-python-image]$ docker run --rm erkansirin78/hello-python:1.0
Hello I am a container from python base image
```

- Push image to dockerhub
```
[train@localhost hello-python-image]$ docker image push erkansirin78/hello-python:1.0
The push refers to repository [docker.io/erkansirin78/hello-python]
0acdf1582ec7: Pushed
ed2268faf1ad: Pushed
f9150e47dbd4: Mounted from library/python
8704124c1733: Mounted from library/python
b3b4d14f7bc3: Mounted from library/python
97be79495d2a: Mounted from library/python
a995c5106335: Mounted from library/python
17bdf5e22660: Mounted from library/python
d37096232ed8: Mounted from library/python
6add0d2b5482: Mounted from library/python
4ef54afed780: Mounted from library/python
1.0: digest: sha256:41a8215b1a2f6ef59fbf706e2b883a8bd75b821553da118ef4c3bd63392c5eae size: 2631
```



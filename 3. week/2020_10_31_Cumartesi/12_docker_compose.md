## What is Docker Compose?
Compose is a tool for **defining and running multi-container Docker applications**. With Compose, you use a YAML file to configure your application’s services. Then, with a single command, you create and start all the services from your configuration.   

- Compose has traditionally been focused on **development and testing** workflows. You can easily create and run isolated development/test/POC environment. Bu can be used single-host deployments in production.

- You define your design in a file named `docker-compose.yml` or `docker-compose.yaml`    
```
version: '2.0'
services:
  web:
    build: .
    ports:
    - "5000:5000"
    volumes:
    - .:/code
    - logvolume01:/var/log
    links:
    - redis
  redis:
    image: redis
volumes:
  logvolume01: {}
  ```

  - Then you run `docker-compose up` command. That's it.

  - You have to install docker-compose seperately from docker-ce.  
  https://docs.docker.com/compose/install/  But in your machine it is already installed.

## Example 
In this example you will create a Flask web application that maintains a hit counter in Redis. It is simple and just counts and shows how many visitors are welcomed so far.
- Create a project directory  and navigate in it.
`[train@localhost play]$ mkdir docker-compose-example`  


- Create `requirements.txt` in your `docker-compose-example` directory and paste following python packeges 
```
flask
redis
```

- Create a python file named `app.py` and paste in the following codes.  
```
import time

import redis
from flask import Flask

app = Flask(__name__)
cache = redis.Redis(host='redis', port=6379)


def get_hit_count():
    retries = 5
    while True:
        try:
            return cache.incr('hits')
        except redis.exceptions.ConnectionError as exc:
            if retries == 0:
                raise exc
            retries -= 1
            time.sleep(0.5)


@app.route('/')
def hello():
    count = get_hit_count()
    return 'Hello World! I have been seen {} times.\n'.format(count)
```

- Create a `Dockerfile` and paste:  
```
FROM centos/python-36-centos7
WORKDIR /code
ENV FLASK_APP app.py
ENV FLASK_RUN_HOST 0.0.0.0
COPY requirements.txt requirements.txt
RUN pip install --upgrade pip && pip install -r requirements.txt
EXPOSE 5000
COPY . .
CMD ["flask", "run"]
```

- Create a docker-compose.yml file and paste in it:
```
version: '3'
services:
  web:
    build: .
    ports:
      - "5000:5000"
  redis:
    image: "redis:alpine"
```

- run docker-compose:  
`docker-compose up`

- Observe the results  
When you see **Ready to accept connections** open browser and type http://localhost:5000/ You will see **Hello World! I have been seen X times**. 

- Close app and docker-compose   
Ctrl+C wil stop containers.
```
Gracefully stopping... (press Ctrl+C again to force)
Stopping docker-compose-example_web_1   ... done
Stopping docker-compose-example_redis_1 ... done
```
- to remove containers  (Always run this command where the docker-compose.yaml file is)
```
[train@localhost docker-compose-example]$ docker-compose down
Removing docker-compose-example_web_1   ... done
Removing docker-compose-example_redis_1 ... done
Removing network docker-compose-example_default
```

- How to modify your code? 
- modify docker-compose.yml file by adding volume    
```
version: '3'
services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumnes:
      - .:/code
    environment:
      FLASK_ENV: development
  redis:
    image: "redis:alpine"
```

Start docker-compose again.  See the page http://localhost:5000/  
Open app.py file and modify it like below   
` return ' <h1>Hello, now you can modify me without a stop</h1> I have been seen {} times\n'.format(count)`  
See the changes on browser. We don't have to restart container. It is a good way of volumes.  

- Just a reminder: Like many other configuration files yaml files are inclined to get format error. Best way to see and fix it copy your yaml codes and paste http://www.yamllint.com/ see errors and fix it.



























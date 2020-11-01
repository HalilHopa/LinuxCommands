## remove container
Before remove you have to stop container or force to remove 

`docker rm <container_id>`  
`docker rm <container name>`

## prune
Removes all the containers.  
```
[train@localhost miuul]$ docker system prune
WARNING! This will remove:
  - all stopped containers
  - all networks not used by at least one container
  - all dangling images
  - all dangling build cache

Are you sure you want to continue? [y/N]


Deleted Containers:
6733f4794fde032099ccf4b5ae937502220b57a5fbc3f46d712ba69968f7de17
98389e53fe09a675f9795d6ccf63b685b89383f1e660de68789c6508c1eeed97
34d2e4d9cf4ecbc29a61b5a442061a4c169795ddafa79cd5cff72f5c53ed5f03
```


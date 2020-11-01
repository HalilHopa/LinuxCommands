
`[train@localhost play]$ docker run --rm nginx`  
open browser and enter http://localhost/ you can't see anything. nginx listens 80 port inside the container but we sent request to localhost's 80 PORT.  

Stop and run again.  
```
[train@localhost play]$ docker run --rm -p 8081:80 -d nginx
bc7ba15c21b238d7d9f5ac2a7ebfb69cb61fa8e485bafb4b5549db1d2bc1f353
```

Enter http://localhost:8081/ in browser and see nginx wellcome page.  

1. Ping Google 7 times and save the results in `google_ping_file`

Answer:
``` 
(venvspark) [train@localhost kurs]$ ping -c 7 google.com > google_ping_file 
(venvspark) [train@localhost kurs]$ cat google_ping_file 
PING google.com (172.217.169.110) 56(84) bytes of data.
64 bytes from sof02s31-in-f14.1e100.net (172.217.169.110): icmp_seq=1 ttl=115 time=60.3 ms
64 bytes from sof02s31-in-f14.1e100.net (172.217.169.110): icmp_seq=2 ttl=115 time=59.7 ms
64 bytes from sof02s31-in-f14.1e100.net (172.217.169.110): icmp_seq=3 ttl=115 time=59.0 ms
64 bytes from sof02s31-in-f14.1e100.net (172.217.169.110): icmp_seq=4 ttl=115 time=59.2 ms
64 bytes from sof02s31-in-f14.1e100.net (172.217.169.110): icmp_seq=5 ttl=115 time=58.2 ms
64 bytes from sof02s31-in-f14.1e100.net (172.217.169.110): icmp_seq=6 ttl=115 time=60.4 ms
64 bytes from sof02s31-in-f14.1e100.net (172.217.169.110): icmp_seq=7 ttl=115 time=60.0 ms

--- google.com ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6036ms
rtt min/avg/max/mdev = 58.242/59.590/60.438/0.744 ms
```


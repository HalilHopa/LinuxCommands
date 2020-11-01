
1. Loop content of file
while_loop.sh  
```
#! /bin/bash

while read DNS; do
    ping -c 3 $DNS
done < dns.txt
```

dns.txt  
```
8.8.8.8
8.8.4.4
```
Run `while_loop.sh`  script (this will ping two google dns server written in `dns.txt` file)
```
[train@localhost play]$ ./while_loop.sh
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=118 time=30.1 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=118 time=30.9 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=118 time=30.1 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 30.103/30.410/30.986/0.407 ms
PING 8.8.4.4 (8.8.4.4) 56(84) bytes of data.
64 bytes from 8.8.4.4: icmp_seq=1 ttl=118 time=25.1 ms
64 bytes from 8.8.4.4: icmp_seq=2 ttl=118 time=24.3 ms
64 bytes from 8.8.4.4: icmp_seq=3 ttl=118 time=24.3 ms

--- 8.8.4.4 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2005ms
```

2. Simply loop and echo a file  
```
while read p; do
  echo "$p"
done < peptides.txt
```
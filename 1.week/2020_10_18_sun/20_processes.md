A **process** is the instance of a computer program that is being executed by one or many threads.

How to see processes?  
- ps - report a snapshot of the current processes.  
- top -
- htop - Advenced version of top  

**PID:** Process ID makes distinguishable processes.  
How to learn PID of a procees?  
`pidof`

**Types of Processes:**  
- Foreground (interactive)
- Background (non-interactive)

**Stopping proces**  
- with pid
`kill <pid_of_process>`  
- with name
`pkill firefox` or `kilall firefox`  

**top and htop**  
`top` or `htop` let us to monitor processes  

In Linux a **service** is just another name for a **daemon**, which is a client / server application that runs in the background. A service continuously listens for incoming requests and sends a response based on the request given. A process is simply an application or a script which can be running in the foreground or the background.


**list all services**   and grep from it
```
[train@localhost play]$ sudo systemctl | grep postgresql
postgresql-10.service loaded active running   PostgreSQL 10 database server
```


**check status of a service**
`sudo systemctl ststus <service_name>`   
```
[train@localhost play]$ sudo systemctl status postgresql-10
● postgresql-10.service - PostgreSQL 10 database server
   Loaded: loaded (/usr/lib/systemd/system/postgresql-10.service; enabled; vendor preset: disabled)
   Active: active (running) since Tue 2020-09-01 13:10:03 +03; 1 day 20h ago
     Docs: https://www.postgresql.org/docs/10/static/
  Process: 1144 ExecStartPre=/usr/pgsql-10/bin/postgresql-10-check-db-dir ${PGDATA} (code=exited, status=0/SUCCESS)
 Main PID: 1169 (postmaster)
    Tasks: 8
   CGroup: /system.slice/postgresql-10.service
           ├─1169 /usr/pgsql-10/bin/postmaster -D /var/lib/pgsql/10/data/
           ├─1222 postgres: logger process
           ├─1231 postgres: checkpointer process
           ├─1232 postgres: writer process
           ├─1233 postgres: wal writer process
           ├─1234 postgres: autovacuum launcher process
           ├─1235 postgres: stats collector process
           └─1236 postgres: bgworker: logical replication launcher

Sep 01 13:10:02 localhost.localdomain systemd[1]: Starting PostgreSQL 10 database server...
Sep 01 13:10:02 localhost.localdomain postmaster[1169]: 2020-09-01 13:10:02.642 +03 [1169] LOG:  listen...432
Sep 01 13:10:02 localhost.localdomain postmaster[1169]: 2020-09-01 13:10:02.642 +03 [1169] LOG:  listen...432
Sep 01 13:10:02 localhost.localdomain postmaster[1169]: 2020-09-01 13:10:02.646 +03 [1169] LOG:  listen...32"
Sep 01 13:10:02 localhost.localdomain postmaster[1169]: 2020-09-01 13:10:02.664 +03 [1169] LOG:  listen...32"
Sep 01 13:10:02 localhost.localdomain postmaster[1169]: 2020-09-01 13:10:02.930 +03 [1169] LOG:  redire...ess
Sep 01 13:10:02 localhost.localdomain postmaster[1169]: 2020-09-01 13:10:02.930 +03 [1169] HINT:  Futur...g".
Sep 01 13:10:03 localhost.localdomain systemd[1]: Started PostgreSQL 10 database server.
Hint: Some lines were ellipsized, use -l to show in full.
```

Start process, push it background call back foreground and stop it.   
To push background Ctrl+z  
Callback foreground fg index or name  
Stop process Ctrl+C  
```   
[train@localhost play]$ firefox
Running without a11y support!
^Z
[1]+  Stopped                 firefox
[train@localhost play]$ jobs
[1]+  Stopped                 firefox
[train@localhost play]$ sudo kill firefox
[sudo] password for train:
[train@localhost play]$ jobs
[1]+  Stopped                 firefox
[train@localhost play]$ fg 1
firefox
^C
[train@localhost play]$ jobs
```
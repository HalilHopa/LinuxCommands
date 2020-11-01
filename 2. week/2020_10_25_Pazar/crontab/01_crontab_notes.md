crontab - Schedules commands execution at Specified time or time interval.  

https://crontab.guru/
```
* * * * * At every minutes

5 * * * * At every hours past 5 mins  

* 5 * * * At every minute past hour 5. 05:01, 05:02, ... 05:59

*/5 * * * * At every 5th minute.  

0 */6 * * *  At minute 0 past every 6th hour.
```
- There is main crontab file and every user has its crontab.  
```
[ansadmin@kmaster1 my_ans_dev]$ cat /etc/crontab
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root

# For details see man 4 crontabs

# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name  command to be executed
```
- List crontab jobs
```
[train@localhost ~]$ crontab -l

```
\# is comment line  

- Edit crontab file `crontab -e`  

- create a simple script and schedule it with crontab  
```
#!/bin/bash
now=$(date +%y%m%d%H%M%S)
echo "a new file $now" > /tmp/${now}_orange_file
```

```
[train@localhost cronjobs]$ crontab -e
crontab: installing new crontab
[train@localhost cronjobs]$ crontab -l
*/1 * * * * /home/train/cronjobs/make_a_file.sh >> /home/train/cronjobs/make_a_file.log 2>&1
```
Now it is working. We expect make_a_file.sh should create new file in /tmp every minutes.

- Check /tmp folder  
```
[train@localhost cronjobs]$ ll /tmp | grep orange_file
-rw-r--r--.   1 train   train        24 Oct 18 23:33 201018233301_orange_file
-rw-r--r--.   1 train   train        24 Oct 18 23:34 201018233401_orange_file
-rw-r--r--.   1 train   train        24 Oct 18 23:35 201018233501_orange_file
-rw-r--r--.   1 train   train        24 Oct 18 23:36 201018233601_orange_file
```

- To pause job comment out of it.  
```
[train@localhost cronjobs]$ crontab -l
#*/1 * * * * /home/train/cronjobs/make_a_file.sh >> /home/train/cronjobs/make_a_file.log 2>&1
```
`2>&1` -> when you use 2>&1 you are basically saying **Redirect the stderr to the same place we are redirecting the stdout.** And that’s why we can do something like this to redirect both stdout and stderr to the same place.


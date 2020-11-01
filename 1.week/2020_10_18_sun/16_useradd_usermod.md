1. Create new user (useradd)  
`useradd` requires sudo privilege


2. Mostly used args with useradd  
- -s user shell e.g. /bin/bash 
- -d specify different home directory (default /home/<username> 
- -m create a home directory while creating the user 
- -g add user a group while creating the it

3. create user with default home directory
```
[train@localhost play]$ sudo useradd -m user1
[sudo] password for train:


[train@localhost play]$ ls -l /home
total 4
drwx------. 37 train train 4096 Sep  2 13:02 train
drwx------.  3 user1 user1   78 Sep  2 13:54 user1
```

4. specify a password for the user1  
`[train@localhost play]$ sudo passwd user1`


5. add a user existing group  
`[train@localhost play]$ sudo usermod -aG docker user1`


6. Where is the users?  
```
[train@localhost play]$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
..
..
..
```

7. Does a user exist?
```
[train@localhost play]$ cat /etc/passwd | grep train
train:x:1000:1000:train:/home/train:/bin/bash
```
Second way   
```
[train@localhost play]$ id user1
uid=1001(user1) gid=980(docker) groups=980(docker)
```
8. Where is the groups?
```
[train@localhost play]$ cat /etc/group
root:x:0:
bin:x:1:
daemon:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
..
..
```

9. Does a group exist?
```
[train@localhost play]$ cat /etc/group | grep train
wheel:x:10:train
train:x:1000:train
docker:x:980:train
```

10. Which users a groups include?
```
[train@localhost play]$ cat /etc/group | grep docker
docker:x:980:train,user1
```

11. List user's group
```
[train@localhost play]$ cat /etc/group | grep train
wheel:x:10:train
train:x:1000:train
docker:x:980:train,user1
```
Or with command
```
[train@localhost play]$ groups
train wheel docker
```

12. Assign a password a user
```
[train@localhost play]$ sudo passwd user1
Changing password for user user1.
New password:
Retype new password:
passwd: all authentication tokens updated successfully
```

13. userdel
 -r, --remove                  remove home directory and mail spool
```
[train@localhost play]$ sudo useradd -m -g docker user2
[sudo] password for train:

[train@localhost play]$ id user2
uid=1002(user2) gid=980(docker) groups=980(docker)

[train@localhost play]$ ll /home
total 4
drwx------. 37 train train  4096 Sep  2 13:02 train
drwx------.  3 user1 docker   78 Sep  2 13:54 user1
drwx------.  3 user2 docker   78 Sep  2 15:55 user2

[train@localhost play]$ sudo userdel -r user2

[train@localhost play]$ ll /home
total 4
drwx------. 37 train train  4096 Sep  2 13:02 train
drwx------.  3 user1 docker   78 Sep  2 13:54 user1

[train@localhost play]$ id user2
id: user2: no such user
```






























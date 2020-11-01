```
[train@localhost play]$ nano runHello.sh
put inside

echo "Hello world"
cwd=$(pwd)
echo "Current directory: $cwd"


[train@localhost play]$ ll
-rw-rw-r--. 1 train train       61 Sep  2 16:08 runHello.sh
```

1. make a file executable
```
[train@localhost play]$ ./runHello.sh
-bash: ./runHello.sh: Permission denied


[train@localhost play]$ sudo chmod +x runHello.sh
[sudo] password for train:
[train@localhost play]$ ./runHello.sh
Hello world
Current directory: /home/train/production_level_ds/linux_basic/play
```

2. use symbols to modify access rights 
``` 
u	user owner  
g	group owner  
o others  
a all  

+	add  
=	specify the exact permission  
-	remove  
```

3. Give user execute right
```
 [train@localhost play]$ ll
total 1768
-rw-rw-r--. 1 user1 docker    2074 Sep  2 11:04 Advertising.csv.gz
-rw-rw-r--. 1 train train       52 Sep  2 10:25 mahmutfile


[train@localhost play]$ sudo chmod u+x mahmutfile

[train@localhost play]$ ll
total 1768
-rw-rw-r--. 1 user1 docker    2074 Sep  2 11:04 Advertising.csv.gz
-rwxrw-r--. 1 train train       52 Sep  2 10:25 mahmutfile
```

4. give group execute right
```
[train@localhost play]$ sudo chmod g+x mahmutfile
[train@localhost play]$ ll
total 1768
-rw-rw-r--. 1 user1 docker    2074 Sep  2 11:04 Advertising.csv.gz
-rwxrwxr--. 1 train train       52 Sep  2 10:25 mahmutfile
```

5. remove read rights from others
```
[train@localhost play]$ sudo chmod a-r mahmutfile
[train@localhost play]$ ll
total 1768
-rw-rw-r--. 1 user1 docker    2074 Sep  2 11:04 Advertising.csv.gz
--wx-wx---. 1 train train       52 Sep  2 10:25 mahmutfile
```

6. Modify all three right at once
```
Remove all rights from user 
[train@localhost play]$ sudo chmod u=--- mahmutfile
[train@localhost play]$ ll
total 1768
-rw-rw-r--. 1 user1 docker    2074 Sep  2 11:04 Advertising.csv.gz
-----wx---. 1 train train       52 Sep  2 10:25 mahmutfile
```

7. add read and write to user
```
[train@localhost play]$ sudo chmod u=rw- mahmutfile
[train@localhost play]$ ll
total 1768
-rw-rw-r--. 1 user1 docker    2074 Sep  2 11:04 Advertising.csv.gz
-rw--wx---. 1 train train       52 Sep  2 10:25 mahmutfile
```

8. Using octals (Follows binary logic)
```
  octal  symbol equivalent 
0 (000)		---
1 (001)		--x
2 (010)		-w-
3 (011)		-wx
4 (100)		r--
5 (101)		r-x
6 (110)		rw- 
7 (111)		rwx
```


9. Remove all rights with octal notation
```
[train@localhost play]$ sudo chmod 000 mahmutfile
[sudo] password for train:
[train@localhost play]$ ll
total 1768
-rw-rw-r--. 1 user1 docker    2074 Sep  2 11:04 Advertising.csv.gz
----------. 1 train train       52 Sep  2 10:25 mahmutfile
```
10. Give user full right
```
train@localhost play]$ sudo chmod 700 mahmutfile
[train@localhost play]$ ll
total 1768
-rw-rw-r--. 1 user1 docker    2074 Sep  2 11:04 Advertising.csv.gz
-rwx------. 1 train train       52 Sep  2 10:25 mahmutfile
```
11. Give user and group read and write
```
[train@localhost play]$ sudo chmod 660 mahmutfile
[train@localhost play]$ ll
total 1768
-rw-rw-r--. 1 user1 docker    2074 Sep  2 11:04 Advertising.csv.gz
-rw-rw----. 1 train train       52 Sep  2 10:25 mahmutfile
```
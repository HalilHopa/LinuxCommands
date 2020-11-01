1. `touch` create file  
```
[train@localhost play]$ touch my_file
[train@localhost play]$ ls -l
total 0
-rw-rw-r--. 1 train train 0 Sep  1 16:41 my_file
```


2. `mkdir` create new folder  

3. `rm` delete file/folder  
```
[train@localhost play]$ rm my_file
[train@localhost play]$ ls -l
total 0
```
popular parameters of rm   
-f force   
-r recursive  
```
[train@localhost play]$ rm myfolder/
rm: cannot remove �myfolder/�: Is a directory

[train@localhost play]$ rm -r myfolder
[train@localhost play]$ ll
```
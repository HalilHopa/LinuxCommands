```
-e exists
-f exists and regular file   
-s is file empty  
-d exists and directory
-r is readable   
-w is writable   
-x is executeable  
file1 -nt file2 file1 is newer than file2.
file1 -ot file2 file1 is older than file2.

```

## Example-1: Check file_operators_test.sh is executable, if not make it executable.  
```
[train@localhost play]$ ll
-rwxrwxr-x. 1 train train 126 Sep  3 14:09 file_operators.sh
-rw-rw-r--. 1 train train   0 Sep  3 14:02 file_operators_test.sh
```

As you see above file_operators_test.sh doesn't have execute permission. Let's check and give it x right.  

file_operators.sh  
```
#! /bin/bash

file=$1
if [ -x $file -a -e $file ] ; then
   echo "$file is already executable"
else
   chmod +x $file
   echo "chmod +x $file is successfull."
fi
```
Run script  
```
[train@localhost play]$ ./file_operators.sh file_operators_test.sh
chmod +x file_operators_test.sh is successfull.
```
Run again  
```
[train@localhost play]$ ./file_operators.sh file_operators_test.sh
file_operators_test.sh is already executable
```
As we changed script says file is already executable.  
```
[train@localhost play]$ ll
-rwxrwxr-x. 1 train train 126 Sep  3 14:09 file_operators.sh
-rwxrwxr-x. 1 train train   0 Sep  3 14:02 file_operators_test.sh
```

## Example-2: Write the script creates xxxx.sh (given as argument), run xxxx.sh script and xxxx.sh tell us it's name like My name is test.sh


file_operators2.sh  
```
#! /bin/bash

file=$1
if [ -e $file ] ; then
   echo "$file exists"
   echo "echo \"My name is \$0.\"" > $file
   chmod +x $file
   bash $file
else
    echo "$file doesn't exist."
    echo "echo  \"My name is \$0.\"" > $file
    chmod +x $file
    bash $file
fi
```
Run script  
```
[train@localhost play]$ ./file_operators2.sh test.sh
test.sh doesn't exist.
Myname is test.sh.
[train@localhost play]$ ./file_operators2.sh test.sh
test.sh exists
Myname is test.sh.
[train@localhost play]$ ll
-rwxrwxr-x. 1 train train 262 Sep  3 14:46 file_operators2.sh
-rwxrwxr-x. 1 train train  21 Sep  3 14:47 test.sh
```
First time we run script creates the test.sh file the
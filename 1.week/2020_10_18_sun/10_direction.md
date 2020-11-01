1. `>` override the file   
```
[train@localhost play]$ cat myfile1
inside myfile1
inside myfile1
[train@localhost play]$ echo "this will override" > myfile1
[train@localhost play]$ cat myfile1
this will override
```

2. `>>` add new line to file   
```
[train@localhost play]$ echo "this will add new line" >> myfile1
[train@localhost play]$ cat myfile1
this will override
this will add new line
```

3. `>` can behave like touch   
```
[train@localhost play]$ echo "this will create new file" > newfile
[train@localhost play]$ ll
total 12
-rw-rw-r--. 1 train train 42 Sep  2 10:21 myfile1
-rw-rw-r--. 1 train train 41 Sep  1 18:38 myfile2
drwxrwxr-x. 2 train train 58 Sep  1 19:05 myfolder
-rw-rw-r--. 1 train train 26 Sep  2 10:23 newfile
[train@localhost play]$ cat newfile
this will create new file
```

4. `&>` will direct errors as well  
```
[train@localhost play]$ ls -l mahmut &> mahmutfile
[train@localhost play]$ cat mahmutfile
ls: cannot access mahmut: No such file or directory
```

5. cat and EOF usage. We can create and write a file easily. 
```
cat <<EOF > filename
line1
line2
line3
EOF 
```

We can append lines also 
```
[ansadmin@kmaster1 my_ans_dev]$ cat <<EOF >> filename
This line will be appended
EOF

[ansadmin@kmaster1 my_ans_dev]$ cat print.sh
line1
line2
line3
This line will be appended
```

6. < file or input  
```
[train@localhost play]$ cat < hello_netcat.txt
Hello netcat
whats up
```
direction.sh  
```
#! /bin/bash

ls -l mahmut
ls -l /etc | head -n 10
```
7. `2>` directs just errors  
```
[train@localhost play]$ ./direction.sh 2> myFile
total 1444
drwxr-xr-x.  3 root root      101 Jul 21 00:01 abrt
-rw-r--r--.  1 root root       16 Jul 21 00:17 adjtime
-rw-r--r--.  1 root root     1529 Apr  1  2020 aliases
-rw-r--r--.  1 root root    12288 Jul 21 02:53 aliases.db
drwxr-xr-x.  3 root root       65 Jul 21 00:06 alsa
drwxr-xr-x.  2 root root     8192 Aug  8 10:16 alternatives
-rw-------.  1 root root      541 Aug  9  2019 anacrontab
-rw-r--r--.  1 root root       55 Aug  8  2019 asound.conf
-rw-r--r--.  1 root root        1 Oct 30  2018 at.deny

[train@localhost play]$ cat myFile
ls: cannot access mahmut: No such file or directory
```

8. `&>` directs both output and errors
```
[train@localhost linux]$ cat şakir
ls: cannot access mahmut: No such file or directory
total 1444
drwxr-xr-x.  3 root root      101 Jul 21 00:01 abrt
-rw-r--r--.  1 root root       16 Jul 21 00:17 adjtime
-rw-r--r--.  1 root root     1529 Apr  1  2020 aliases
-rw-r--r--.  1 root root    12288 Jul 21 02:53 aliases.db
drwxr-xr-x.  3 root root       65 Jul 21 00:06 alsa
drwxr-xr-x.  2 root root     8192 Aug  8 10:16 alternatives
-rw-------.  1 root root      541 Aug  9  2019 anacrontab
-rw-r--r--.  1 root root       55 Aug  8  2019 asound.conf
-rw-r--r--.  1 root root        1 Oct 30  2018 at.deny
```

9. `&>>` adds output and error

10.  `command > şakir 2> hatalı-şakir`  girects output to şakir, errors to hatalı-şakir
```
[train@localhost linux]$ ./direction.sh > şakir 2> hatalı-şakir
[train@localhost linux]$ cat şakir
total 1444
drwxr-xr-x.  3 root root      101 Jul 21 00:01 abrt
-rw-r--r--.  1 root root       16 Jul 21 00:17 adjtime
-rw-r--r--.  1 root root     1529 Apr  1  2020 aliases
-rw-r--r--.  1 root root    12288 Jul 21 02:53 aliases.db
drwxr-xr-x.  3 root root       65 Jul 21 00:06 alsa
drwxr-xr-x.  2 root root     8192 Aug  8 10:16 alternatives
-rw-------.  1 root root      541 Aug  9  2019 anacrontab
-rw-r--r--.  1 root root       55 Aug  8  2019 asound.conf
-rw-r--r--.  1 root root        1 Oct 30  2018 at.deny
[train@localhost linux]$ cat hatalı-şakir
ls: cannot access mahmut: No such file or directory
./direction.sh: line 4: 2/0 : division by 0 (error token is "0 ")
```
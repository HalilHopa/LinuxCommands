Data compression is the process of removing redundancy from data.

**Logic of compression **  
```
[train@localhost linux]$ cat compress-simulation.sh
#!/bin/bash

for i in {1..20};
  do
    echo "$i - These lines are male"
  done

for j in {21..40};
  do
    echo "$j - These lines are female"
  done
```
`[train@localhost linux]$ ./compress-simulation.sh`  

Discuss the output.

1. `gzip` **compresses** and **overwrites** the normal_file  
`gzip <file>`

```
[train@localhost linux]$ gzip -v /home/train/datasets/Advertising.csv
/home/train/datasets/Advertising.csv:    55.2% -- replaced with /home/train/datasets/Advertising.csv.gz

[train@localhost play]$ ll /home/train/datasets
total 352
-rw-rw-r--. 1 train train   2074 Jul 21 18:58 Advertising.csv.gz
-rw-rw-r--. 1 train train   4611 Sep  1 16:13 iris.csv
-rw-rw-r--. 1 train train  15802 Sep  1 16:13 iris.json
-rw-rw-r--. 1 train train 325145 Sep  1 16:14 kuruyemisler.txt
drwxrwxr-x. 2 train train    133 Jul 23 22:06 retail_db
-rw-rw-r--. 1 train train    148 Sep  1 16:16 simple_text.txt
```

2. `gunzip` uncompresses `.gz` extension file
```
[train@localhost play]$ gunzip ~/datasets/Advertising.csv.gz

[train@localhost play]$ ll ~/datasets/
total 356
-rw-rw-r--. 1 train train   4556 Jul 21 18:58 Advertising.csv
-rw-rw-r--. 1 train train   4611 Sep  1 16:13 iris.csv
-rw-rw-r--. 1 train train  15802 Sep  1 16:13 iris.json
-rw-rw-r--. 1 train train 325145 Sep  1 16:14 kuruyemisler.txt
drwxrwxr-x. 2 train train    133 Jul 23 22:06 retail_db
-rw-rw-r--. 1 train train    148 Sep  1 16:16 simple_text.txt
```

3. `gzip -c` prevent overwriting
```
[train@localhost play]$ gzip -c /home/train/datasets/Advertising.csv > Advertising.csv.gz

[train@localhost play]$ ll
total 20
-rw-rw-r--. 1 train train 2074 Sep  2 11:04 Advertising.csv.gz
-rw-rw-r--. 1 train train   52 Sep  2 10:25 mahmutfile
-rw-rw-r--. 1 train train   42 Sep  2 10:21 myfile1
-rw-rw-r--. 1 train train   41 Sep  1 18:38 myfile2
drwxrwxr-x. 2 train train   58 Sep  1 19:05 myfolder
-rw-rw-r--. 1 train train   26 Sep  2 10:23 newfile
```
```
[train@localhost play]$ ll ~/datasets/
total 356
-rw-rw-r--. 1 train train   4556 Jul 21 18:58 Advertising.csv
-rw-rw-r--. 1 train train   4611 Sep  1 16:13 iris.csv
-rw-rw-r--. 1 train train  15802 Sep  1 16:13 iris.json
-rw-rw-r--. 1 train train 325145 Sep  1 16:14 kuruyemisler.txt
drwxrwxr-x. 2 train train    133 Jul 23 22:06 retail_db
-rw-rw-r--. 1 train train    148 Sep  1 16:16 simple_text.txt
 ```

We compressed and moved .gz file to our current directory.  
 
4. `gzip -r` recursively compress used all files in a folder
 ```
[train@localhost play]$ ll /home/train/datasets/retail_db/
total 9328
-rw-rw-r--. 1 train train    1074 Jul 23 22:05 categories.csv
-rw-rw-r--. 1 train train  953847 Jul 23 22:06 customers.csv
-rw-rw-r--. 1 train train      88 Jul 23 22:06 departments.csv
-rw-rw-r--. 1 train train 5408988 Jul 23 22:06 order_items.csv
-rw-rw-r--. 1 train train 2999990 Jul 23 22:06 orders.csv
-rw-rw-r--. 1 train train  174240 Jul 23 22:06 products.csv
```
```
[train@localhost play]$ gzip -r /home/train/datasets/retail_db/
[train@localhost play]$ ll /home/train/datasets/retail_db/
total 1756
-rw-rw-r--. 1 train train     612 Jul 23 22:05 categories.csv.gz
-rw-rw-r--. 1 train train  250493 Jul 23 22:06 customers.csv.gz
-rw-rw-r--. 1 train train     115 Jul 23 22:06 departments.csv.gz
-rw-rw-r--. 1 train train 1031577 Jul 23 22:06 order_items.csv.gz
-rw-rw-r--. 1 train train  471126 Jul 23 22:06 orders.csv.gz
-rw-rw-r--. 1 train train   28136 Jul 23 22:06 products.csv.gz
```


5. `gunzip -r` recursively uncompress files 
```
[train@localhost play]$ gunzip -r ~/datasets/retail_db/
[train@localhost play]$ ll /home/train/datasets/retail_db/
total 9328
-rw-rw-r--. 1 train train    1074 Jul 23 22:05 categories.csv
-rw-rw-r--. 1 train train  953847 Jul 23 22:06 customers.csv
-rw-rw-r--. 1 train train      88 Jul 23 22:06 departments.csv
-rw-rw-r--. 1 train train 5408988 Jul 23 22:06 order_items.csv
-rw-rw-r--. 1 train train 2999990 Jul 23 22:06 orders.csv
-rw-rw-r--. 1 train train  174240 Jul 23 22:06 products.csv
```



















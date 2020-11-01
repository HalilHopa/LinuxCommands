[train@localhost big_data]$ cd hadoop-hdfs/play/

[train@localhost play]$ start-all.sh

1. ls lists 
```
[train@localhost play]$ hdfs dfs -ls /
Found 2 items
drwxrwxr-x   - train supergroup          0 2020-08-26 06:22 /tmp
drwxr-xr-x   - train supergroup          0 2020-08-22 08:40 /user
```

`/user` is home directory of users like `/home` in linux. In this case our hdfs home is `/user/train`

2. mkdir 
`[train@localhost play]$ hdfs dfs -mkdir /user/train/play-hdfs-commands`  

Now sort and see newly created folder.
```
[train@localhost play]$ hdfs dfs -ls -t /user/train
Found 10 items
drwxr-xr-x   - train supergroup          0 2020-09-15 04:49 /user/train/play-hdfs-commands
drwxr-xr-x   - train supergroup          0 2020-08-26 18:25 /user/train/.sparkStaging
drwxr-xr-x   - train supergroup          0 2020-08-26 18:14 /user/train/write_to_kafka
drwxr-xr-x   - train supergroup          0 2020-08-26 14:56 /user/train/read_from_kafka
drwxr-xr-x   - train supergroup          0 2020-08-26 11:31 /user/train/exactly_once_guarantee
drwxr-xr-x   - train supergroup          0 2020-08-25 20:47 /user/train/wordCountCheckpoint
drwxr-xr-x   - train supergroup          0 2020-08-22 08:15 /user/train/datasets
drwxr-xr-x   - train supergroup          0 2020-08-21 11:53 /user/train/output_data
drwxr-xr-x   - train supergroup          0 2020-07-23 22:07 /user/train/myHDFSFolder
-rw-r--r--   1 train supergroup       4556 2020-07-23 21:53 /user/train/copied.csv
```

2. put  
put copies files and folders from lokal to hdfs.  

3. mv  
move hdfs files/folder to another directory.

4. cp  
copies hdfs files/folders to another directory.

5. chown
changes ownership of file/folder.

6. chmod
changes access rights of file/folder.

7. get
downloads a file/folder form hdfs to local.

8. du
shows size of folder.

9. rm
deletes file/folder from hdfs.  
For folders `-r`  
For skipping trash `-skipTrash`  

10. head, tail, cat to read files.

11. hdfs environment variables  
```
[train@localhost play]$ hdfs envvars

JAVA_HOME='/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.262.b10-0.el7_8.x86_64/jre/'
HADOOP_HDFS_HOME='/opt/manual/hadoop/'
HDFS_DIR='share/hadoop/hdfs'
HDFS_LIB_JARS_DIR='share/hadoop/hdfs/lib'
HADOOP_CONF_DIR='/opt/manual/hadoop/etc/hadoop'
HADOOP_TOOLS_HOME='/opt/manual/hadoop/'
HADOOP_TOOLS_DIR='share/hadoop/tools'
HADOOP_TOOLS_LIB_JARS_DIR='share/hadoop/tools/lib'
```

12. health check  
```
[train@localhost play]$ hdfs fsck /user/train
Connecting to namenode via http://localhost:9870/fsck?ugi=train&path=%2Fuser%2Ftrain
FSCK started by train (auth:SIMPLE) from /127.0.0.1 for path /user/train at Tue Sep 15 05:19:32 TRT 2020

Status: HEALTHY
 Number of data-nodes:  1
 Number of racks:               1
 Total dirs:                    249
 Total symlinks:                0

Replicated Blocks:
 Total size:    1001184061 B
 Total files:   4223
 Total blocks (validated):      4222 (avg. block size 237135 B)
 Minimally replicated blocks:   4222 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    1
 Average block replication:     1.0
 Missing blocks:                0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)

Erasure Coded Block Groups:
 Total size:    0 B
 Total files:   0
 Total block groups (validated):        0
 Minimally erasure-coded block groups:  0
 Over-erasure-coded block groups:       0
 Under-erasure-coded block groups:      0
 Unsatisfactory placement block groups: 0
 Average block group size:      0.0
 Missing block groups:          0
 Corrupt block groups:          0
 Missing internal blocks:       0
FSCK ended at Tue Sep 15 05:19:32 TRT 2020 in 281 milliseconds


The filesystem under path '/user/train' is HEALTHY
```

13. 
1. Startcluster `start-all.sh`  

2. In terminal-1 Start spark-shell in yarn mode  
`[train@localhost play]$ pyspark --master yarn --executor-memory 1g --num-executors 1 --total-executor-cores 1`  

You should see the following output:  
```

Python 3.6.8 (default, Apr  2 2020, 13:34:55)
[GCC 4.8.5 20150623 (Red Hat 4.8.5-39)] on linux
Type "help", "copyright", "credits" or "license" for more information.
Setting default log level to "WARN".
To adjust logging level use sc.setLogLevel(newLevel). For SparkR, use setLogLevel(newLevel).
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /__ / .__/\_,_/_/ /_/\_\   version 3.0.0
      /_/

Using Python version 3.6.8 (default, Apr  2 2020 13:34:55)
SparkSession available as 'spark'.

```
3. See resourcemanager webui http://localhost:8088 and learn applicaionId from there.  

4. List yarn applications  
In terminal-2:  
```[train@localhost play]$ yarn application -list
WARNING: YARN_CONF_DIR has been replaced by HADOOP_CONF_DIR. Using value of YARN_CONF_DIR.
2020-09-15 22:06:12,398 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
Total number of applications (application-types: [], states: [SUBMITTED, ACCEPTED, RUNNING] and tags: []):1
                Application-Id      Application-Name        Application-Type          User           Queue                  State              Final-State             Progress                        Tracking-URL
application_1600195619400_0002          PySparkShell                   SPARK         train         default                RUNNING                UNDEFINED                  10%               http://10.0.2.15:4040
```

5. Status of application  
```
[train@localhost play]$ yarn application -status application_1600195619400_0002
WARNING: YARN_CONF_DIR has been replaced by HADOOP_CONF_DIR. Using value of YARN_CONF_DIR.
2020-09-15 22:09:27,099 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
2020-09-15 22:09:27,902 INFO conf.Configuration: resource-types.xml not found
2020-09-15 22:09:27,903 INFO resource.ResourceUtils: Unable to find 'resource-types.xml'.
Application Report :
        Application-Id : application_1600195619400_0002
        Application-Name : PySparkShell
        Application-Type : SPARK
        User : train
        Queue : default
        Application Priority : 0
        Start-Time : 1600196421910
        Finish-Time : 0
        Progress : 10%
        State : RUNNING
        Final-State : UNDEFINED
        Tracking-URL : http://10.0.2.15:4040
        RPC Port : -1
        AM Host : 10.0.2.15
        Aggregate Resource Allocation : 1368551 MB-seconds, 1071 vcore-seconds
        Aggregate Resource Preempted : 0 MB-seconds, 0 vcore-seconds
        Log Aggregation Status : DISABLED
        Diagnostics :
        Unmanaged Application : false
        Application Node Label Expression : <Not set>
        AM container Node Label Expression : <DEFAULT_PARTITION>
        TimeoutType : LIFETIME  ExpiryTime : UNLIMITED  RemainingTime : -1seconds
```

6. Logs of yarn application  
save logs in a file then read with less
```
[train@localhost play]$ yarn logs -applicationId application_1600195619400_0002 > yarnApp_002_logs
WARNING: YARN_CONF_DIR has been replaced by HADOOP_CONF_DIR. Using value of YARN_CONF_DIR.
2020-09-15 22:11:05,765 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
[train@localhost play]$ less yarnApp_002_logs
```

7. Run a yarn application  and see it is in accepted state.
```
[train@localhost play]$ yarn jar mapreduce.wordcount.jar com.veribilimiokulu.mapreduce.MR2WordCount /user/train/datasets/dried_fruits_input /user/train/datasets/dried_fruits_out


```

8. Kill PySparkshell application on Resource Manager UI or command line (exit()) and see yarn application (mapreduce) chaged running state.  


9. See the application outputs  
```
[train@localhost play]$ hdfs dfs -cat /user/train/datasets/dried_fruits_out/part-r-00000
ANTEP FISTIK    2244
CEVIZ   13020
FINDIK  7842
KAJU    6186
YER FISTIĞI     1866
ÇIĞ FINDIK      1866
ÜZÜM    7716
```

10. Open Resource manager UI and see yarn application moved running state to finished one. See also PySparkshell application in killed state.  

11. List all running nodes  
```
[train@localhost play]$ yarn node -all -list
WARNING: YARN_CONF_DIR has been replaced by HADOOP_CONF_DIR. Using value of YARN_CONF_DIR.
2020-09-16 09:49:54,185 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
Total Nodes:1
         Node-Id             Node-State Node-Http-Address       Number-of-Running-Containers
 localhost:44803                RUNNING    localhost:8042                                  0
 ```

 12. See the status of node  
 ```
 [train@localhost play]$ yarn node -status localhost:44803
WARNING: YARN_CONF_DIR has been replaced by HADOOP_CONF_DIR. Using value of YARN_CONF_DIR.
2020-09-16 09:51:44,549 INFO client.RMProxy: Connecting to ResourceManager at /0.0.0.0:8032
2020-09-16 09:51:45,368 INFO conf.Configuration: resource-types.xml not found
2020-09-16 09:51:45,369 INFO resource.ResourceUtils: Unable to find 'resource-types.xml'.
Node Report :
        Node-Id : localhost:44803
        Rack : /default-rack
        Node-State : RUNNING
        Node-Http-Address : localhost:8042
        Last-Health-Update : Wed 16/Sep/20 09:50:59:541TRT
        Health-Report :
        Containers : 0
        Memory-Used : 0MB
        Memory-Capacity : 3500MB
        CPU-Used : 0 vcores
        CPU-Capacity : 8 vcores
        Node-Labels :
        Resource Utilization by Node : PMem:4199 MB, VMem:4294 MB, VCores:0.55962694
        Resource Utilization by Containers : PMem:0 MB, VMem:0 MB, VCores:0.0
```

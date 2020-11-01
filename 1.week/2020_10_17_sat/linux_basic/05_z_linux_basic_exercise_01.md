
# SORULAR

1. MY_ML_APP_HOME glabal değişkeni oluşturup PATH'e dahil ediniz. PATH içindekileri yazdırarak kontrol ediniz.

2. Varsayılan olarak bash shell'ini kullanan kullanıcıları listeleyiniz.

3. /etc/hosts dosyası içerisinde localhost bulunan satır numaralarını gösteriniz

4. /etc/hosts içinde  localhost kelimesinin dosya içinde kaç kez tekrarlandığını bukunuz.

5. /etc dizininde kaç tane klasör olduğunu bulunuz?  

6. /etc dizininde .conf uzantılı dosyaların boyutunu ve sayısını bulunuz.





# CEVAPLAR

1. MY_ML_APP_HOME glabal değişkeni oluşturup PATH'e dahil ediniz. PATH içindekileri yazdırarak kontrol ediniz.
```
[train@localhost linux_basic]$ export MY_ML_APP_HOME=/home/train/mlapp

[train@localhost linux_basic]$ PATH="$PATH:$MY_ML_APP_HOME"

[train@localhost linux_basic]$ echo $PATH
/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin:/home/train/.local/bin:/home/train/bin:/usr/lib/jvm/java-1.8.0-openjdk//bin:/opt/manual/kafka//bin:/opt/manual/hadoop//bin:/opt/manual/hadoop//sbin:/opt/manual/hive//bin:/opt/manual/sqoop//bin:/opt/manual/spark//bin:/opt/manual/maven//bin:/opt/manual/intellij//bin:/opt/manual/pycharm//bin:/opt/manual/presto//bin:/home/train/mlapp
```


2. Varsayılan olarak bash shell'ini kullanan kullanıcıları listeleyiniz.

Answer: 
``` 
[train@localhost ~]$ cat /etc/passwd | grep /bin/bash$
root:x:0:0:root:/root:/bin/bash
train:x:1000:1000:train:/home/train:/bin/bash
postgres:x:26:26:PostgreSQL Server:/var/lib/pgsql:/bin/bash
user1:x:1001:980::/home/user1:/bin/bash
```

3. /etc/hosts dosyası içerisinde localhost bulunan satır numaralarını gösteriniz

Display localhost information from the /etc/hosts file, display the line number(s) matching the search string and count the number of occurrences of the string.

Answer:  
```
[train@localhost ~]$ cat /etc/hosts | grep -o -i -n localhost
1:localhost
1:localhost
1:localhost
1:localhost
2:localhost
2:localhost
2:localhost
2:localhost
```
4. /etc/hosts içinde  localhost kelimesinin dosya içinde kaç kez tekrarlandığını bukunuz.
```
[train@localhost ~]$ cat /etc/hosts | grep -o -i -n localhost | wc -l
8
```

5. /etc dizininde kaç tane klasör olduğunu bulunuz?  
Answer:
```
[train@localhost linux_basic]$ ls -l /etc | grep -c ^d
147
```

6. /etc dizininde .conf uzantılı dosyaların boyutunu ve sayısını bulunuz.
Answer
```
[train@localhost linux_basic]$ ll /etc | grep .conf$ | du -hs
11M
```











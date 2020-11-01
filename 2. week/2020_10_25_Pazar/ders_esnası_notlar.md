## Ana bilgisayardan sanal makineye dosya kopyalama gitbash 

```
$ scp -P 22 /c/Users/user/movies.json train@localhost:/home/train/datasets
Ankatrain@localhost's password:
movies.json                                                                                                         100%  844     0.8KB/s   00
```

# Git



## Alıştırma 
Bir git projesi oluşturunuz. Proje içinde iki adet dosya oluşturup bir tanesini staging area'ya ekleyiniz.


## İki commit arasında bir dosya içindeki değişikilikleri karşılaştırma
```
[train@localhost git_project]$ git diff dbc5c8de11  322740671 myfile
diff --git a/myfile b/myfile
index 9765325..4886f4a 100644
--- a/myfile
+++ b/myfile
@@ -1 +1,3 @@
 Merhaba ben ilk satırım
+
+Bu ikinci satırım
```

gitbash kopyalama seçince kopyalar, Ctrl+insert 
gitbash yapıştırma, Ctrl+Shift+V, Ctrl+insert 

## Önceki commitlerden birisine geri dönmek 
```
[train@localhost git_project]$ git checkout dbc5c8de11c -- myfile
[train@localhost git_project]$ cat myfile
Merhaba ben ilk satırım
```

## Github repo tanıtma
[train@localhost git_project]$ git remote add origin https://github.com/erkansirin78/git-lessons.git

## Eklenmiş repo 
[train@localhost git_project]$ git remote
origin

## Github repo push (kodları github'a gönderme)
[train@localhost git_project]$ git push origin master


## Github remote branch silme 
1. Önce github arayüzünden default branch'i değiştir (eğer sileceğin default branch ise)
settings -> branches -> Default branch

2. Aşağıdaki komut ile istediğin branch'ı sil. 
[train@localhost git_project]$ git push origin --delete main

## Git clone 
[train@localhost git_project]$ git clone https://github.com/erkansirin78/git-lessons.git

git clone sadece repo içeriğini kopyalar. Git projesi başlamaz.


# Crontab 

Diğer araçlar 
Ooozie, Airflow, Azkaban (Job scheduling) 

- crontab işlerini listeleme
[train@localhost mycron-jobs]$ crontab -l
#*/1 * * * * /home/train/cronjobs/make_a_file.sh >> /home/train/cronjobs/make_a_file.log 2>&1
#* * * * * /home/train/mycron-jobs/my_script.sh >> /home/train/mycron-jobs/my_script_logs.log 2>&1

- crontab işi tanımlama
crontab -e 

- log tail etme
tail -f <logdosyası>



# Postgresql 
- kullanıcı
- password 
- sunucu nerede?
- Hangi veritabanına erişilecek 

[train@localhost ~]$ psql -h localhost -p 5432 -U train -W -d traindb

Pratik bağlantı 
[train@localhost ~]$ psql -U train -d traindb
Password: Ankara06 


# linux shell üzerinden postgresql'e komut gönderme 
[train@localhost postgresql]$ psql -U train -d traindb -c "select * from users;"
Password for user train:
 id | name | age
----+------+-----
(0 rows)



# Bir dosyadan postgresql tabloya veri kopyalama 
[train@localhost postgresql]$ psql -U train -d traindb -c "\copy users from users.csv DELIMITERS ',' CSV HEADER;
Password for user train:


users.csv 
id,name,age
1,Murat,33
2,Aslı,45
3,Tarık,23
4,Cemalettin,32
5,Serap,29
 
[train@localhost postgresql]$ psql -U train -d traindb -c "select * from users;"
Password for user train:
 id |    name    | age
----+------------+-----
  1 | Murat      |  33
  2 | Aslı       |  45
  3 | Tarık      |  23
  4 | Cemalettin |  32
  5 | Serap      |  29
(5 rows)


Bakılacaklar






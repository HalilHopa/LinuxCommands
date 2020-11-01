1. Aşağıdaki telefon numaralarını bir dosyaya kaydediniz. regex ile `(xxx) xxx xxxx` paternine sahip numaraları `gecerli-numaralar.txt` uymayanları da `gecersiz-numaralar.txt` dosyalarına yazdırınız.  
```
(532) 432 5567
(544) 213 8832
(312) 244 4195
0532 543456
+90544 876 55 44
(212) 220 2225
0 (216) 395 9569
```

2. Önemli bilgilerin bulunduğu bir dosya yaratın. Bu dosyayı sadece kullanıcı okuyabilsin.





# CEVAPLAR
1. Aşağıdaki telefon numaralarını bir dosyaya kaydediniz. regex ile `(xxx) xxx xxxx` paternine sahip numaraları `gecerli-numaralar.txt` uymayanları da `gecersiz-numaralar.txt` dosyalarına yazdırınız.  
```
(532) 432 5567
(544) 213 8832
(312) 244 4195
0532 543456
+90544 876 55 44
(212) 220 2225
0 (216) 395 9569
``` 
Cevap-1: 

```
grep "^([0-9]\{3\}) [0-9]\{3\} [0-9]\{4\}$" numbers > gecerli-numaralar.txt
grep -v "^([0-9]\{3\}) [0-9]\{3\} [0-9]\{4\}$" numbers > gecersiz-numaralar.txt

[train@localhost linux]$ cat gecerli-numaralar.txt
(532) 432 5567
(544) 213 8832
(312) 244 4195
(212) 220 2225
[train@localhost linux]$ cat gecersiz-numaralar.txt
0532 543456
+90544 876 55 44
0 (216) 395 9569
```

2. Önemli bilgilerin bulunduğu bir dosya yaratın. Bu dosyayı sadece kullanıcı okuyabilsin.
Cevap-2:
```
[train@localhost linux]$ cat <<EOF > important_file
> Ankara06
> EOF
[train@localhost linux]$ ll important_file
-rw-rw-r--. 1 train train 9 Oct 17 22:29 important_file
[train@localhost linux]$ chmod a=--- important_file
[train@localhost linux]$ chmod u=r-- important_file
[train@localhost linux]$ ll important_file
-r--------. 1 train train 9 Oct 17 22:29 important_file
[train@localhost linux]$ cat important_file
Ankara06
```


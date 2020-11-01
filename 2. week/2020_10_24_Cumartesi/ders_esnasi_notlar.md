

if (koşul) then şunu yap else bunu yap 

# Temel if koşulu 
```
[train@localhost ~]$ cat conditionals.sh
#!/bin/bash

isim=Burcu
if [ $isim = Erkan ]
  then
    echo "İsminiz $isim"
  else
    echo "isminiz Erkan değil"
  fi
```

# Temel if koşuşu ; kullanarak 
```
[train@localhost ~]$ cat conditionals.sh
#!/bin/bash

isim=Burcu
if [ $isim = Erkan ] ; then
    echo "İsminiz $isim"
  else
    echo "isminiz Erkan değil"
  fi
 ```
 # Dizin kontrolü örneği
 ```
 [train@localhost bash-script]$ cat conditionals.sh
#!/bin/bash

DIRECTORY=/home/train/bash-script
if [ -d $DIRECTORY ] ; then
    echo "Bu $DIRECTORY  var."
  else
    echo "Bu $DIRECTORY yok."
  fi

```
 # Alıştırma: Bulunduğunuz dizinde test.sh adında bir dosya (file) olup olmadığını kontrol edin
 # Eğer dosya yok ise yaratın var ise var diye ikaz edin.
 ```
 [train@localhost bash-script]$ cat conditionals2.sh
#!/bin/bash

FOLDER=/home/train/bash-script/test.sh
if [ -f $FOLDER ] ; then
    echo "Bu $FOLDER dosyası var."
  else
    echo "Bu $FOLDER dosyası yok."
    touch test.sh
  fi

```
Kontrol 

```
[train@localhost bash-script]$ ./conditionals2.sh
Bu /home/train/bash-script/test.sh dosyası yok.

[train@localhost bash-script]$ ./conditionals2.sh
Bu /home/train/bash-script/test.sh dosyası var.
```
 
 
 Matematiksel karşılaştırma
 ```
 [train@localhost bash-script]$ cat condition-math.sh
#!/bin/bash

SAYI=3
if (( $SAYI > 5 )) ; then
    echo "Sayı 5 dan büyüktür."
  else
    echo "Bu $SAYI 5 dan küçüktür."
  fi

```

Eğer koşulun içinde > veya < kullanıyor isek [[ ]] veya (( )) kullanmalıyız.

Matematiksel ifadeleri SONUC=$((5*8)) örneğinde olduğu gibi bir değişkene atayabiliriz.

# Alıştırma: 33 sayısının 5'in katı olup olmadığını sınayan bir script yazınız.
 
 ```
 #!/bin/bash

SAYI=30
kalan=$(($SAYI%5))
if [ $kalan = 0 ]
  then
    echo "$SAYI sayısı 5'e tam bölünüyor"
  else
    echo "$SAYI sayısının 5 ile bölümünden kalan $kalan dır."
fi
```
 
# ARGUMENTS

Argüman kullanan script:
```
[train@localhost bash-script]$ cat basic-script.sh
#!/bin/bash

ISIM=$1
SOYISIM=$2
echo "Benim adım $ISIM, soyadım $SOYISIM."
echo "Çalışan script: $0"
echo "Bu scriptte $# tane argüman var."
```

Kullanım:
```
[train@localhost bash-script]$ ./basic-script.sh Erkan Şirin
Benim adım Erkan, soyadım Şirin.
Çalışan script: ./basic-script.sh
Bu scriptte 2 tane argüman var.
```


# FOR LOOP

Script:
```
[train@localhost bash-script]$ cat for_loop.sh
#!/bin/bash

for (( i=0; i<=10; i++ ))
  do
    echo $i
  done
```

Kullanım 
```
[train@localhost bash-script]$ ./for_loop.sh
0
1
2
3
4
5
6
7
8
9
10
```


## Alıştırma: İki sayı arasındaki tek sayıları ekrana yazdıran bir script yazınız.
```
[train@localhost bash-script]$ cat for_loop.sh
#!/bin/bash
SAYI1=$1
SAYI2=$2

for (( i=$SAYI1; i<$SAYI2; i++ ))
  do
    if [ $((i%2)) = 1 ]
     then
       echo $i
    fi
  done

```
Test:
```
[train@localhost bash-script]$ ./for_loop.sh 10 20
11
13
15
17
19
```

## Inline for loop örneği 
```
[train@localhost bash-script]$ for i in {1..5}; do echo $i; done
1
2
3
4
5
```

## Bir dizin içinde for döngüsü 
```
[train@localhost bash-script]$ cat loop_dir.sh
#!/bin/bash

DIRECTORY=$1

for file in $DIRECTORY/*
  do
    echo $file
  done
[train@localhost bash-script]$ ./loop_dir.sh $(pwd)
/home/train/bash-script/5
/home/train/bash-script/basic-script.sh
/home/train/bash-script/conditionals2.sh
/home/train/bash-script/conditionals.sh
/home/train/bash-script/condition-math.sh
/home/train/bash-script/for_loop.sh
/home/train/bash-script/loop_dir.sh
/home/train/bash-script/read
/home/train/bash-script/test.sh
```
## Bir dosya içindeki satırlarda for döngüsü ile gezme
```
[train@localhost bash-script]$ cat for_loop_file.sh
#!/bin/bash

for line in $(cat  ~/datasets/insanlar.csv)
  do
    echo $line
  done
[train@localhost bash-script]$ ./for_loop_file.sh
1,"Gülsüm",35
2,"Cemal",23
3,"Elif",29
4,"Funda",41
5,"Hamza",33
6,"Yalçın",45
7,"Mehmet",44
8,"Gülay",33
9,"Cumhur",38
10,"Burcu",41
11,"Metin",47
12,"Veysel",53
```

# WHILE LOOP 
```
[train@localhost bash-script]$ cat while_loop.sh
#! /bin/bash

while read adres; do
    ping -c 1 $adres
done < dns.txt
[train@localhost bash-script]$ ./while_loop.sh
PING www.google.com (172.217.169.196) 56(84) bytes of data.
64 bytes from sof02s34-in-f4.1e100.net (172.217.169.196): icmp_seq=1 ttl=117 time=33.5 ms

--- www.google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 33.537/33.537/33.537/0.000 ms
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=117 time=28.1 ms

--- 8.8.8.8 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 28.199/28.199/28.199/0.000 ms
PING 8.8.4.4 (8.8.4.4) 56(84) bytes of data.
64 bytes from 8.8.4.4: icmp_seq=1 ttl=117 time=34.8 ms

--- 8.8.4.4 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 34.814/34.814/34.814/0.000 ms
```

dns.txt
```
[train@localhost bash-script]$ cat dns.txt
www.google.com
8.8.8.8
8.8.4.4
```








# FUNCTIONS
```
[train@localhost bash-script]$ cat functions.sh
#!/bin/bash
SAYI1=$1
SAYI2=$2
toplama() {

   echo "$(($SAYI1+$SAYI2))"
}

toplama
[train@localhost bash-script]$ ./functions.sh 5 8
13
```



## Alıştırma 
xxxx-1, xxxx-2, ..... xxxx-n şeklinde isimlendirilmek üzere ardışık numaralarla klasör/dosya yaratan bir script yazınız.
argüman 1: kaç tane klasör/dosya yaratılacak?
argüman 2: Dosya mı klasör mü yaratılacak?
argüman 3: Dosya/klasör sabit kısmında kullanılacak isim.
```
#!/bin/bash

NUMBER=$1
FILE_OR_FOLDER=$2
CONSTANT_PART=$3

for (( i=1; i<=$NUMBER; i++ ))
  do
    if [ $FILE_OR_FOLDER = folder ]
      then
        mkdir ${CONSTANT_PART}-$i
      else
        touch ${CONSTANT_PART}-$i
    fi
  done
 ```
Test:
```
[train@localhost kurs]$ ./generate_filenames.sh 5 file myfile

[train@localhost kurs]$ ./generate_filenames.sh 5 folder myfolder

[train@localhost kurs]$ ll
total 4
-rwxr-xr-x. 1 train train 235 Oct 18 17:21 generate_filenames.sh
-rw-rw-r--. 1 train train   0 Oct 18 17:21 myfile-1
-rw-rw-r--. 1 train train   0 Oct 18 17:21 myfile-2
-rw-rw-r--. 1 train train   0 Oct 18 17:21 myfile-3
-rw-rw-r--. 1 train train   0 Oct 18 17:21 myfile-4
-rw-rw-r--. 1 train train   0 Oct 18 17:21 myfile-5
drwxrwxr-x. 2 train train   6 Oct 18 17:22 myfolder-1
drwxrwxr-x. 2 train train   6 Oct 18 17:22 myfolder-2
drwxrwxr-x. 2 train train   6 Oct 18 17:22 myfolder-3
drwxrwxr-x. 2 train train   6 Oct 18 17:22 myfolder-4
drwxrwxr-x. 2 train train   6 Oct 18 17:22 myfolder-5
```













Bakılacak konular:
1. argümanları isimlendirme argparse
getops ile bir örnek 03_arguments.md dersine eklendi.


2. Bashscript'te veri türü var mı kontrolü nasıl olur?
Programlama dillerinde olduğu gibi bash içinde veri türü yok. Çünkü sınıf kavramı yok.
Diller genelde veri türlerini sınıflarla tanımlıyor. Ancak sınırlı bir şekilde
type tanımlanabilir. Detaylı bilgi için bakınız: 
https://stackoverflow.com/questions/29840525/get-variable-type-in-bash


3. Fonksiyon sonunda parantez olup olmaması neyi değiştiriyor?
Fonksiyon tanımında iki yöntem var 
Eğer function <function_name> {} kullanılırsa () kullanılmayabilir.
<function_name(){} yönteminde () kullanmak gerekiyor. 
Fonksiyon çağırırken () kullanmıyoruz.




















 
 
 
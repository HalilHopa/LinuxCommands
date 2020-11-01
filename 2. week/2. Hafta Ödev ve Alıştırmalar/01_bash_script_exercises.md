# SORULAR
1. Bir dizini argüman olarak alan ve aşağıdakileri işleri yapan bir script yazınız.  
    - Bütün dosya ve klasörleri dolaşsın  
    - Klasör olanların disk kullanımlarını yazdırsın.

Answer: /home/train/advanced_ds_bigdata/exercises/bash_script/print_disk_sizes_of_folders.sh

2. Aşağıdaki işleri yapan bir script yazınız:
- İki argüman alacak: 1. argüman dosya adı 2. argüman klasör dosya yolu (path) olacak
- dosya adı o dizinde yok ise yeni dosya yaratsın
- Yaratılan yeni dosyayı bir kendi adını (1. argümanda verilen) söyleyen bir script haline getirsin
- Bu script'i çalıştırsın.

Örnek komut ve çıktı
```
[train@localhost play]$ ./exercise2.sh execrcise2-test $(pwd)
execrcise2-test doesn't exist.
My name is execrcise2-test.

[train@localhost play]$ ./exercise2.sh execrcise2-test $(pwd)
execrcise2-test exists
My name is execrcise2-test.
```

3.  `xxxx-1, xxxx-2, ..... xxxx-n ` şeklinde isimlendirilmek üzere ardışık 
numaralarla klasör/dosya yaratan bir script yazınız.
- argüman 1: kaç tane klasör/dosya yaratılacak?
- argüman 2: Dosya mı klasör mü yaratılacak?
- argüman 3: Dosya/klasör sabit kısmında kullanılacak isim.
Örnek komut ve beklenen çıktı: 
```
[train@localhost kurs]$ ./generate_filenames.sh 5 file myfile
-rwxr-xr-x. 1 train train 235 Oct 18 17:21 generate_filenames.sh
-rw-rw-r--. 1 train train   0 Oct 18 17:21 myfile-1
-rw-rw-r--. 1 train train   0 Oct 18 17:21 myfile-2
-rw-rw-r--. 1 train train   0 Oct 18 17:21 myfile-3
-rw-rw-r--. 1 train train   0 Oct 18 17:21 myfile-4
-rw-rw-r--. 1 train train   0 Oct 18 17:21 myfile-5
```

4. Inline for loop döngüsü yazınız.
- Her döngüde 1 saniye uyusun
- 10 kez dönsün
- tek sayıları ekrana yazsın.

5. Paket yöneticisi ile `tree` paketini kurunuz. Eğitimi takip ettiğiniz dizini ağaç yapısında listeleyiniz.

# 	Linux Example 

1- My_script.text adında bir dosya oluşturunuz. İçine "Hello , I am learn Bash Script" yazıp , oluşturduğunuz dosyayı shellde yazdırınız.

Çözüm:

```bash
touch My_script.text #yeni bir dosya oluşturur

nano My_script.text #metin düzenleyicisi açar.  "Hello , I am learn Bash Script" #kayıt edip çıkış yapın

cat mkdi My_script.text #yazdırır
```

2-  Linux komut satırında gerekli komutları kullanarak bir klasör oluşturunuz ve oluşturduğunuz klasöre komut satırından erişip görüntüleyiniz.

```bash
mkdir my_file

cd my_file
```

3- Linux komut satırından  desktop klasörünün içerisinde "file" kelimesi geçen dosyaları listeleyiniz.

Örnek:

```bash
find [arama-yapilacak-dizin] [opsiyon] [aranacak-orgu]
```

Çözüm:

```bash
find Desktop -name "*file*"
```

4-Linux komut satırından bir dosyaya gidip 2-3 dosyayı .tar dosyasında sıkıştırınız ve .tar dosyasında sıkıştırılan dosyaları listeleyip , bu dosyaları .tar dan çıkarınız.

```bash
tar -cvf ornekArsiv.tar /home/ornekArsiv
Bu örnekte sıkıştırılması gereken dizin /home/ornekArsiv‘dir ve bunun sonucu olarak ornekArsiv.tar oluşacaktır.

Komut -cvf seçenekleri kullanır:

c – Yeni bir .tar dosyası oluşturur
v – sıkıştırma işleminin ayrıntılı açıklamasını gösterir
f – dosya adı

Arşiv oluşturulduktan sonra içerikleri aşağıdakine benzer bir komut kullanarak listeleyebilirsiniz:
tar -tvf ornekArsiv.tar

Linux tar komutu ayrıca bir dosyanın içindekileri çıkarmak için kullanılabilir. Aşağıdaki komut dosyaları mevcut dizine çıkaracaktır:
tar -xvf ornekArsiv.tar
```

5-Linux komut satırında çalıştığınız son 10 kodu yazdırınız.

```bash
history 10
```

6-  Linux komut satırında NewFile diye bir klasör oluşturup içerisine myText adlı bir dosya ekleyiniz. Oluşturduğunuz myText i silip, tekrar desktop dizinine gelip en son oluşturduğunuz klasörü siliniz.

```bash
mkdir newFile #yeni dosya oluşturduk.

cd newFile #dosyanın bulunduğu dizine gittik.

touchMytext # bulunduğumuz dizine myText dosyası ekledik

rm myText # myText dosyasını sildik

cd.. #Önceki dizine gittik.

rm -r newFile/ #newFile sildik.
```

7-Linux komut satırında  oldFile ve new isminde iki klasör oluşturunuz, oldFile klasörünü new klasörünün içine atıp new dizinine giriniz. oldFile dosyasının adını myFile olarak değiştiriniz.

```bash
cd Desktop/

mkdir oldFile

mkdir new

mv oldFile new/

cd new/

mv oldfile newFile
```

8- Linux komut satırında bulunduğunuz dizini listeleyiniz.

Çözüm:

```bash
ls
```

9-  Linux komut satırında gerekli olan komutları kullanarak herhangi bir komutu bir değişkene atayıp yazdırınız.

Örnek : 

```bash
alias cls=clear #clear komutunu cls olarak isimlendirmiş olduk.
```

Çözüm:

```bash
alis deneme=cd #atama işlemi gerçekleştirildi.
```

10-  Linux komut satırından herhangi bir dosyanın içine gidip dosyanın izinlerini değiştiriniz.

```bash
Bazı chmod örnekleri :

chmod +r deneme : deneme dosyasına okuma® izni vermiş olduk.
chmod u=rw,go= deneme : Dosya sahibine okuma ve yazma izni verdik. Grup ve diğerleri için tüm erişim izinlerini kaldırdık.
chmod +x dosyaismi : Dosyaya tüm kullanıcılar (user,group,other) için çalıştırma izni verdik.
chmod +rw dosyaismi : Komutu veren user için okuma ve yazma izni grup ve diğerleri için sadece okuma izinlerini verdik.
```

11- Linux komut satırından herhangi bir dosyanın path'ini (yolunu) yazdırınız.

Çözüm:

```bash
find -iname "my_file"
```

12- Linux komut satırından gerekli komutları kullanarak "examples "adlı bir klasör oluşturunuz. Oluşturduğunuz dosyanın altında "2020" adlı yeni bir dizin oluşturunuz.

Çözüm:

```bash
mkdir examples

mv examples 2020/

```

13- Linux komut satırında "touch" komutunu kullanarak yeni bir directory oluşturup içine hello.text adında bir dosya ekleyip yazdırınız.

Çözüm:

```bash
touch Deneme/Ornek.txt
```

14-  13. soruda oluşturduğunuz dosyayı gerekli komutlar kullanarak aynı dizin içerisinde kopyalayınız.

Çözüm:

```bash
cp Deneme/Ornek.txt Ornek2.txt
Bu komut aktif klasördeki Deneme klasöründeki Ornek.txt dosyasını (az önce oluşturduğumuz dosya) geçerli klasöre kopyalar.
NOT: cp komutu klasör kopyalayamaz. Sadece dosya kopyalayabilir.

```

15- Linux komut satırından "Deneme" adında bir dosya oluşturunuz. Oluşturduğunuz dosyanın içeresine hi.text adında bir dosya ekleyip gerekli komutlarla bu dosyanın ismini değiştiriniz.

Çözüm:

```bash
mkdir Deneme

touch hi.text

mv hi.text hello.text

ls
```

16- Linux komut satırından oluşturduğunuz bir dosyanın izinlerini root olarak değiştiriniz.

```bash
# Seçeceğiniz bir dosyanın izinlerini bu komutlarla takip edebilirsiniz.
chmod komutunun parametrelerini tanıyarak örnek verme işlemine geçelim.

u : Dosya-dizinin sahibi

g : Dosya-dizinin sahibi ile aynı grupta bulunan kullanıcılar

o : Diğer kullanıcılar

a : Herkese açık.

= : Yetki eşitleme

+ : Yetki ekleme

- : Yetki çıkarma
```

17- Linux komut satırından oluşturduğunuz bir dosyanın izinlerini sadece okuma olarak değiştiriniz.

Çözüm:

```bash
# Seçeceğiniz bir dosyanın izinlerini bu komutlarla takip edebilirsiniz.
chmod komutunun parametrelerini tanıyarak örnek verme işlemine geçelim.

u : Dosya-dizinin sahibi

g : Dosya-dizinin sahibi ile aynı grupta bulunan kullanıcılar

o : Diğer kullanıcılar

a : Herkese açık.

= : Yetki eşitleme

+ : Yetki ekleme

- : Yetki çıkarma
```

18- Linux komut satırından geçerli olan dizini yazdırınız.

Çözüm :

```bash
pwd
```

19- Desktopta bir text dosyası oluşturunuz. Linux komut satırından bu dosyanın ilk 10 satırını yazdırınız.

Örnek:

```bash
head examplefile.txt #not: head fonkisyonunun ön tanımlı değeri 10dur.

Fatih elmasuyu 20
Suzan portakalsuyu 5
Melih kavunsuyu 12
Melih kavunsuyu 12
Rasim kirazsuyu 4
Tarık portakalsuyu 9
Lale şeftalisuyu 7
Suzan portakalsuyu 12
Melih kayısısuyu 39
Ayşe mangosuyu 7
```

Çözüm:

```
head examplefile.txt
```

20- Linux komut satırında çalıştığınız penceredeki tüm komutları temizleyiniz.

```bash
clear
```

21- Linux komutlarını kullanarak nano komutunun yüklü olduğunu kontrol ediniz.Ardından bir nano editörü açıp , "Hello , I am learn Bash Script" yazıp dosyayı kaydediniz.

```
$ sudo yum install nano #yükleme işlemi gerçekleştirildi
Mevcut bir dosyayı açmak veya yeni bir dosya oluşturmak için, nanoardından dosya adını yazın:
$nano filename
Bu, yeni bir düzenleyici penceresi açar ve dosyayı düzenlemeye başlayabilirsiniz.
```

İpucu:

### Temel Nano Metin Düzenleyicisi Komutları

| **Komut**    | Açıklama                                                     |
| :----------- | ------------------------------------------------------------ |
| **CTRL + A** | Satırın başına git.                                          |
| **CTRL + E** | Satırın sonuna git.                                          |
| **CTRL + Y** | Sayfayı aşağı kaydır.                                        |
| **CTRL + V** | Sayfayı yukarı kaydır.                                       |
| **CTRL + G** | Nano editörü ile kullanabileceğiniz tüm komutlarla ilgili bilgi içeren bir **Yardım** penceresi getirecektir. |
| **CTRL + O** | Dosyayı kaydetmek için kullanılır. Nano sizden istediğiniz dosya adınızı düzenlemenizi veya doğrulamanızı ister. |
| **CTRL + W** | Metninizde belirli bir ifadeyi aramak için kullanılır. Aynı ifadeyi tekrar aramak için **ALT + W** tuşlarına basın. |
| **CTRL + K** | Seçili olan tüm satırı “kesme ara belleği”ne keser.          |
| **CTRL + U** | Metni “kesme arab belleği”nden seçilen satıra yapıştırır.    |
| **CTRL + J** | Seçili paragrafı iki yana yaslar.                            |
| **CTRL + C** | Metindeki imleç pozisyonunu gösterir. (satır/sütun/karakter). |
| **CTRL + R** | Bir dosyayı açar ve imleç konumuna yerleştirir.              |
| **CTRL + X** | Nano metin düzenleyicisinden çıkar. Eğer dosyada değişiklik yaptıysanız, kaydetmek isteyip istemediğinizi sorar. |
| **CTRL + \** | Dizi ve normal ifadeyi değiştirin.                           |
| **CTRL + T** | Eğer mevcutsa yazım denetleyicisini açar.                    |
| **CTRL + _** | Belirli satır ve sütun numarasına gitmenize izin verir.      |
| **ALT + A**  | Metin seçer. Bu komutu **CTRL + K** tuşlarıyla birleştirerek metnin bir bölümünü “kesme ara belleği”ne kesebilirsiniz. |

22- Linux komutlarıyla vi dosyası oluşturup içine "Hello , I am learn linux" yazıp kayıt ediniz ve yazdırınız.

```bash
vi dosyaAdi 
#yeni dosya açıldı buraya yazılarımızı yazabiliriz.
#Dosyamızda yaptığımız değişiklikleri kaydetmek için “:w” ;
#Dosyamızdan direkt olarak çıkış yapmak istiyorsak “:q!”;
#Dosyamızdaki değişiklikleri hem kaydedip hem de çıkmak istiyorsak “:wq”
#Dosyada bir değişiklik varsa kaydedip çıksın, yoksa da direkt olarak çıkması için “:x”;
#İmlecimizin bulunduğu satırı kopyalamak için “yy”, kopyaladığımız satırı yapıştırmak içinse “p” yazmamız yeterlidir.Tabiki bu #seçeneklerin hangisini kullanırsak kullanalım “enter” tuşuna basmadan herhangi Bir şey yapamayız.

Yazdırmak için ---->>> echo dosyaAdi 
```

23- Linux komutlarıyla yeni bir kullanıcı oluşturun ve ön tanımlı ayarlarını değiştiriniz.

```bash
useradd [-c açıklama] [-d evdizini]
        [-e bitiş_tarihi] [-f askı_süresi]
        [-g birincil_grup] [-G grup[,...]]
        [-m [-k iskelet_dizin] | -M] [-p parola]
        [-s kabuk] [-u kull_kiml [ -o]] [-n] [-r] kullanıcı

useradd -D [-g öntanımlı_grup] [-b öntanımlı_ev]
        [-f öntanımlı_askı_süresi] [-e öntanımlı_bitiş_tarihi]
        [-s öntanımlı_kabuk]
        
        #yukardaki komutlarla yeni kullanıcı oluşturulur ve ön tanımlı ayarlar değiştirilebilir.
```

24- Usermod kullanarak oluşturduğunuz yeni kullanıcıyı düzenleyiniz.

```bash
usermod — bir kullanıcı hesabını düzenler
#usermod komutu, sistem hesap dosyalarını düzenlemeye, üzerlerinde değişiklik yapmaya yarar. Bu komuta uygulanabilecek seçenekler şunlardır:
usermod [-c açıklama] [-d evdizini [-m]]
        [-e bitiş_tarihi] [-f askı_süresi]
        [-g birincil_grup] [-G grup[,...]]
        [-l kullanıcı-adı]  [-p parola]
        [-s kabuk] [-u kull_kiml [-o]] [-L|-U] kullanıcı
```

25- Linux komutlarını kullanarak home dizinine gidip bir directory oluşturunuz. Bu directory içine localden kişisel bir kaç dosyanızı yükleyiniz.Burdaki dosyayı herhangi bir dizine yönlendirip rapor.txt dosyası oluşturunuz.

Çözüm:

```bash
$ cd 
~$ mkdir redirect 
~$ cd redirect 
~/redirect $ touch metin.txt resim.jpg belge.doc video.mpeg 
~/redirect $ ls 
belge.doc metin.txt resim.jpg video.mpeg
~/redirect $ ls > rapor.txt 
~/redirect $ ls 
belge.doc metin.txt rapor.txt resim.jpg video.mpeg
~/redirect $ cat rapor.txt
belge.doc
metin.txt
rapor.txt
resim.jpg
video.mpeg
```

26-Desktopta bir text dosyası oluşturunuz.Linux komut satırından bu dosyanın son 10 satırını yazdırınız.

```bash
Masaüstünde yeni bir dosya oluşturunuz.
$ tail yeni_dosya.text

```

27-Linux komut satırından yum komutunu kullanarak bilgisayarınızda yüklü olmayan bir uygulamayı kurunuz.

Örnek:

```bash
yum install firefox
```

28- Linux komut satırından yum komutunu kullanarak bilgisayarınızda yüklü olan bir uygulamayı siliniz.

Örnek:

```bash
yum remove firefox
```

29-Linux komut satırından belirlediğiniz 5 adet process komutuyla ilgili işlem yapınız.

```bash
Çalışan işlemleri listelemek için kullanabileceğiniz birkaç komut vardır: ps , top ve htop .

Çalışan işlemleriniz hakkında daha ayrıntılı bilgi almak için ps aux'u kullanabilirsiniz . 

Linux işlemlerini hiyerarşik bir görünümde listelemek istiyorsanız, ps -axjf komutunu kullanın.
ps -u [kullanıcı adı] belirli bir kullanıcının tüm çalışan işlemlerini listeler.
ps -e veya ps -A , etkin Linux işlemlerini genel UNIX biçiminde görüntüler.
ps -T , terminalden yürütülen etkin işlemleri yazdırır.
Ps -C işlem_adı listeyi işlem adına göre filtreleyecektir. Ayrıca bu komut, belirtilen sürecin tüm alt süreçlerini de gösterir.
```



30- Aşağıda verilen bütün komutlarla ilgili işlemler yapınız ve komutların ne işe yaradıklarını bir text dosyasına yazarak ödevler klasörüne yükleyiniz.

### 1. pwd

### 2. ls

### 3. cd

### 4. mkdir & rmdir

### 5. touch

### 6. man & -help

### 7. cp

### 8. mv

### 9. nano & vi

### 10. sudo

Çözüm:

### 1. pwd

Terminali ilk açtığımız zaman, giriş yapmış olduğunuz kullanıcının home dosyasında başlar. Eğer hangi dosyanın içinde olduğumuzu bilmek istiyorsak “pwd” komutunu yazarız. Bu komutun çıktısı bize roottan başlayarak tam hangi klasörde olduğumuzu gösterir. Root Linux bir sistemin temelidir. Root, eğik bir çizgi ile gösterilir(/).

![Yeni Başlayanlar için Basit Linux Komutları](https://aktif.net/files/images/news/basit-linux-komutlari-2.png)

Şekil 1: pwd komutu çıktısı.

### 2. ls

“ls” komutu, bulunduğunuz dizindeki hangi dosyaların olduğunu bilmek için kullanılır. “Ls –a” komutunu kullanarak ta tüm gizli dosyaları görebilirsiniz.

![Yeni Başlayanlar için Basit Linux Komutları](https://aktif.net/files/images/news/basit-linux-komutlari-3.png)

Şekil 2: ls komutu çıktısı.

### 3. cd

“cd”, bir dizine gitmek için kullanılan komuttur. Örneğin, Home klasöründeyseniz ve Downloads klasörüne gitmek istiyorsanız, “cd Downloads” yazabilirsiniz. Unutmayın ki bu komut büyük / küçük harfe duyarlıdır ve klasörün adını tam olarak olduğu gibi yazmanız gerekir. Bulunduğunuz klasörden geri dönmek veya bir üst klasöre çıkmak istiyorsanız “cd ..” komutu kullanılır.

![Yeni Başlayanlar için Basit Linux Komutları](https://aktif.net/files/images/news/basit-linux-komutlari-4.png)

Şekil 3: cd komutu çıktısı.

### 4. mkdir & rmdir

“mkdir” komutu, bir klasör veya dizin oluşturmanız gerektiğinde kullanılır. Örneğin “ TEST” adlı bir dizin yapmak istiyorsanız “mkdir TEST” komutunu yazabilirsiniz. “rmdir” bir dizini silmek için kullanılan komuttur. Ancak, rmdir yalnızca boş bir dizini silmek için kullanılabilir. İçi dolu bir klasörü silmek istiyorsanız komutu “rm –r klasörünadı” şeklinde kullanmanız gerekir.

![Yeni Başlayanlar için Basit Linux Komutları](https://aktif.net/files/images/news/basit-linux-komutlari-5.png)

Şekil 4: mkdir & rmdir komutu çıktısı.

### 5. touch

“touch” komutu bir dosya yaratmak için kullanılır. Bu dosya herhangi bir şey olabilir. Örneğin bir zip dosyası ya da txt dosyasını aynı komutla yaratabilirsiniz.

![Yeni Başlayanlar için Basit Linux Komutları](https://aktif.net/files/images/news/basit-linux-komutlari-6.png)

Şekil 5: mkdir & rmdir komutu çıktısı.

### 6. man & -help

Bir komutun nasıl kullanılacağını ve hakkında daha fazla bilgi edinmek için man komutu kullanılır. Örneğin, “man touch” touch komutunun manuel sayfalarını gösterir. Bir komutu yazıp arkasına “–help” eklersek, yine manual çıktısı ile aynı sonuca ulaşırız.

![Yeni Başlayanlar için Basit Linux Komutları](https://aktif.net/files/images/news/basit-linux-komutlari-7.png)

Şekil 6: man & -help komutu çıktısı.

### 7. cp

Cp komutu, komut satırı üzerinden kopyalama yapmak için kullanılır. İki argüman alır; ilki kopyalanacak dosyanın konumu, ikincisi kopyalanacak yerdir.

![Yeni Başlayanlar için Basit Linux Komutları](https://aktif.net/files/images/news/basit-linux-komutlari-8.png)

Şekil 7: cp komutu çıktısı.

### 8. mv

Mv komutu, dosyaları komut satırı yoluyla taşımak için kullanılır. Bir dosyayı yeniden adlandırmak için mv komutunu da kullanabiliriz. Örneğin az önce kopyaladığımız “copytest.txt” d0syasının ismini “newcopytest.txt” olarak değiştirmek istiyoruz. “mv copytest.txt newcopytest.txt” komutu ile bu işlemi gerçekleştirebiliriz.

![Yeni Başlayanlar için Basit Linux Komutları](https://aktif.net/files/images/news/basit-linux-komutlari-9.png)

Şekil 8: mv komutu çıktısı.

### 9. nano & vi

nano ve vi, Linux komut satırı üzerinde hali hazırda yüklü olan metin düzenleyicilerdir. Nano, renkli anahtar kelimeleri gösteren ve dillerin çoğunu tanıyan iyi bir metin editörüdür. Vi, nano’dan daha basittir. Bu komutla yeni bir dosya oluşturabilir veya bu düzenleyiciyi kullanarak dosyayı değiştirebilirsiniz.

![Yeni Başlayanlar için Basit Linux Komutları](https://aktif.net/files/images/news/basit-linux-komutlari-10.png)

Şekil 9: nano komutu çıktısı.

### 10. sudo

Sudo, Linux komut satırında yaygın olarak kullanılan bir komuttur. Sudo, “SuperUserDo” kelimesinden gelir. Bu komutu yapılacak bir işlemde kök ayrıcalıkları kullanmak istersek veya idari bir yapıyla erişim gerekiyorsa kullanabiliriz. Örneğin “sudo su” komutunu kullanarak sistemde admin yetkisi ile işlem yapmaya başlayabiliriz.

![Yeni Başlayanlar için Basit Linux Komutları](https://aktif.net/files/images/news/basit-linux-komutlari-11.png)

Şekil 10: sudo komutu çıktısı.


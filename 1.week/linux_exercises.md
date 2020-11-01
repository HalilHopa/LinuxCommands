# 	Linux Example 

1- My_script adında bir dosya oluşturunuz. İçine "Hello , I am learning Bash Script" yazıp , oluşturduğunuz dosyayı shellde yazdırınız.

2-  Linux komut satırında gerekli komutları kullanarak bir klasör oluşturunuz ve oluşturduğunuz klasöre komut satırından erişip görüntüleyiniz.

3- Linux komut satırından  desktop klasörünün içerisinde "file" kelimesi geçen dosyaları listeleyiniz.

Örnek:

```bash
find <startingdirectory> <options> <search term>
```

4-Linux komut satırından bir dosyaya gidip 2-3 dosyayı .tar dosyasında sıkıştırınız ve .tar dosyasında sıkıştırılan dosyaları listeleyip , bu dosyaları .tar dan unzip yap çıkarınız.

5-Linux komut satırında çalıştığınız son 10 kodu yazdırınız.

6-  Linux komut satırında NewFile diye bir klasör oluşturup içerisine myText adlı bir dosya ekleyiniz. Oluşturduğunuz myText i silip, tekrar desktop dizinine gelip en son oluşturduğunuz klasörü siliniz.

7-Linux komut satırında  oldFile ve path isminde iki klasör oluşturunuz, oldFile klasörünü path klasörünün içine atıp path dizinine giriniz. oldFile dosyasının adını myFile olarak değiştiriniz.

8- Linux komut satırında bulunduğunuz dizini listeleyiniz.

9-  Linux komut satırında gerekli olan komutları kullanarak herhangi bir komutu bir değişkene atayıp yazdırınız.

Örnek : 

```bash
alias cls=clear #clear komutunu cls olarak isimlendirmiş olduk.
```

10-  Linux komut satırından herhangi bir dosyanın içine gidip dosyanın izinlerini değiştiriniz.

11- Linux komut satırından herhangi bir dosyanın path'ini (yolunu) yazdırınız.

12- Linux komut satırından gerekli komutları kullanarak "examples "adlı bir klasör oluşturunuz. Oluşturduğunuz dosyanın altında "2020" adlı yeni bir dizin oluşturunuz.

13- Linux komut satırında "touch" komutunu kullanarak yeni bir directory oluşturup içine hello.text adında bir dosya ekleyip yazdırınız.

Örnek:

```bash
touch Deneme/Ornek.txt
```

14-  13. soruda oluşturduğunuz dosyayı gerekli komutlar kullanarak aynı dizin içerisinde kopyalayınız.

15- Linux komut satırından "Deneme" adında bir dosya oluşturunuz. Oluşturduğunuz dosyanın içeresine hi.text adında bir dosya ekleyip gerekli komutlarla bu dosyanın ismini değiştiriniz.

16- Linux komut satırından oluşturduğunuz bir dosyanın izinlerini root olarak değiştiriniz.

17- Linux komut satırından oluşturduğunuz bir dosyanın izinlerini sadece okuma olarak değiştiriniz.

18- Linux komut satırından geçerli olan dizini yazdırınız.

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



20- Linux komut satırında çalıştığınız penceredeki tüm komutları temizleyiniz.

21- Linux komutlarını kullanarak nano komutunun yüklü olduğunu kontrol ediniz.Ardından bir nano editörü açıp

 "Hello , I am learning Bash Script" yazıp dosyayı kaydediniz.

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

22- Linux komutlarıyla vi dosyası oluşturup içine "Hello , I am learning linux" yazıp kayıt ediniz ve yazdırınız.

23- Linux komutlarıyla yeni bir kullanıcı oluşturun ve ön tanımlı ayarlarını değiştiriniz.

24- Usermod kullanarak oluşturduğunuz yeni kullanıcıyı düzenleyiniz.

25- Linux komutlarını kullanarak home dizinine gidip bir directory oluşturunuz. Bu directory içine localden kişisel bir kaç dosyanızı yükleyiniz.Burdaki dosyayı herhangi bir dizine yönlendirip rapor.txt dosyası oluşturunuz.

26-Desktopta bir text dosyası oluşturunuz.Linux komut satırından bu dosyanın son 10 satırını yazdırınız.

27-Linux komut satırından yum komutunu kullanarak bilgisayarınızda yüklü olmayan bir uygulamayı kurunuz.

Örnek:

yum install firefox

28- yum komutunu kullanarak bilgisayarınızda yüklü olan bir uygulamayı siliniz.

Örnek:

yum remove firefox

29-Linux komut satırından belirlediğiniz 5 adet process komutuyla ilgili işlem yapınız.

30- Aşağıda verilen bütün komutlarla ilgili işlemler yapınız ve komutların ne işe yaradıklarını bir text dosyasına yazınız.
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
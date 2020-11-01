# SORULAR
1. Her 2 dakikada bir çalışacak bir script yazınız. Script aşağıdaki işleri yapmalıdır.
- Postgresql traindb veri tabanında users adında bir tablo olup olmadığını kontrol etsin. 
- users tablosu yok ise oluştursun.
- users tablosu şeması id, name, age şeklindedir.
- Her 2 dakikada bir bu tabloya bir kayıt girsin.
- Girilen kayıtta id yerine o anki saat-dakika-saniyeden oluşan sayı örneğin 143221, name yerine sanal makinenin adını, age yerine kayıt anındaki dakikayı girsin.
- Script stdin, stderr sonuçlarını <scriptadı_logs.log> adında bir dosyaya loglasın.
- 15 dakika boyunca bu görevi açık tutunuz daha sonra kapatınız.
- 15 dakika sonunda tablo içeriğini select komutu ile gösteriniz.

10-15 dk sonunda örnek tablo sorgu sonucu aşağıdaki gibi olmalıdır:
```
   id   |         name          | age
--------+-----------------------+-----
 145402 | localhost.localdomain |  54
 145601 | localhost.localdomain |  56
 145801 | localhost.localdomain |  58
 150002 | localhost.localdomain |   0
 150201 | localhost.localdomain |   2
 150401 | localhost.localdomain |   4
```

2. https://github.com/erkansirin78/datasets/tree/master/retail_db
adresindeki csv dosyalarını retail adında bir veri tabanında oluşturacağınız tablolara kopyalayınız.
Tablo isimleri csv dosya isimleri ile aynı olmalıdır.
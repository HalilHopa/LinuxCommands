# SORULAR
1. Çalışan containerları listeleyiniz.

2. Çalışan ve durmuş containerları listeleyiniz.

3. httpd:alpine imajından detached bir container yaratınız. Bu containerı durdurup kaldırınız.

4. httpd:alpine imajından yeni bir container yaratın, adı apache olsun, ana işletim sisteminizin tarayıcısı (örneğin chrome) üzerinden localhost:8082 adresinden erişecek şekilde port yönlendirmesi yapın. localhost:8082 adresten eriştiğinizde gördüğünüz sonucu not edin.

5. Az önce yarattığınız apache isimli container loglarını inceleyiniz.

6. Az önce yarattığınız apache container web arayüzünde docker volume kullanmadan Hi there. I have changed this. Well done to me :) yazdırınız.

7. Az önceki apache isimli containerı siliniz.

8. Ana bilgisayar tarayıcısından localhost:8082 adresine girdiğinizde Hi there. I have changed this. Well done to me :) ibaresini docker volume kullanarak gösteriniz.

9. Web sayfasında adınızı soyadınızı yazan bir flask uygulaması yazın, bu uygulamayı Docker file ile imaj haline getirin. Dockerhub'a imajınızı push edin. Bu imajı kullanarak container yaratın ve tarayıcıdan erişerek adınızı soyadınızı tarayıcıda görün. 

10. jupyter/datascience-notebook:python-3.8.5 imajından bir jupyter notebook container oluşturunuz. Browser üzerinden 8888 portundan bu jupyter arayüze erişiniz. Basit bir notebook oluşturunuz. Containerı siliniz. Linux terminalden python virtual environment'ı aktif hale gitiriniz. Jupyter çalıştırınız. Container içinde ürettiğiniz notebook'u burada kullanınız.

11. https://github.com/erkansirin78/datasets/tree/master/retail_db adresindeki csv dosyalarını retail adında bir veri tabanında oluşturacağınız tablolara kopyalayınız. Tablo isimleri csv dosya isimleri ile aynı olmalıdır.
# git pratik komutlar

### git komutlarını .git dosyasının olduğu dizinde çalıştırmalısınız.

### Working directory -> staging area (Çalışmaları staging area'ya ekleme)
Yöntem-1: git add myfile   
Yöntem-2: git add .  
Yöntem-3: git add . --all   

### unstage: Staging area -> working directory (Staging area'ya yapılan eklemeleri geri alma)
Yöntem-1: git rm --cached myfile  
Yöntem-2: git reset

### Staging area -> Local repository (Staging area'dan local repository'e commit etmek)
git commit -m "myfile added"

### Local repository -> Staging area'ya dönmek (En son commit sonrası yapılan değişiklikleri geri almak)
git checkout -- myfile

### Local repository -> Staging area'ya dönmek (Geçmişteki bir commit'e geri dönmek)
Yöntem-1: git checkout a1ee838d83c myfile  (Belirgin bir dosya için)  
Yöntem-2: git checkout a1ee838d83c myfile  (Tüm dosyalar için)


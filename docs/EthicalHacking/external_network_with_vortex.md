# Vortex ile Dış Ağa Açılma

Bu notlar, **vtxhub.com** üzerinden bir sunucuyu dış dünyaya açmak için izlenen adımları özetler.

-----

## 1\. Kayıt İşlemleri

  * **vtxhub.com** adresine giderek siteye kaydolun.
  * Geçici bir e-posta adresi kullanmak isterseniz, **tempmail** gibi servislerden yararlanabilirsiniz.

## 2\. Yapılandırma Dosyasını İndirme

  * Siteye kaydolduktan sonra gerekli olan yapılandırma dosyasını indirin.
  * İndirdiğiniz bu sıkıştırılmış (`.zip`) dosyayı `unzip` komutuyla açın.

## 3\. Yapılandırma ve Kaydetme

  * Terminalde, indirdiğiniz dizin içinde şu komutu çalıştırın:
    ```bash
    ./vortex --save
    ```
  * Bu komut, gerekli bilgileri (`token`, `server`, vb.) girmenizi isteyecektir. Bilgileri girdikten sonra yapılandırma dosyası kaydedilir.

## 4\. Sunucu Yönlendirmesi

  * Artık bilgisayarınızda çalışan sunucunuzu (`localhost`) dış dünyaya yönlendirebilirsiniz.
  * Vortex, belirlediğiniz port ve adrese gelen trafiği yerel sunucunuza yönlendirerek dış ağdan erişim sağlar.
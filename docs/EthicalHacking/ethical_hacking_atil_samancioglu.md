# Etik Hacking ve Linux Temelleri

---

## Linux Dizin Yapısı

Linux'un dosya sistemi, her bir dizinin belirli bir amaca hizmet ettiği hiyerarşik bir yapıya sahiptir.

* **`/bin`**: Temel kullanıcı komutları burada bulunur. (`ls`, `cp`, `mv` gibi).
* **`/dev`**: Sistemdeki donanım aygıtları, dosyalar gibi görünür ve burada yer alır.
* **`/etc`**: Sistem çapında yapılandırma (`configuration`) dosyaları bu dizindedir.
* **`/var`**: Loglar, yedekler ve web sunucusu dosyaları gibi sürekli değişen verileri içeren dizindir.
* **`/tmp`**: Geçici dosyalar için ayrılmış bir alandır. Genellikle sistem yeniden başlatıldığında içeriği silinir.
* **`/home`**: Her kullanıcının kişisel klasörü burada bulunur.
* **`/root`**: Sistemdeki en yetkili kullanıcı olan `root` kullanıcısının ana dizinidir.
* **`/mnt`**: Geçici olarak bağlanmış (`mount`) dosya sistemleri için kullanılır.
* **`/media`**: CD, DVD veya USB bellek gibi harici medyaların otomatik olarak bağlandığı dizindir.
* **`/boot`**: İşletim sistemini başlatmak için gerekli olan dosyaları içerir.
* **`/srv`**: Sunulan servislerin verileri burada bulunur.
* **`/usr`**: Kullanıcıya ait programlar ve kütüphanelerin bulunduğu ana dizinlerden biridir.
* **`/lib`**: Sistem kütüphaneleri ve çekirdek modüllerinin tutulduğu dizindir.

---

## Nano ve Wireshark

* **Nano**: Kullanımı kolay bir komut satırı metin düzenleyicisidir.
    * **`Ctrl + O`**: Dosyayı kaydeder.
    * **`Ctrl + K`**: Seçili satırı keser.
* **Wireshark**: Bir ağ paket analiz aracıdır. Bulunulan ağdaki tüm gelen ve giden paketleri yakalamak, görüntülemek ve detaylı olarak incelemek için kullanılır. Bu, ağ trafiği sorunlarını gidermek veya güvenlik analizleri yapmak için vazgeçilmez bir araçtır.

---

## Sızma Testi Araçları ve Güvenlik Notları

* **Wi-Fi Kartı**: Linux'a bir Wi-Fi kartı bağlamak, ağları denetlemek ve sızma testleri yapmak için ilk adımlardan biridir.
* **FatRat**: Bir arka kapı (`backdoor`) oluşturma aracıdır.
* **Güvenlik Uyarısı**: Oluşturulan zararlı yazılımları (`backdoor`) **VirusTotal** gibi herkese açık platformlarda test etmek, kodun imzasını güvenlik firmalarına ifşa edebilir. Bu nedenle, bu tür dosyalar için **Nodistribute** gibi gizliliği koruyan platformlar tercih edilmelidir.
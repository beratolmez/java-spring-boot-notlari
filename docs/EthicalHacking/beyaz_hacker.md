# Beyaz Şapkalı Hacker Ders Notları

---

## Sistem ve Kullanıcı Bilgileri

* **`apropos ls`**: İçerisinde `ls` kelimesi geçen tüm komutları ve araçları listeler.
* **`lsb_release -a`**: Sisteminizin dağıtımı hakkında ayrıntılı bilgiler (dağıtım adı, sürüm numarası vb.) verir.
* **`cat /etc/issue`**: Sistemin dağıtım adını ve versiyonunu okumak için kullanılır.
* **`uname`**: İşletim sisteminizin çekirdek adını ve diğer temel bilgilerini gösterir.
* **`w`**: Sisteme kimlerin giriş yaptığını, ne kadar süredir aktif olduklarını ve ne yaptıklarını gösteren özet bir rapor sunar.
* **`whoami`**: O an hangi kullanıcı hesabıyla işlem yaptığınızı gösterir.
* **`uptime`**: Sistemin ne kadar süredir çalıştığını (açık olduğunu) ve sistem yükü ortalamasını gösterir.
* **`top`**: Aktif olarak çalışan süreçleri ve bu süreçlerin CPU, bellek gibi kaynak kullanımını canlı olarak gösterir. Bu komut, kaynak tüketen uygulamaları tespit etmek için idealdir.
* **`ps`**: O an çalışan süreçleri listeler.
* **`pstree -p`**: Çalışan süreçleri ağaç yapısında, yani hiyerarşik bir şekilde gösterir.
* **`kill`**: Belirtilen bir sürecin (`process`) kimlik numarası (`PID`) ile o süreci sonlandırmaya yarar.

---

## Dosya Sistemi Yönetimi

* **`touch`**: İçeriği boş olan yeni bir dosya oluşturur.
* **`echo`**: Belirtilen metni terminale veya bir dosyaya yazar.
* **`more`**: Dosya içeriğini sayfa sayfa görüntülemek için kullanılır.
* **`less`**: `more`'dan daha gelişmiş bir dosya görüntüleyicisidir. Hem ileri hem de geri yönde hareket etmeye olanak tanır.
* **`grep`**: Dosya veya veri akışı içinde belirli bir metin kalıbını aramak ve filtrelemek için kullanılır.
* **`fdisk -l`**: Disk bölümlerinin (`partition`) tablosunu listeler. Disklerinizi yönetmek için kullanılır.
* **`df`**: Dosya sistemindeki toplam alanı ve kullanılan/kalan alanı gösterir.
* **`mount`**: SD kart, USB bellek veya DVD gibi harici depolama birimlerini dosya sistemine bağlar.

---

## Dosya Sıkıştırma ve Arşivleme

* **`tar`**: Birden fazla dosya ve klasörü tek bir arşiv dosyası içinde birleştirmek için kullanılır.
    * **`tar -cf deneme.tar ./*`**: Bulunulan dizindeki tüm dosyaları sıkıştırmadan `deneme.tar` adlı bir arşivde toplar.
    * **`tar -xf deneme.tar`**: Bir arşiv dosyasını dışarı çıkarır.
    * **`tar -zcf deneme.tar.gz ./*`**: `gzip` kullanarak sıkıştırılmış bir tar arşivi oluşturur.
* **`gzip`**: Dosyaları sıkıştırmak için kullanılır.
    * **`gzip -9 deneme.txt`**: `deneme.txt` dosyasını en yüksek sıkıştırma seviyesiyle sıkıştırır.
* **`gunzip`**: `.gz` uzantılı sıkıştırılmış dosyaları açar.
* **`bzip2`**: `gzip`'ten daha yüksek sıkıştırma oranı sunan bir sıkıştırma aracıdır.
* **`bunzip`, `unzip`**: Sıkıştırılmış dosyaları dışarı çıkarmak için kullanılan araçlardır.

---

## Kullanıcı ve Yetki Yönetimi

* **`usermod -L kullanici`**: Belirtilen kullanıcının hesabını kilitler (`Lock`), yani pasif hale getirir.
* **`usermod -U kullanici`**: Kilitlenen bir kullanıcı hesabını açar (`Unlock`), yani aktif hale getirir.
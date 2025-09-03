# Linux Kullanıcı Komutları

---

## Kullanıcı ve Grup Yönetimi

### Kullanıcı Oluşturma
* `useradd -m <kullanıcı_adı>`: Yeni bir kullanıcı oluşturur ve aynı isimde bir **home dizini** (`-m` argümanı sayesinde) otomatik olarak yaratır.
* **Örnek:** `useradd -m zeynep`

### Kullanıcıya Şifre Verme
* `passwd <kullanıcı_adı>`: Belirtilen kullanıcı için şifre belirlemenizi sağlar.
* **Örnek:** `passwd zeynep`

### Grup Oluşturma
* `groupadd <grup_adı>`: Yeni bir grup oluşturur.
* **Örnek:** `groupadd hadoop`

### Kullanıcıyı Gruba Ekleme
* `usermod -aG <grup_adı> <kullanıcı_adı>`: Mevcut bir kullanıcıyı bir gruba ekler. `-aG` argümanı, kullanıcının mevcut gruplarını koruyarak yeni bir gruba ekler.
* **Örnek:** `usermod -aG hadoop zeynep`

### Kullanıcıya Yönetici Ayrıcalıkları Verme
* `usermod -aG sudo <kullanıcı_adı>`: Kullanıcıyı **`sudo`** grubuna ekleyerek yönetici ayrıcalıkları verir. Böylece kullanıcı, `sudo` komutuyla diğer komutları root yetkisiyle çalıştırabilir.
* **Örnek:** `sudo usermod -aG sudo zeynep`

---

## Kullanıcı ve Grup Bilgilerini Sorgulama

* `ls /home`: Home dizinindeki tüm kullanıcıların dizinlerini listeler.
* `grep <grup_adı> /etc/group`: Belirtilen grubun kullanıcılarını listeler. Bu komut, bir kullanıcının bir gruba eklenip eklenmediğini kontrol etmek için kullanışlıdır.
* **Örnek:** `grep hadoop /etc/group`
* `cat /etc/passwd`: Sistemdeki tüm kullanıcıları listeler.
* `cat /etc/passwd | grep <kullanıcı_adı>`: Mevcut kullanıcılar arasında arama yapmak için kullanılır.
* `id <kullanıcı_adı>`: Bir kullanıcının sistemde var olup olmadığını kontrol eder ve kullanıcı kimlik (UID) ve grup kimlik (GID) bilgilerini gösterir.

---

## Kullanıcı Silme

* `userdel <kullanıcı_adı>`: Kullanıcıyı siler.
* `userdel -r <kullanıcı_adı>`: Kullanıcıyı silerken **home dizinini** ve **mail spool** gibi ilgili dosyalarını da siler.

---

## SSH Bağlantısı İçin Kullanıcıya Yetki Verme

* `usermod -a -G sshusers <kullanıcı_adı>`: Kullanıcıyı **`sshusers`** grubuna ekleyerek uzaktan SSH bağlantısı kurmasına izin verir. Bu adım, SSH konfigürasyonuna bağlı olarak gerekebilir.
* **Örnek:** `usermod -a -G sshusers zeynep`

---

## Sudo Hatası Çözümü

* **Hata:** `user is not in the sudoers file. This incident will be reported.`
* **Çözüm:** Bu hata, kullanıcının `sudoers` dosyasında tanımlı olmamasından kaynaklanır. Çözüm için kullanıcıyı `sudo` grubuna eklemeniz gerekir:
    * `usermod -aG sudo <kullanıcı_adı>`
* **Alternatif:** Veya `echo "<kullanıcı_adı> ALL=(ALL) ALL" >> /etc/sudoers` komutunu root kullanıcısı olarak çalıştırarak kullanıcıyı `sudoers` dosyasına doğrudan ekleyebilirsiniz.
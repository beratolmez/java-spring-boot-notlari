# Steganografi: Verileri Gizleme Sanatı

Steganografi, bir bilginin varlığının dahi fark edilmemesi için, onu başka bir mesaj veya nesne içerisine gizleme yöntemidir. Metin, resim, video veya ses gibi hemen hemen her türlü dijital içerik, gizli verileri taşımak için kullanılabilir.

---

## Steganografi Araçları ve Kullanımı

### Steghide (JPEG Dosyaları İçin)

`Steghide`, JPEG dosyalarında veri gizleme ve çıkarma için popüler bir araçtır.

* **Kurulum:** `apt install steghide`
* **Veri Gizleme:** `steghide embed -ef [gizlenecek_dosya] -cf [ana_dosya].jpeg -p [parola]`
* **Veri Çıkarma:** `steghide extract -sf [gizlenmiş_dosya].jpeg -p [parola]`
    * **Örnek:** `steghide extract -sf jpeg1.jpeg -p password123` komutu, `jpeg1.jpeg` dosyasından parolayla korunan gizli veriyi çıkarır.

### Stegcracker (Steganografi Şifresi Kırma)

`Stegcracker`, şifre korumalı steganografik dosyaların parolasını kaba kuvvet saldırısı (`brute force`) ile kırmak için kullanılır.

* **Kurulum:** `pip3 install stegcracker`
* **Kullanım:** `stegcracker [gizli_veri_dosyası] [wordlist_dosyası]`
    * **Örnek:** `stegcracker jpeg1.jpeg /usr/share/wordlists/rockyou.txt` komutu, `rockyou.txt` dosyasındaki şifreleri deneyerek `jpeg1.jpeg` dosyasının parolasını bulmaya çalışır.

### Zsteg (PNG ve BMP Dosyaları İçin)

`Zsteg`, özellikle PNG ve BMP dosyalarındaki gizli verileri tespit etmek için kullanılır.

* **Kurulum:** `gem install zsteg`
* **Önemli Parametreler:**
    * `--lsb`: En az önemli biti (`Least Significant Bit`) inceler.
    * `--msb`: En çok önemli biti (`Most Significant Bit`) inceler.
    * `-v`: Detaylı çıktı verir.
    * `-E`: Belirli bir yükü (`payload`) çıkarmak için kullanılır.
* **Kullanım:** `zsteg png1.png` komutu, `png1.png` dosyasında gizlenmiş verileri tespit etmeye çalışır.

---

## Ekstraksiyon ve Analiz Araçları

### ExifTool (Meta Veri Analizi)

`ExifTool`, resim ve diğer medya dosyalarındaki meta verileri görüntülemek ve düzenlemek için kullanılan güçlü bir araçtır. Steganografik veriler genellikle meta veri alanlarına gizlenebilir.

* **Kurulum:** `apt install exiftool`
* **Kullanım:** `exiftool jpeg1.jpeg`

### StegoVeritas (Çoklu Dosya Formatı Analizi)

`StegoVeritas`, birçok dosya formatında steganografik veriyi analiz etmek için kullanılan çok yönlü bir araçtır.

* **Kurulum:** `pip3 install stegoveritas`
* **Önemli Parametreler:**
    * `-meta`: Dosyanın meta verilerini kontrol eder.
    * `-steghide`: Dosyada `Steghide` ile gizlenmiş veri olup olmadığını kontrol eder.
    * `-extractLSB`: LSB (En az önemli bit) verilerini çıkarmaya çalışır.
* **Kullanım:** `stegoveritas jpeg1.jpeg` komutu, analiz sonuçlarını `results` adlı bir klasörde toplar.

---

## Ses Dosyalarında Steganografi (Spectrogram)

Ses dosyaları, sesin grafiksel gösterimi olan **spektrogramlar** aracılığıyla görsel olarak gizli veriler içerebilir.

* **Sonic Visualiser (Analiz İçin):**
    * **Kurulum:** `apt install sonic-visualiser`
    * **Kullanım:** Uygulama başlatılır, ses dosyası açılır ve `Layer > Add Spectogram` seçeneğiyle gizlenmiş veriler görsel olarak incelenir.
* **Coagula (Gizleme İçin):**
    * `Coagula`, metin veya resimleri ses dosyalarına dönüştürerek gizli veri içeren spektrogramlar oluşturmaya yarayan bir araçtır. Mesaj arayüze girilir, `Render` edilip kaydedilir.
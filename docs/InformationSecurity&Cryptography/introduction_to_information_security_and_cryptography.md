# Bilgi Güvenliği ve Kriptografi

---

## Sonlu Cisimler (Finite Fields)

**Sonlu Cisimler (Galois Cisimleri)**, matematiksel olarak toplama, çıkarma, çarpma ve bölme işlemlerinin yapılabildiği, sonlu sayıda elemandan oluşan kümelerdir. Modern kriptografide, özellikle **AES** ve **Eliptik Eğri Kriptografisi (ECC)** gibi algoritmaların temelini oluştururlar.

* **Cisim:** Toplama ve çarpmaya göre tersi alınabilen bir cebirsel yapıdır.
    * Toplama işlemine göre tersi: `-a` veya `m - a`
    * Çarpma işlemine göre tersi: `a^-1` (`a * a^-1 = 1 mod m`)
* **İlkel Eleman:** Bir cismin tüm elemanlarını üretebilen elemandır.
* `GF(2)`: İki elemanlı (0 ve 1) sonlu cisimdir. İşlemleri `XOR` mantığına benzer şekilde çalışır.

### GCD (En Büyük Ortak Bölen)
İki sayının en büyük ortak bölenini bulmak için kullanılan bir algoritmadır.

* **Örnek:** `gcd(540, 168)`
    `gcd(540, 168) = gcd(168, 36) = gcd(36, 24) = gcd(24, 12) = 12`

### Euler Fonksiyonu
Bir sayıya kadar olan, o sayı ile aralarında asal olan sayıların sayısını bulur.

* **Örnek:** 60 ile aralarında asal olan sayıların sayısı
    `60 = 2^2 * 3^1 * 5^1`
    `(2^2 - 2^1) * (3^1 - 1) * (5^1 - 1) = 16`

---

## Şifreleme Algoritmaları ve Kriptografik Özellikler

### Simetrik Şifreleme
Simetrik şifreleme algoritmalarında, şifreleme ve şifre çözme için aynı anahtar kullanılır.

* **Blok Şifreler:** Veriyi küçük, sabit boyutlu bloklar halinde şifreler.
    * **Feistel Ağları:** Veri bloğunu ikiye bölerek çalışan bir yapıdır. **DES** bu yapıyı kullanır.
    * **SPN (Substitution-Permutation Network):** Veri üzerinde dönüşümler ve permütasyonlar yaparak şifreleme sağlar. **AES** bu yapıyı kullanır.
* **S-Kutuları (S-Boxes):** Simetrik şifreleme algoritmalarında doğrusal olmayan dönüşümler sağlamak için kullanılan anahtar bileşenlerdir.

### AES (Advanced Encryption Standard)
* **Blok Boyutu:** Sabit 128 bit.
* **Anahtar Uzunluğu:** 128, 192 veya 256 bit. Anahtar uzunluğu tur sayısını belirler.
    * 128 bit için 10 tur
    * 192 bit için 12 tur
    * 256 bit için 14 tur
* **Mimarisi:** SPN (Substitution-Permutation Network)
* **Döngü İşlemleri:**
    1.  `SubBytes` (Bayt Değiştirme)
    2.  `ShiftRows` (Satır Kaydırma)
    3.  `MixColumns` (Sütun Karıştırma) - **Son turda bu işlem yapılmaz.**
    4.  `AddRoundKey` (Anahtar Ekleme)

### DES (Data Encryption Standard)
* **Blok Boyutu:** 64 bit.
* **Anahtar Uzunluğu:** 56 bit (8 bit hata kontrolü için ayrılır).
* **Mimarisi:** Feistel
* **Güvenlik:** Kısa anahtar boyutu nedeniyle günümüzde güvenli kabul edilmez.

| Özellik | DES | AES |
| :--- | :--- | :--- |
| **Blok Boyutu** | 64 bit | 128 bit |
| **Anahtar Uzunluğu** | 56 bit | 128, 192 veya 256 bit |
| **Yapı** | Feistel | Substitution-Permutation |
| **Güvenlik** | Düşük (kırılabilir) | Yüksek (kırılması zor) |

---

## Bilgi Güvenliğinin Hedefleri

Bilgi güvenliği, veriyi koruma altına almak için belirli hedefler üzerine kurulmuştur:

* **Gizlilik (Confidentiality):** Yetkisiz erişime karşı verinin korunması.
* **Bütünlük (Integrity):** Verinin yetkisiz değişikliklere karşı korunması.
* **Süreklilik (Availability):** Yetkili kullanıcıların verilere erişebilmesi.
* **Kimlik Denetimi (Authentication):** Bir kullanıcının kimliğinin doğrulanması.
* **İnkar Edilemezlik (Non-Repudiation):** Yapılan bir işlemin sonradan reddedilememesi.
* **İzlenebilirlik (Accountability):** Sistemdeki eylemlerin takibi ve denetlenmesi.
# Kablosuz Ağlara Giriş

* **Anten:** Ters üçgen (△) ile sembolize edilir.
* **Line of Sight (LOS):** Doğrudan görüş hattı anlamına gelir.

---

## Kablosuz Ortam (Wireless Environment)

* Bu ortamda sinyal iletimi sırasında karşılaşılan zorluklar mevcuttur.

## Mobil Radyo Evrim Yolu (Evolution PATH of Mobile Radio)

* **Boyutlandırma:** Makro hücrelerden (geniş alan) Piko hücrelere (küçük alan) doğru bir küçülme söz konusudur.

---

## Sinyal Yayılımı (Propagation)

* **Fading (Solma):** Sinyalin gücündeki dalgalanmalardır, **multipath** (çoklu yol) yayılımının bir sonucudur.
* **Path Loss (Yol Kaybı):** Sinyalin yayıldıkça gücünü kaybetmesi.
* **Ground Reflection (Yer Yansıması):** Sinyalin yerden yansıyarak ek yollar oluşturması.
* **Diffraction (Kırınım):** Sinyalin bir engelin etrafından bükülerek yayılması.

---

## Anten ve Sinyal

* Sinyal iletimi için **anten boyutu** önemlidir. Anten boyu, sinyal **dalga boyu** ($\lambda$) ile ilişkilidir. Genellikle anten boyu $\lambda / 10$ civarındadır.
* **Desibel (dB):** Logaritmik bir ölçüm birimidir.
* **dBm:** Gücün desibel cinsinden miliwatt'a göre ifadesidir.

---

## Sinyal Paraziti ve Çözümleri

* **Near-Far Effect:** Yakındaki bir istasyonun fazla güçle yayın yapması, **parazit (interference)** oluşturur. Bu durum, uzaktaki istasyonlarla iletişimi zorlaştırır veya engeller.
* Bu etki, sistem kapasitesini etkilemez.

### Terimler

* **Cluster (Küme):** Hücrelerden oluşan bir gruptur.
* **Frequency Reuse (Frekansın Yeniden Kullanımı):** Aynı frekansların farklı coğrafi bölgelerde tekrar kullanılmasıdır.

### Parazit Türleri

* **Co-channel Interference:** Aynı frekans kanalını kullanan diğer hücrelerin yarattığı parazittir.
    * **Çözüm:** Aynı kanalı kullanan hücreler arasındaki mesafeyi artırmak.
* **Adjacent Channel Interference:** Bitişik frekans kanallarının yarattığı parazittir.
    * **Çözüm:** Farklı frekans aralıklarında uygun ayarlamalar yaparak bu paraziti azaltmak.
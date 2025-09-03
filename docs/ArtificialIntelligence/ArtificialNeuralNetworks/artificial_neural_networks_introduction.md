# Nöron Ağlarına Giriş

**Yapay sinir ağları**, insan beynindeki nöronların çalışma prensibini taklit ederek oluşturulmuş hesaplama sistemleridir.

---

## Yapay Nöronun Yapısı

Bir yapay nöronun temel işleyişi şu adımlardan oluşur:

1.  **Ağırlıklı Girişlerin Hesaplanması:** Nöron, gelen her bir girdiyi kendi ağırlık değeriyle çarpar.
2.  **Eşik Değerinin Uygulanması:** Toplanan ağırlıklı girdiler, bir **eşik aktivasyon fonksiyonu** kullanılarak işlenir. Bu mekanizma aynı zamanda **Eşik Mantık Ünitesi (TLU - Threshold Logic Unit)** olarak da adlandırılır.

### Ağırlık Vektörü ve Karar Sınırı

* **Ağırlık Vektörü:** Karar sınırına (karar düzlemine) dik olmalıdır.
* Ağırlık vektörünün yönü, pozitif çıktılar üretecek vektörlerin hangi tarafta olacağını belirler. Bu sayede, pozitif çıktılı vektörler karar sınırının bir tarafında, negatif çıktılılar ise diğer tarafında kalır.
* **Eğilim (Bias):** Karar sınırının uzaydaki konumunu belirler. Karar sınırını bulmak için `wp + b = 0` denklemi çözülür.

**Not:** `wij` notasyonu, `i` ve `j` nöronları arasındaki ağırlıklı bağlantıyı ifade eder.

---

## Nöronun Fonksiyonları

Bir nöronun temel işlevleri üç ana fonksiyonda özetlenebilir:

1.  **Yayılım Fonksiyonu:** Nöronun tüm girdilerini ve ağırlıklarını kullanarak **net girdiyi (net input)** hesaplar.
2.  **Aktivasyon Fonksiyonu:** Hesaplanan net girdiyi işleyerek nöronun ne kadar etkin olacağını belirler.
3.  **Çıktı Fonksiyonu:** İşlenmiş net girdi değerine göre nöronun nihai çıktısını üretir.
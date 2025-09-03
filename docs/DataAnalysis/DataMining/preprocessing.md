# Veri Ön İşleme (Data Preprocessing)

Veri ön işleme, ham verinin analiz ve makine öğrenmesi modelleri için daha uygun hale getirilmesi sürecidir.

---

## Veri Kalitesini Etkileyen Faktörler

* **Doğruluk (Accuracy):** Verilerin doğru ve hatasız olması.
* **Tutarlılık (Consistency):** Aynı verinin farklı yerlerde aynı şekilde ifade edilmesi.
* **Tam Olma Durumu (Completeness):** Veri kümesinde eksik değerlerin olmaması.
* **Güvenirlik (Reliability):** Verilerin kaynağının güvenilir olması.
* **Tahmin Edilebilirlik (Predictability):** Verilerin gelecekteki davranışları tahmin etmede kullanılabilir olması.

### Zayıf Veri Kümesi Özellikleri
* **Gürültü (Noise):** Rastgele hatalar veya varyanslar.
* **Eksik Veriler (Missing Data):** Bazı değerlerin boş olması.
* **Tekrarlı Veriler (Duplicate Data):** Aynı kaydın birden fazla kez bulunması.
* **Yanlış Veriler (Incorrect Data):** Hatalı veya geçerliliği olmayan değerler.

---

## Veri Ön İşleme Yöntemleri

### Eksik Verileri Yönetme
1.  **Göz ardı etme (Ignoring):** Eksik verileri içeren satırları veya sütunları tamamen silme.
2.  **Elle doldurma (Manual filling):** Uzman bilgisiyle eksik verileri manuel olarak girme.
3.  **Global değişken kullanma:** Tüm eksik değerleri sabit bir global değerle (örn: `0` veya `bilinmiyor`) değiştirme.
4.  **Merkezi bir ölçü ile değiştirme:** Eksik verileri o sütunun ortalaması, medyanı veya modu ile değiştirme.
5.  **Aynı sınıfa ait merkezi bir ölçü ile değiştirme:** Sadece aynı sınıfa ait verilerin ortalaması veya medyanı ile değiştirme.
6.  **Olası bir değer ile değiştirme:** Regresyon veya makine öğrenmesi algoritmaları kullanarak eksik değerleri tahmin etme.

### Veri Dönüşümleri

#### Birleştirme (Integration)
* Birden fazla özelliği tek bir özellik altında toplama.
* **Örnek:** "Gün" ve "Saat" özelliklerini tek bir "Tarih" özelliği olarak birleştirme.

#### Özellik İndirgemesi (Feature Reduction)
* Gereksiz özelliklerden kurtularak veri boyutunu azaltma.
* **Amaçlar:** Zaman kaybını önlemek, görselleştirmeyi kolaylaştırmak ve model performansını artırmak.
* **Teknik:** **Birincil Etken Analizi (PCA)** gibi yöntemler kullanılır.

#### Kesikli Hale Getirme (Discretization)
* Sürekli verileri (örn: yaş, gelir) belirli aralıklara bölerek kategorik verilere dönüştürme.
* **Kullanım Alanı:** Özellikle sınıflandırma algoritmalarında kullanılır.

#### İkili Sisteme Çevirme (Binarization)
* Sürekli veya kategorik değişkenleri `0` ve `1` gibi ikili değerlere dönüştürme.
* **Kullanım Alanı:** Genellikle birliktelik kuralları (association rules) için yapılır.

#### Normalizasyon (Normalization)
* Özelliklerin değerlerini belirli bir aralığa (genellikle 0-1) sıkıştırır.
* `Min-max normalizasyonu` en yaygın yöntemdir: `(eski değer - min) / (max - min)`.

#### Standardizasyon (Standardization) - Z-Score
* Verileri, ortalaması 0 ve standart sapması 1 olacak şekilde dönüştürür.
* `Standardizasyon = (eski değer - ortalama) / standart sapma`.
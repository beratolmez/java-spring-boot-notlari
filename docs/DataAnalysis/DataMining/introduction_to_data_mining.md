# Veri Madenciliğine Giriş

Veri madenciliği, büyük veri kümelerinden anlamlı ve faydalı bilgileri çıkarmak için kullanılan bir dizi tekniktir.

* **Veri Madenciliği Süreci:**
    `Data -> Data Preprocessing -> Data Mining -> Post Processing -> Information`

* **Predictive (Tahmine Dayalı):** Tahminlere dayalı öngörülerde bulunmak için geçmiş veya mevcut veriyi kullanır.

---

## Veri Ön İşleme (Data Preprocessing)

Veri, genellikle gürültülü, tamamlanmamış, tutarsız veya tekrarlanan değerler içerir. Veri ön işleme, modeli eğitilebilir hale getirmek için veriyi düzenleme işlemidir.

### Normalizasyon Yöntemleri

* **Z-score Normalizasyonu:** Verileri standart normal dağılıma dönüştürür.
    `Yeni Değer = (Eski Değer - Ortalama) / Standart Sapma`
* **Min-max Normalizasyonu:** Verileri 0 ile 1 arasına ölçeklendirir.
    `Yeni Değer = (Eski Değer - Minimum Değer) / (Maksimum Değer - Minimum Değer)`

---

## Sınıflandırma (Classification) Algoritmaları

Sınıflandırma, verileri belirli kategorilere veya sınıflara ayırmak için kullanılan bir veri madenciliği tekniğidir.

* Karar Ağaçları
* En Yakın Komşu (K-NN)
* Yapay Sinir Ağları
* Naive Bayes
* Destek Vektör Makineleri (SVM)

### Algoritma Performans Metrikleri

* **Precision (Kesinlik):** Modelin pozitif olarak tahmin ettiği durumların ne kadarının gerçekten pozitif olduğunu gösterir.
    `Keşfedilen Hedef / Keşfedilen Tüm`
* **Recall (Duyarlılık):** Gerçekte pozitif olan durumların ne kadarını modelin doğru tahmin ettiğini gösterir.
    `Keşfedilen Hedef / Gerçek Tüm`
* **F-Score:** Precision ve Recall değerlerinin harmonik ortalamasıdır. İki metriği de dengeleyen bir ölçüm sunar.
    `2 * Precision * Recall / (Precision + Recall)`

---

## Karar Ağaçları

* Hem **kategorik** hem de **sayısal** verileri işleyebilen tek yöntemdir.
* **Eager learner** tekniğiyle çalışır; tüm eğitim verisini analiz ederek bir model oluşturur.
* En az sayıda karşılaştırma yaparak bir sınıflandırma sonucuna ulaşmayı hedefler.

### Ağaç Oluşturma Yöntemleri

* **Entropy (Entropi):** Veri setindeki rastgeleliği ve belirsizliği ölçer. Karar ağaçlarında **bilgi kazancını** hesaplamak için kullanılır.
    `Bilgi Kazancı = Genel Entropi - Sütun Entropisi`
    Bilgi kazancı en yüksek olan öznitelik kök düğüm olarak seçilir.
* **Gini İndeksi:** Sadece ikili dallanma (binary split) yaklaşımıyla çalışır. En düşük Gini indeksine sahip öznitelik seçilerek düğümler oluşturulur.

---

## K-En Yakın Komşu (K-Nearest Neighbor - KNN)

* **Supervised** (gözetimli) bir makine öğrenmesi tekniğidir.
* **Lazy learner** (tembel öğrenme) tekniğini kullanır. Eğitim aşamasında model oluşturmaz; tahmin aşamasında en yakın komşularına göre karar verir.
* Belirtilen `K` değeri (genellikle tek sayı), tahmin için kaç komşunun dikkate alınacağını belirler.

Elbette, veri madenciliğine giriş notlarınızın Markdown formatına dönüştürülmüş halini aşağıda bulabilirsiniz.

---

## Sınıflandırma ve Tahmin Algoritmaları

### Naive Bayes
* Her bir niteliğin birbirinden bağımsız olduğunu varsayan olasılıksal bir sınıflandırma algoritmasıdır.
* **İşleyiş:** Bir örneğin hangi sınıfa ait olduğunu, sınıfların ve özelliklerin olasılıklarını çarparak tahmin eder.
* **Temel Prensip:** Nitelikler birbirinden bağımsızdır ve eşit derecede önemlidir.

### Regresyon
* **Sürekli Veri Tahmini:** Bağımsız değişkenlerin değerlerine dayanarak sürekli bir bağımlı değişkenin değerini tahmin etmek için kullanılır.
* **Kullanım Alanı:** Fiyat tahmini, sıcaklık tahmini gibi sürekli değerlerin olduğu problemlerde kullanılır.

### Destek Vektör Makineleri (SVM)
* **Amacı:** Sınıflar arasında en iyi "hiper düzlemi" (karar sınırını) bularak sınıflandırma yapmaktır.
* **Yöntem:** Problemi ikili parçalara bölerek çözmeye çalışır (**"böl, parçala, yönet"** metodu). Hem doğrusal hem de doğrusal olmayan verilerde etkilidir.

### Yapay Sinir Ağları (YSA)
* **Gücü:** Doğrusal olmayan veriler arasındaki karmaşık ilişkileri bulmada güçlü bir yapıdır.
* **Temel Yapı:**
    * **Giriş Nöronları:** Veri setindeki nitelik sayısına eşittir.
    * **Gizli Nöronlar:** Öğrenme sürecinde ayarlanan ara katmanlardır.
    * **Çıkış Nöronları:** Tahmin edilecek sınıf sayısına eşittir.
* **Öğrenme Aşaması:** Oluşturma, eğitme, küçültme ve yorumlama adımlarını içerir.

---

## Model Değerlendirmesi ve Optimizasyonu

### Bias (Sapma) ve Varyans
* **Bias:** Modelin tahminleri ile gerçek değerler arasındaki ortalama farkı gösterir. Yüksek bias, modelin yeterince öğrenemediği anlamına gelir.
* **Varyans:** Modelin tahminlerinin farklı veri setleri üzerindeki değişkenliğidir. Yüksek varyans, modelin eğitim verisine aşırı uyum sağladığı (ezberlediği) anlamına gelir.
* **İlişkisi:**
    * **Yüksek Bias, Düşük Varyans:** **Underfitting** (Model yetersiz öğrenme)
    * **Düşük Bias, Yüksek Varyans:** **Overfitting** (Model aşırı öğrenme)
* **Çözümler:**
    * **Yüksek Varyans (Overfitting) için:** Daha fazla eğitim verisi eklemek veya **düzenlileştirme (regularization)** tekniklerini kullanmak.
    * **Yüksek Bias (Underfitting) için:** Model eğitimini artırmak veya farklı bir algoritma kullanmak.

### Ensemble ve Random Forest
* **Ensemble (Topluluk Öğrenmesi):** Tek bir güçlü model yerine, birden fazla zayıf modelin bir araya getirilerek daha iyi sonuçlar elde etmesini sağlayan bir tekniktir.
* **Random Forest:** Birden fazla karar ağacından oluşan bir ensemble algoritmasıdır. Hangi algoritmanın daha başarılı olacağını belirleyerek çalışır.

---

## Kümeleme (Clustering)

* **Tanım:** Verileri gruplara ayırarak kümeleme yapan, **gözetimsiz (unsupervised)** bir tekniktir. Verileri etiketlemez, benzerliklerine göre gruplandırır.
* **Algoritmalar:** K-Means, Hiyerarşik Kümeleme, Yoğunluk Tabanlı Kümeleme.

### K-Means Algoritması
1.  Veri kümesi `k` alt kümeye ayrılır.
2.  Her kümenin ortalaması (merkez noktası) hesaplanır.
3.  Her bir nesne, kendine en yakın merkez noktaya atanır.
4.  Nesne atamalarında değişiklik olmayana kadar 2. ve 3. adımlar tekrarlanır.
* **Değerlendirme:** Hataların Kareleri Toplamını (SSE) azaltmak için küme sayısı artırılabilir veya farklı merkez noktaları seçilebilir.

---

## Birliktelik Kuralları (Association Rule)

* **Amaç:** Veriler arasında, bir öğenin varlığının başka bir öğenin varlığına yol açtığı kuralları bulmaktır (Örn: "Eğer bir müşteri X ürününü aldıysa, Y ürününü de alma olasılığı nedir?").
* **Apriori Algoritması:** Birliktelik kurallarını bulmak için kullanılan yaygın bir algoritmadır.

### Temel Metrikler
* **Support (Destek):** Bir öğe setinin toplam verideki görünme oranı.
    * `Support = (A ve B'nin Birlikte Görünme Sayısı) / (Toplam Satır Sayısı)`
* **Confidence (Güven):** Belirli bir öğe setinin (`A`) verildiğinde, başka bir öğe setinin (`B`) de bulunma olasılığı.
    * `Confidence = (A ve B'nin Birlikte Görünme Sayısı) / (A'nın Görünme Sayısı)`
# Bulanık Mantık (Fuzzy Logic)

Bulanık mantık, insan düşünce yapısına benzer şekilde kesin olmayan veya belirsiz durumları modellemek için kullanılan bir mantık sistemidir.

### Temel Özellikler
1.  **Kural Tabanlı Sistem:** Uzman bilgisini veya veriye dayalı kuralları kullanarak çalışır.
2.  **Bulanık Kurallar:** `Eğer-ise` (`if-then`) kuralları ile ifade edilir.
3.  **Üyelik Fonksiyonları:** Bir elemanın bir kümeye ne kadar ait olduğunu gösteren fonksiyonlarla tanımlanır.
4.  **Bilgi Edinme:** Uzmanlardan veya bilgi tabanlarından kural setleri elde etmek en temel adımdır.

### Neden Bulanık Mantık?
* **Sezgisel Yapı:** Karar veya kural tabanlı yapısıyla insan mantığına yakındır.
* **Model Bağımsızlığı:** Karmaşık matematiksel bir modele ihtiyaç duymaz.
* **Hız ve Adaptasyon:** Hızlıdır ve değişen koşullara kolayca adapte olabilir.
* **Problemden Az Etkilenme:** Küçük değişikliklerden veya hatalı verilerden daha az etkilenir.

### Bulanık Sistem Tipleri
* **Saf Bulanık Sistem:** Klasik bulanık mantık sistemidir.
* **Takagi-Sugeno-Kang (TSK) Bulanık Sistem:** Çıktıları doğrusal fonksiyonlar olan bir model türüdür.
* **Bulandırıcı ve Durulayıcı Bulanık Sistem:** Veriyi bulanıklaştırıp (fuzzification) işleyen ve sonra tekrar kesin değere (defuzzification) dönüştüren bir sistemdir.

---

## Küme Tipleri ve İşlemleri

### Kesin Küme (Crisp Set)
* Bir eleman bir kümenin ya **tam üyesidir (1)** ya da **hiç üyesi değildir (0)**.
* Üyelik derecesi sadece 0 veya 1 olabilir.

### Bulanık Küme (Fuzzy Set)
* Bir eleman bir kümeye **0 ile 1 arasında herhangi bir değerle** üye olabilir.
* Bu üyelik derecesi, bir **üyelik fonksiyonu** ile tanımlanır.
    * **Üyelik Fonksiyonu Türleri:** Üçgen, Yamuk, Gauss vb.

### Bulanık İşlemler
* **Kesişim (t-norm):** İki üyelik fonksiyonunun **minimum** değerini alır. `AND` ifadesine karşılık gelir.
    * `μ_A∩B(x) = min(μ_A(x), μ_B(x))`
* **Birleşim (s-norm):** İki üyelik fonksiyonunun **maksimum** değerini alır. `OR` ifadesine karşılık gelir.
    * `μ_A∪B(x) = max(μ_A(x), μ_B(x))`
* **Dışlama (d-norm):** Bir üyelik fonksiyonunun tersini alır. `NOT` ifadesine karşılık gelir.

---

## Bulanık Çıkarım ve Durulama

### Bulanık Çıkarım (Fuzzy Inference)
* Bulanık kurallara dayalı bir karar verme mekanizmasıdır.
* Sistem, bulanık girdileri alarak bulanık çıktıları üretir.
* `Supremum`: Genellikle birleştirme işlemlerinde (`maksimum`) kullanılır.
* `Infimum`: Kural değerlendirmesinde (`minimum`) kullanılır.

### Durulama (Defuzzification)
* Bulanık çıkarım sisteminin çıktısı olan bulanık kümeyi, gerçek dünya için anlamlı olan **tek bir sayısal değere (crisp değer)** dönüştürme işlemidir.

### Durulama Metotları
1.  **Merkezi Ortalama Metodu (WAM):**
    * `y* = (y1*w1 + y2*w2 + ...) / (w1 + w2 + ...)`
    * Ağırlıklı bir ortalama hesaplama yöntemidir.
2.  **Ağırlık Merkezi Metodu (Centroid):** Bulanık çıktının geometrik ağırlık merkezini hesaplar.
3.  **Gravite Merkezi / Alan Merkezi Metodu:** Sürekli formda çalışan ve alanın ağırlık merkezini bulmaya odaklanan bir yöntemdir.

### Standart Bulanık Sistem
* **Singleton Bulandırıcı:** Girdiyi birim üyelik derecesiyle tek bir nokta olarak alır.
* **Çarpım Çıkarım Sistemi:** Kural çıkarımında çarpım (`multiplication`) operatörünü kullanır.
* **Merkezi Ortalama Durulayıcı:** Sonucu tek bir değere indirmek için merkezi ortalama yöntemini kullanır.
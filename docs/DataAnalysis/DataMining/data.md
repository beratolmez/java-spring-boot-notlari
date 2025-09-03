# Veri ve Veri Hazırlama

Veri madenciliği ve makine öğrenmesi süreçlerinin en kritik adımlarından biri, **veri ön işleme** aşamasıdır. Bu aşamada, ham veriler eksik, kirli veya hatalı bilgilerden arındırılarak analize uygun hale getirilir.

---

## Veri Tipleri

Veri türleri, taşıdıkları anlama ve üzerinde yapılabilecek işlemlere göre dört ana gruba ayrılır. Bu gruplar genellikle **kategorik** ve **nümerik** olmak üzere iki ana kategoriye ayrılabilir.

### Kategorik Veri Tipleri
1.  **Nominal Veriler:** Aralarında herhangi bir sıralama veya büyüklük ilişkisi olmayan verilerdir. Sadece eşitlik veya eşitsizlik durumları söz konusudur.
    * **Örnekler:** ID numaraları, göz renkleri, şehir isimleri. (`=`, `!=`)
2.  **Ordinal (Sıralama Ölçeği):** Belirli bir sıralama ilişkisi bulunan verilerdir, ancak aralarındaki farklar ölçülemez.
    * **Örnekler:** Ürün değerlendirme (kötü, iyi, çok iyi), kıyafet bedenleri (S, M, L). (`<`, `>`, `<=`, `>=`)

### Nümerik Veri Tipleri
3.  **Interval (Aralıklı):** Sayısal değerler arasında anlamlı farklar olan verilerdir. Toplama ve çıkarma işlemleri yapılabilir, ancak çarpma ve bölme işlemleri anlamlı değildir çünkü mutlak bir sıfır noktası yoktur.
    * **Örnekler:** Fahrenheit ve Celsius sıcaklıkları, takvim yılları. (`+`, `-`)
4.  **Ratio (Oran):** Mutlak bir sıfır noktası olan (yokluğu ifade eden) sayısal verilerdir. Tüm matematiksel işlemler (toplama, çıkarma, çarpma, bölme) anlamlıdır.
    * **Örnekler:** Kelvin sıcaklığı, uzunluk, ağırlık. (`*`, `/`)

---

## Değişken Tipleri

* **Kesikli Değişken:** Belirli, sayılabilir sayıda değere sahiptir. Genellikle tam sayılarla ifade edilir. **İkili (binary)** gösterim bu değişkenin bir alt tipidir.
* **Sürekli Değişken:** Sınırsız sayıda değere sahip olabilir. Genellikle ondalıklı veya kesirli değerlerle ifade edilir.

---

## Veri Görselleştirme

Veri görselleştirme, verinin dağılımını, ilişkilerini ve aykırı değerleri hızlıca anlamamızı sağlar.

* **Histogram:** Veri dağılımının şeklini gösterir. Kutucukların yüksekliği, ilgili aralıktaki veri sayısını (frekans) temsil eder.
* **Dağılım (Scatter) Grafiği:** İki değişken arasındaki ilişkiyi, eğilimi veya örüntüyü incelemek için kullanılır. Her bir veri noktası, x ve y eksenlerindeki bir çift değeri temsil eder.
* **Kutu Grafikleri (Box Plots):** Bir veri kümesinin dağılım özetini gösterir. Medyan, çeyreklikler (IQR), minimum, maksimum ve aykırı değerler gibi önemli istatistikleri kolayca görmeyi sağlar.

---

## Veri Benzerliği ve Uzaklık Ölçütleri

* **Benzerlik Ölçüsü:** İki veri noktası arasındaki benzerliği gösteren bir metriktir. Değeri `[0, 1]` arasında değişir. `1`'e yakın bir değer, verilerin birbirine çok benzediğini gösterir.
* **Uzaklık (Benzemezlik) Ölçüsü:** İki veri noktası arasındaki farklılığı ölçer. Değerin `0`'a yakın olması, verilerin benzer olduğunu ifade eder.
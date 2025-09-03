# NumPy ile Sayısal İşlemler

NumPy, Python'da bilimsel hesaplamalar için temel bir kütüphanedir. Özellikle çok boyutlu diziler (`arrays`) ve matrislerle çalışmak için hızlı ve verimli fonksiyonlar sunar.

### Dizi Oluşturma Fonksiyonları

* **`np.array()`**: Verilen bir listeyi NumPy dizisine dönüştürür.
* **`np.arange(0, 10)`**: Belirtilen aralıkta (0'dan 9'a kadar) değerlerden oluşan bir dizi oluşturur. Python'daki `range()` fonksiyonuna benzer.
* **`np.zeros(5)`**: İçinde 5 adet `0` değeri olan tek boyutlu bir dizi oluşturur.
* **`np.zeros((2, 2))`**: Değerleri `0` olan 2x2 boyutunda bir matris oluşturur.
* **`np.ones((2, 2))`**: Değerleri `1` olan 2x2 boyutunda bir matris oluşturur.
* **`np.linspace(0, 20, 5)`**: 0 ile 20 arasında, aralıkları eşit olan 5 adet değerden oluşan bir dizi oluşturur.
* **`np.eye(3)`**: 3x3 boyutunda birim matris (köşegenleri `1` olan) oluşturur.

### Rastgele Sayı Üretme

NumPy, çeşitli rastgele sayı fonksiyonları da sunar.

* **`np.random.randn(8)`**: Standart normal dağılıma göre 8 adet rastgele ondalıklı sayıdan oluşan bir dizi döndürür.
* **`np.random.randint(1, 10)`**: 1 ile 9 arasında (10 hariç) rastgele bir tam sayı üretir.
* **`np.random.randint(1, 300, 5)`**: 1 ile 299 arasında rastgele 5 adet tam sayıdan oluşan bir dizi oluşturur.

---

### Dizi Özellikleri ve Metotları

NumPy dizileri, veri manipülasyonunu kolaylaştıran birçok kullanışlı metoda sahiptir.

* **`dizi.reshape(5, 6)`**: Bir diziyi 5x6 boyutunda bir matrise dönüştürür.
* **`dizi.max()`**: Dizideki en büyük değeri döndürür.
* **`dizi.min()`**: Dizideki en küçük değeri döndürür.
* **`dizi.argmax()`**: En büyük değerin indeksini döndürür.
* **`dizi.argmin()`**: En küçük değerin indeksini döndürür.
* **`dizi.shape`**: Dizinin boyutunu ve şeklini (`(satır_sayısı, sütun_sayısı)`) gösterir.

### Bellek Yönetimi ve Slicing

* **`slicingDizisi[:] = 700`**: NumPy'da bir dizinin kesitini (`slice`) başka bir değişkene atamak, aslında aynı bellek alanını işaret eder. Bu nedenle, kesit üzerinde yapılan değişiklikler orijinal diziyi de etkiler.
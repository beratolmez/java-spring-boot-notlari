# Pandas Kütüphanesi ile Veri Analizi

Pandas, Python'da veri manipülasyonu ve analizi için kullanılan güçlü bir kütüphanedir. İki ana veri yapısı vardır: **Series** ve **DataFrame**. Genellikle **veri çerçeveleri (data frames)** ile çalışırsınız, bu da verileri tablo formatında saklamanızı sağlar.

-----

## Series (Seriler)

Series, tek boyutlu etiketli bir dizidir.

  * **Oluşturma:** Bir sözlükten veya bir veri ve indeks listesinden oluşturulabilir.
    ```python
    pd.Series(sozlugum)
    pd.Series(data, index=index)
    ```
  * **Toplama:** İki seri toplandığında, Pandas ortak indekslere sahip değerleri toplar ve diğer indeksler için **NaN (Not a Number)** bırakır.

## DataFrame (Veri Çerçeveleri)

DataFrame, iki boyutlu etiketli bir veri yapısıdır. Excel veya SQL tablosuna benzer.

  * **Oluşturma:** Bir sözlükten, NumPy dizisinden veya başka veri yapılarından oluşturulabilir.
    ```python
    dataFrame = pd.DataFrame(data)
    pd.DataFrame(data, index=index, columns=columns)
    ```
  * **Sütun Silme:** Belirli bir sütunu silmek için `drop()` kullanılır. `axis=1` sütunu, `inplace=True` ise değişikliğin kalıcı olmasını belirtir.
    ```python
    dataFrame.drop("yas", axis=1, inplace=True)
    ```
  * **İndeks Değiştirme:** Yeni bir sütunu indeks olarak ayarlamak için `set_index()` kullanılır.
    ```python
    yeniDataFrame.set_index("yeni indeks", inplace=True)
    ```
  * **Çoklu İndeks:** İki veya daha fazla indeksi birleştirmek için `zip()` kullanılır.
    ```python
    birlesmisIndeks = list(zip(ilkIndeksler, icIndeksler))
    ```

-----

## Eksik Verilerle Başa Çıkma

Eksik veriler (`NaN` değerleri) analiz sürecini olumsuz etkileyebilir. Pandas bu verilerle başa çıkmak için çeşitli yöntemler sunar.

  * **Satırları Silme:**
      * `dataFrame.dropna()`: Boş değer içeren tüm satırları siler.
      * `dataFrame.dropna(axis=1)`: Boş değer içeren tüm sütunları siler.
      * `dataFrame.dropna(axis=1, thresh=2)`: Sadece en az 2 veya daha fazla boş değeri olan sütunları siler.
  * **Boşlukları Doldurma:**
      * `dataFrame.fillna(20)`: Tüm boş değerleri 20 ile doldurur.

-----

## Veri Gruplama ve Birleştirme

Pandas, büyük veri kümelerini analiz etmek için güçlü bir gruplama ve birleştirme yeteneğine sahiptir.

  * **Gruplama:** `groupby()` fonksiyonu ile veriler belirtilen bir sütuna göre gruplanabilir.
    ```python
    grupObjesi = dataFrame.groupby("Departman")
    ```
  * **Birleştirme (Concatenation):** Farklı DataFrame'leri birleştirmek için `pd.concat()` kullanılır.
    ```python
    pd.concat([dataFrame1, dataFrame2, dataFrame3])
    ```
  * **Birleştirme (Merging):** İki DataFrame'i ortak bir sütun (`on`) üzerinden birleştirmek için `pd.merge()` kullanılır.
    ```python
    pd.merge(dataFrame1, dataFrame2, on="Isim")
    ```

## Eşsiz Değerleri Bulma

  * `maasDataFrame["Departman"].unique()`: "Departman" sütunundaki tüm benzersiz değerleri bir NumPy dizisi olarak döndürür.
  * `maasDataFrame["Departman"].nunique()`: "Departman" sütunundaki benzersiz değerlerin sayısını döndürür.
  * `maasDataFrame["Departman"].value_counts()`: Her bir benzersiz değerin kaç kez tekrarlandığını sayar.
  * **Excel İşlemleri:** Pandas, Excel dosyalarından veri okuma ve yazma işlemlerini de kolaylaştırır.
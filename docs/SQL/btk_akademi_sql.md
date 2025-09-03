# Uygulamalarla SQL Öğreniyorum

---

## Temel SQL Komutları

SQL komutları, genellikle veriyi ve veritabanı yapısını yönetmek için iki ana gruba ayrılır.

### Veri İşleme (DML - Data Manipulation Language)

* **`SELECT`**: Veritabanından veri çekmek için kullanılır.
    * `SELECT KOLON1, KOLON2 FROM TABLOADI WHERE <ŞARTLAR>`
* **`INSERT`**: Bir tabloya yeni veri eklemek için kullanılır.
    * `INSERT INTO TABLOADI (KOLON1, KOLON2) VALUES (DEĞER1, DEĞER2)`
* **`UPDATE`**: Mevcut veriyi güncellemek için kullanılır.
    * `UPDATE TABLOADI SET KOLON1=YENİ_DEĞER WHERE <ŞARTLAR>`
* **`DELETE`**: Bir tablodan veri silmek için kullanılır.
    * `DELETE FROM TABLOADI WHERE <ŞARTLAR>`
* **`TRUNCATE`**: Bir tablodaki tüm verileri hızlı bir şekilde siler.

### Veritabanı Yapısı İşleme (DDL - Data Definition Language)

* **`CREATE`**: Yeni veritabanı, tablo veya nesneler oluşturmak için kullanılır.
* **`ALTER`**: Mevcut bir veritabanı nesnesinin yapısını değiştirmek için kullanılır.
* **`DROP`**: Mevcut bir veritabanı nesnesini silmek için kullanılır.

---

## Şartlar ve Filtreleme (`WHERE` Clause)

`WHERE` komutu, sorgularınıza filtre eklemek için kullanılır.

* `=` : Eşittir
* `<>` : Eşit değildir
* `>`, `<`, `>=`, `<=` : Büyük, küçük, büyük eşit, küçük eşit
* **`BETWEEN`**: Belirli bir aralıktaki değerleri seçer.
* **`LIKE`**: Metin verilerinde desen araması yapar.
    * `LIKE '%ÇOLAKOĞLU'`: "Çolakoğlu" ile bitenleri bulur.
* **`IN`**: Belirtilen listedeki değerleri seçer.
* **`NOT LIKE` / `NOT IN`**: Belirtilen desen veya listede olmayan değerleri seçer.

---

## Sorgu Fonksiyonları ve Sıralama

* **`DISTINCT`**: Seçilen sütundaki yinelenen değerleri kaldırarak sadece benzersiz değerleri getirir.
    * `SELECT DISTINCT City FROM Customers`
* **`ORDER BY`**: Sorgu sonuçlarını belirli bir sütuna göre sıralar.
    * `ASC`: Artan sıralama (varsayılan)
    * `DESC`: Azalan sıralama
* **`TOP` / `PERCENT`**: Sorgu sonucunda kaç satır veya yüzde kaçının getirileceğini belirler.
* **`Aggregate Functions`**: Veri grupları üzerinde matematiksel işlemler yapar.
    * `SUM()`: Toplamını alır.
    * `MIN()`, `MAX()`: En küçük ve en büyük değeri bulur.
    * `AVG()`: Ortalamayı alır.
    * `COUNT()`: Sayısını bulur.
* **`GROUP BY`**: Agregasyon fonksiyonlarını belirli gruplara göre uygular.
* **`HAVING`**: `GROUP BY` ile birlikte kullanılır ve gruplara filtre uygular. `WHERE` ile aynı mantıkta çalışır ancak grup sonuçlarına etki eder.

---

## Diğer Önemli Kavramlar

* **`ALIAS` (`AS`)**: Tablo veya sütunlara geçici takma adlar (alias) verir, bu da sorguyu daha okunaklı hale getirir.
* **`CONVERT`**: Veri tiplerini dönüştürür.
    * `CONVERT(DATE, DATE_)`
* **String Fonksiyonları:**
    * `SUBSTRING('BERAT ÖLMEZ', 6, 6)`: Bir metin içinden belirli bir parçasını alır.
    * `CONCAT()` / `CONCAT_WS()`: İki veya daha fazla metni birleştirir.

---

## İlişkisel Veritabanı ve JOIN İşlemleri

İlişkisel veritabanı, birbirine bağlı tablolardan oluşan bir yapıdır. Tablolar arası ilişkiler kurarak veriyi birleştirmek için **`JOIN`** komutları kullanılır.

* **`INNER JOIN`**: İki tablonun sadece ortak olan kayıtlarını (kesişim kümesi) getirir.
* **`LEFT JOIN`**: Sol taraftaki tablodaki tüm kayıtları ve bunlarla eşleşen sağ tablodaki kayıtları getirir.
* **`RIGHT JOIN`**: Sağ taraftaki tablodaki tüm kayıtları ve bunlarla eşleşen sol tablodaki kayıtları getirir.
* **`FULL JOIN`**: Her iki tablodaki tüm kayıtları birleştirir. Eşleşme olmasa bile her iki tablodaki verileri getirir.
* **`SUBQUERY`**: Bir sorgunun içinde başka bir sorgu kullanılmasıdır.

---

## Veri Tipleri

* **Tam Sayı:** `bigint`, `int`, `smallint`, `tinyint`
* **Ondalık Sayı:** `decimal`, `money`, `float`, `real`
* **Metin (String):**
    * `char`: Belirtilen boyutta yer kaplar.
    * `text`: Yazılan kadar yer kaplar.
    * `varchar`: Maksimum boyutu belirtilir ama sadece kullanılan kadar yer kaplar.
    * **Unicode Destekli:** `nvarchar`, `nchar`, `ntext` gibi tipler, farklı dillerdeki karakterleri destekler.
* **Tarih, Saat:** `date`, `smalldate`, `datetime`, `datetime2`, `time`
* **Diğer:** `image`, `binary`, `varbinary` (dosya verileri için)
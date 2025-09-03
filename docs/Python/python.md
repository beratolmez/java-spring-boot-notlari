# Python Programlama Diline Giriş

Python, veri analizi, web geliştirme ve yapay zeka gibi birçok alanda kullanılan, okunabilir ve basit bir dildir.

---

## Koleksiyonlar ve Fonksiyonlar

### Setler (Kümeler)
Bir liste `set`'e dönüştürüldüğünde, içindeki yinelenen değerler otomatik olarak kaldırılır ve sadece benzersiz değerler kalır.

* **Örnek:** `[1, 2, 3, 1, 2, 2]` listesi, sete çevrildiğinde `{1, 2, 3}` haline gelir.

### `pass` İfadesi
Bir döngü veya fonksiyonun içine herhangi bir kod yazmak istemediğinizde `pass` ifadesini kullanabilirsiniz. Bu, kodun hiçbir şey yapmadan tamamlanmasını sağlar ve sintaks hatası vermesini engeller.

### `range()` Fonksiyonu
Belirli bir aralıkta sıralı sayılar oluşturmak için kullanılır.
* `list(range(20))`: 0'dan 19'a kadar (20 dahil değil) bir liste oluşturur.
* `list(range(5, 22, 4))`: 5'ten başlayarak 21'e kadar (22 dahil değil), 4'er birim atlayarak veriler oluşturur.

### `enumerate()` Fonksiyonu
Bir koleksiyondaki her elemanı numaralandırır.
* **Örnek:** `enumerate(list(range(5, 15)))` ifadesi, 5'ten 14'e kadar olan elemanları numaralandıran bir demet (`tuple`) listesi oluşturur.

### `zip()` Fonksiyonu
Birden fazla koleksiyonu birleştirir.
* `list(zip(liste1, liste2, liste3))`: Üç farklı listenin elemanlarını birleştirerek bir liste oluşturur.

### `random` Kütüphanesi
Rastgele sayılar üretmek için kullanılır.
* `randint(0, 100)`: 0 ile 100 arasında (100 dahil) rastgele bir tam sayı oluşturur.

---

## Gelişmiş Özellikler

### Liste Oluşturma (List Comprehension)
Listeleri daha kısa ve okunaklı bir şekilde oluşturmanızı sağlar.
* **Örnek:** `metin = "texas paris"` ifadesini, `listeOrnegi = [harf for harf in metin]` kullanarak her harfin bir eleman olduğu bir listeye dönüştürebilirsiniz.

### Esnek Fonksiyon Argümanları

* **`*args`:** Fonksiyonlara sınırsız sayıda pozisyonel argüman (`*args`) eklemenizi sağlar. Bu argümanlar, fonksiyon içinde bir demet (`tuple`) olarak erişilebilir.
* **`**kwargs`:** Fonksiyonlara sınırsız sayıda anahtar-değer ilişkili argüman (`**kwargs`) eklemenizi sağlar. Bu argümanlar, fonksiyon içinde bir sözlük (`dictionary`) olarak erişilebilir.

---
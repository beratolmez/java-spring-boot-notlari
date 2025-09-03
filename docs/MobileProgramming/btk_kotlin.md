# Kotlin'e Giriş

-----

## Değişken Tanımlama

Kotlin'de değişken tanımlamak için iki temel anahtar kelime kullanılır:

  * `var`: Değeri sonradan **değiştirilebilir** değişkenler için kullanılır.
  * `val`: Değeri tanımlandıktan sonra **değiştirilemeyen** (sabit) değişkenler için kullanılır.

-----

## Koleksiyonlar (Collections)

### Diziler (Arrays)

  * `arrayOf()`: Sabit boyutlu bir dizi oluşturur.
      * **Örnek:** `val dizi = arrayOf("deger1", "deger2")`
  * `arrayListOf()`: Dinamik boyutlu (büyüyüp küçülebilen) bir liste oluşturur.
      * **Örnek:** `val liste = arrayListOf("deger1", "deger2")`

### Listeler (Lists)

  * `val listeAdi = arrayListOf<Int>()`: Boş bir tamsayı listesi oluşturur.
  * `arrayListOf<Any>()`: Herhangi bir türde değişkeni tutabilen bir liste oluşturur.

### Haritalar (Maps)

  * **Anahtar-Değer Eşleşmesi:** Anahtar ve değer çiftlerini saklamak için kullanılır.
  * `var harita = hashMapOf<String, Int>()`: Boş bir harita oluşturur.
  * **Değer Ekleme:** `harita.put("Elma", 100)` komutuyla yeni bir çift eklenir.

-----

## Kontrol Yapıları

### When İfadesi

  * Diğer dillerdeki **`switch-case`** yapısına benzerdir.
  * Bir değişkenin değerine göre farklı kod bloklarını çalıştırır.

<!-- end list -->

```kotlin
when(kontrolDegiskeni) {
    0 -> notString = "gecersiz"
    1 -> notString = "gecerli"
    else -> notString = "bilinemez"
}
```

### For Döngüsü

  * Belirli bir koleksiyondaki her eleman üzerinde gezinmek için kullanılır.

<!-- end list -->

```kotlin
for (numara in baskaDizi) {
    println(numara)
}
```

-----

## Fonksiyonlar ve Sınıflar

### Fonksiyonlar (Functions)

  * `fun fonksiyonAdi() { ... }`: Geriye değer döndürmeyen bir fonksiyon tanımlar.
  * `fun fonksiyonAdi(): Int { ... }`: Geriye bir tamsayı (`Int`) değeri döndüren bir fonksiyon tanımlar.

### Sınıflar (Classes)

  * **Constructor:** Bir sınıf nesnesi oluşturulurken ilk çalışan metottur.
      * `class Superkahraman(var isim: String, var yas: Int, var meslek: String)`
  * **Nesne Türetme:** `val superman = Superkahraman("Clark Kent", 30, "Gazeteci")`
  * **Özelliklere Erişim:**
      * `superman.meslek` gibi özelliklere erişilebilir.
      * `superman.isinat()` gibi sınıfın metotları çağrılabilir.
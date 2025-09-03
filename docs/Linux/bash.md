# Bash Kabuk Betiği Temelleri

Bash, Linux sistemlerinde en sık kullanılan **kabuk betik dilidir**. Linux'ta sistemdeki her şey bir dosya olarak kabul edilir, bu da Bash'in dosya ve dizin yönetimi için ne kadar güçlü olduğunu gösterir.

-----

## Temel Komutlar ve Değişkenler

  * **`time`**: Bir komutun veya sürecin ne kadar sürede tamamlandığını gösterir.
  * **`date`**: Sistemdeki güncel tarih ve saati görüntüler.

### Değişkenler ve Argümanlar

  * **`myvariable="Selam"`**: Bir değişken tanımlama. `=` işaretinin etrafında boşluk bırakılmaz.
  * **`$1`, `$2`**: Kabuk betiğine dışarıdan gönderilen argümanları temsil eder.
  * **`$0`**: Çalıştırılan programın adını ifade eder.
  * **`$$`**: Çalışan sürecin (`process`) kimlik numarasını (`PID`) verir.
  * **`$USER`**: Betiği çalıştıran kullanıcının adını yazar.
  * **`$RANDOM`**: 0 ile 32767 arasında rastgele bir tam sayı üretir.
  * **`$HOSTNAME`**: Çalışılan makinenin adını gösterir.

### Matematiksel İşlemler

  * **`let a=5+4`**: `let` ifadesi basit aritmetik işlemler için kullanılır.
      * **Örnek:** `let a=a+1` veya `let "a = a + 1"` komutları, `a` değişkeninin değerini 1 artırır. Tırnak işaretleri, boşlukları doğru şekilde yönetmek için kullanılır ancak basit durumlarda zorunlu değildir.
  * **`expr 2 + 3`**: `expr` komutu, aralarında boşluk olan ifadelerle aritmetik işlemler yapar ve sonucu ekrana yazdırır.

-----

## Kontrol Yapıları ve Fonksiyonlar

### Koşul İfadeleri (`if`)

`if` koşulu, belirli bir durumun doğru olup olmadığını kontrol eder.

```bash
if [ "merhaba" = "merhaba" ]
then
    echo "Girilen değer doğru"
else
    echo "Girilen değer yanlış"
fi
```

  * **Eşitlik kontrolü:** ` =  ` veya `-eq` operatörleri kullanılır.
  * **Büyüklük/Küçüklük kontrolü:**
      * `-gt` (`greater than`): Büyükse
      * `-lt` (`less than`): Küçükse

### Fonksiyonlar

Bash'te fonksiyonlar iki şekilde tanımlanabilir:

```bash
function topla() {
    # fonksiyon kodları
}
```

veya

```bash
topla() {
    # fonksiyon kodları
}
```

  * **Değişken Kapsamı:** Fonksiyon içinde `local` ifadesi ile tanımlanmayan değişkenler **global** olarak kabul edilir ve her yerden erişilebilir.
  * **`$?`**: En son çalıştırılan komutun veya fonksiyonun dönüş değerini (`exit status`) gösterir.

-----

## Diğer Faydalı Komutlar

  * **`command ls -la`**: Bir komutu çalıştırır. Bazen komut adlarının aynı olduğu durumlarda karışıklığı önlemek için kullanılır.
  * **`tput`**: Komut satırında metin biçimlendirme ve imleç kontrolü gibi etkileşimli özellikler sağlar.

-----

## Vi Editörü Kullanımı

Vi, Unix ve Linux sistemlerinde yaygın olarak kullanılan güçlü bir metin editörüdür. Temel komutları:

  * **`i`**: Ekleme (`insert`) moduna geçerek metin yazmanızı sağlar.
  * **`Esc`**: Ekleme modundan çıkarak komut moduna döner.
  * **`:w`**: Yaptığınız değişiklikleri kaydeder.
  * **`:q`**: Dosyadan çıkar.
  * **`:wq`**: Değişiklikleri kaydeder ve çıkar.
  * **`:q!`**: Değişiklikleri kaydetmeden zorla çıkar.
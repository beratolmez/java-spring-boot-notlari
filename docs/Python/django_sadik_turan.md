# Python Django Notları

---

## Proje ve Uygulama Oluşturma

* **Proje Oluşturma:** `django-admin startproject <proje_adı>` komutu, belirttiğiniz isimde bir ana proje klasörü oluşturur.
  * **Örnek:** `django-admin startproject movieapp`
* **Uygulama Oluşturma:** Django, küçük ve yönetilebilir alt uygulamalarla çalışır. Projenin tamamı bu uygulamaların birleşimiyle oluşur.
  * **Komut:** `python3 manage.py startapp <uygulama_adı>`
  * **Örnek:** `python3 manage.py startapp movies` veya `python3 manage.py startapp account`

## Ayarlar (Settings)

* Oluşturulan her yeni uygulamanın, projenin ana klasöründeki **`settings.py`** dosyası içinde bulunan **`INSTALLED_APPS`** dizisine eklenerek tanıtılması gerekir.

## Sunucuyu Çalıştırma

* **Komut:** `python3 manage.py runserver`
* Bu komut, geliştirme sunucusunu başlatır ve projenizin yerel ağda erişilebilir olmasını sağlar.

## Yönlendirmeler (URLs) ve Görüntüleme (Views)

* **`urls.py`:** URL yönlendirmelerinin tanımlandığı dosyadır. Gelen bir URL isteğini hangi fonksiyona veya görünüme (view) yönlendireceğini belirtir.
* **`views.py`:** Gelen istekleri karşılayan ve bir HTTP yanıtı üreten fonksiyonların bulunduğu dosyadır. Genellikle dinamik verileri hazırlar ve bir HTML şablonuna gönderir.

## HTML Şablonları (Templates)

* HTML dosyaları genellikle projenizin `templates` klasöründe tutulur.
* `views.py` içindeki bir fonksiyon, `return render(...)` komutuyla bir HTML dosyası döndürür.

### Dinamik Veri Gönderme

* **Views'dan HTML'e:** `views.py` dosyasından HTML şablonuna dinamik veri göndermek için `render` fonksiyonuna bir `data` sözlüğü (`dict`) parametresi eklenir.
  * **Örnek:** `return render(request, "index.html", data)`
* **HTML İçinde Kullanım:** Gönderilen veriler, HTML şablonları içinde **for** döngüsü veya **if** koşul blokları gibi yapılarla manipüle edilebilir.
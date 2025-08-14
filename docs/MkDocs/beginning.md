# Yeni Bir Proje Oluşturma

Yeni bir proje oluşturmak oldukça basit. Aşağıdaki komutlar çalıştırılarak yeni bir proje oluşturulabilir.

```
mkdocs new my-project
cd my-project
```

mkdocs.yml adında bir konfigrasyon dosyası ve içinde index.md markdown dosyası bulunan "docs" adında bir klasör oluşturacaktır. "docs" klasörü gerekli kaynak dosyalarını barındırır. Bu klasörün varsayılan ayarı mkdocs.yml konfigrasyon dosyasında, docs_dir değeri altında değiştirilebilir.

Sunucuyu başlatmak için aşağıdaki komutu çalıştırabilirsiniz:  

```
mkdocs serve
```

Yaklaşık olarak şöyle bir çıktı alınacaktır:

```
INFO    -  Building documentation...
INFO    -  Cleaning site directory
INFO    -  Documentation built in 0.22 seconds
INFO    -  [15:50:43] Watching paths for changes: 'docs', 'mkdocs.yml'
INFO    -  [15:50:43] Serving on http://127.0.0.1:8000/
```

Tarayıcıda http://127.0.0.1:8000/ url'sini açın ve varsayılan sayfayı görüntüleyin.
Sunucunun otomatik yeniden yükleme özelliği sayesinde, dökümanlardaki değişiklik sonucunda, sayfayı yenilediğiniz taktirde sunucu hemen sayfayı güncelleyecektir.
Aşağıda örnek yönlendirme ayarları bulunmaktadır:

```
nav:
  - Home: index.md
  - About: about.md
```


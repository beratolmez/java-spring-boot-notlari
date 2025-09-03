# MkDocs Notları

## Yeni Bir Proje Oluşturma
Yeni bir proje oluşturmak oldukça basit. Aşağıdaki komutları çalıştırarak yeni bir proje oluşturulabilir:

```bash
mkdocs new my-project
cd my-project
```

Bu işlem sonucunda:
- `mkdocs.yml` adında bir konfigrasyon dosyası,
- İçinde `index.md` markdown dosyası bulunan `docs` adında bir klasör  
oluşturulacaktır.  

`docs` klasörü gerekli kaynak dosyalarını barındırır. Bu klasörün varsayılan ayarı `mkdocs.yml` konfigrasyon dosyasında `docs_dir` değeri altında değiştirilebilir.

### Sunucuyu Başlatmak
```bash
mkdocs serve
```

Örnek çıktı:
```
INFO    -  Building documentation...
INFO    -  Cleaning site directory
INFO    -  Documentation built in 0.22 seconds
INFO    -  [15:50:43] Watching paths for changes: 'docs', 'mkdocs.yml'
INFO    -  [15:50:43] Serving on http://127.0.0.1:8000/
```

Tarayıcıda [http://127.0.0.1:8000/](http://127.0.0.1:8000/) adresini açarak varsayılan sayfayı görüntüleyebilirsiniz.  

Sunucunun **otomatik yeniden yükleme** özelliği sayesinde, dokümanlarda yapılan değişiklikler sayfayı yenilediğinizde hemen güncellenir.

### Örnek Yönlendirme Ayarları
```yaml
nav:
  - Home: index.md
  - About: about.md
```

### Konfigürasyon Parametreleri
- **Zorunlu:** `site_name` (Sitenin adı)
- **Opsiyonel:** `theme`, `nav`, `repo_url`, vb.

### Arama Fonksiyonu
Ekstra ayar gerektirmeksizin çalışır.

### Tema Değiştirme
```yaml
theme: readthedocs
```

Favicon değiştirmek için `img` klasörüne istediğiniz simgeyi koyabilirsiniz.  

---

## Dökümantasyonu Yayınlamak
Dökümantasyonu build etmek için:

```bash
mkdocs build
```

Bu işlem `site` adında yeni bir dizin oluşturur. İçerisinde:
- `index.html`
- `about/index.html`
- medya dosyaları ve temalar  

yer alır.

---

## Notlar
### Windows Kullanıcıları
Ortam değişkeni sorunlarından dolayı komutlar çalışmazsa şu şekilde kullanılabilir:
```bash
python -m mkdocs serve
```

### Gizli Dosyalar
`.` (nokta) ile başlayan dosya ve dizinler yok sayılır.  
Gerekirse `exclude_docs` ile değiştirilebilir.

---

## URL Yönlendirmeleri
Dosya isimlerine göre otomatik URL alınır.  
Örn: `about.md` → `/about/`

Alt başlıklar ile yönlendirme örneği:

```yaml
nav:
  - Home: index.md
  - User Guide:
    - Writing your docs: writing-your-docs.md
    - Styling your docs: styling-your-docs.md
  - About:
    - License: license.md
    - Release Notes: release-notes.md
```

---

## Markdown Yazımı

### Link
```markdown
Please see the [project license](license.md) for further details.
```

### Tablo
```markdown
First Header | Second Header | Third Header
------------ | ------------- | ------------
Content Cell | Content Cell  | Content Cell
Content Cell | Content Cell  | Content Cell
```

---

## Metadata
### YAML Biçimi
```yaml
---
title: My Document
summary: A brief description
authors:
    - Waylan Limberg
    - Tom Christie
date: 2018-07-10
some_url: https://example.com
---
```

### MultiMarkdown
```
Title:   My Document
Summary: A brief description
Authors: Waylan Limberg, Tom Christie
Date:    January 23, 2018
```

---

## Kod Blokları
```python
def fn():
    pass
```

---

## Tema Yapılandırması
```yaml
theme:
  name: readthedocs
  color_mode: auto
  user_color_mode_toggle: true
  nav_style: primary
  highlightjs: true
  hljs_languages:
    - yaml
    - rust
```

Google Analytics entegrasyonu:
```yaml
theme:
  name: mkdocs
  analytics:
    gtag: G-ABC123
```

Kısayol örneği:
```yaml
shortcuts:
  help: 191
  next: 78
  previous: 80
  search: 83
```

---

## CLI Komutları
- `mkdocs build` → Projeyi inşa eder.
- `mkdocs get-deps` → Gerekli PyPI paketlerini gösterir.
- `mkdocs gh-deploy` → GitHub Pages’e gönderir.
- `mkdocs new` → Yeni proje açar.
- `mkdocs serve` → Geliştirme sunucusunu çalıştırır.

---

## Yayınlama
### GitHub Pages
```bash
mkdocs gh-deploy
```

### Organization / User Pages
```bash
cd ../orgname.github.io/
mkdocs gh-deploy --config-file ../my-project/mkdocs.yml --remote-branch master
```

### Custom Domain
Bir `CNAME` dosyası oluşturup ekleyin.

### Read the Docs
Ücretsiz barındırma sağlar.

---

## Tema Özelleştirme
```yaml
extra_css:
  - style.css
```

Ekstra sosyal medya ikonları:
```yaml
extra:
  social:
    - icon: simple/youtube
      link: https://www.youtube.com/watch?v=xlABhbnNrfI
```

---

## İleri Seviye Örnekler
### Bölümleme
```markdown
=== "Plain text"
    This is some plain text

=== "Unordered list"
    * First item
    * Second item
    * Third item
```

### Bilgi Kutuları
```markdown
!!! note "Başlık"
    Açıklama buraya gelir.

??? info "Ek bilgi"
    Detaylar buraya gelir.
```

### Mermaid Diyagramları
Kod blokları içerisinde kullanılabilir.

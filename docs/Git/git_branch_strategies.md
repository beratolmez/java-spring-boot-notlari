# Branch Stratejileri

Büyük ekiplerde ve uzun ömürlü projelerde **branch stratejisi**, projeyi temiz ve yönetilebilir tutar.

---

### 🔹 1. Git Flow

* Branch yapısı:

  * `main` → stabil, üretime hazır kod
  * `develop` → geliştirme branch’i
  * `feature/*` → yeni özellik branch’i
  * `release/*` → sürüm hazırlıkları
  * `hotfix/*` → acil düzeltmeler
* Workflow:

  1. Feature branch’ini `develop`’den oluştur
  2. Feature tamamlanınca `develop`’e merge et
  3. Release hazırsa `main`’e merge ve tag ekle

---

### 🔹 2. Trunk-Based Development

* Kısa ömürlü feature branch’ler
* Sık sık main’e merge edilir (daily/continuous integration)
* CI/CD ile testler otomatik çalışır
* Büyük projelerde hızlı deploy için tercih edilir

---

### 🔹 3. Avantajlar

| Strateji    | Avantajlar                                      |
| ----------- | ----------------------------------------------- |
| Git Flow    | Branch’ler net, sürüm takibi kolay              |
| Trunk-Based | Hızlı deploy, sık entegrasyon, CI/CD ile uyumlu |

---

### Mini Test

* Diyelim ki ekipte çalışıyorsun ve **feature branch’ler uzun süre main’den ayrılıyor**.
* Merge yaparken çatışmalar çok çıkıyor.
* Hangi strateji, çatışmaları azaltmak için daha uygun olur?

A) Git Flow
B) Trunk-Based Development
C) Herkes direkt main’e commit yapmalı

* Cevap: **A) Git Flow**
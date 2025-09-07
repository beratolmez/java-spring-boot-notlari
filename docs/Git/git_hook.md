# 🔎 Git Hook’lar

**Amaç:**

* Git işlemleri sırasında **otomatik scriptler çalıştırmak**.
* Örneğin: commit etmeden önce testleri çalıştırmak, mesaj formatını kontrol etmek, push öncesi linter çalıştırmak gibi.

### Hook Türleri

* `.git/hooks/` klasöründe bulunurlar.
* Örnekler:

  * `pre-commit` → Commit işlemi başlamadan önce çalışır.
  * `commit-msg` → Commit mesajını kontrol eder.
  * `pre-push` → Push işleminden önce çalışır.

### Basit Örnek

* `pre-commit` hook ile Python dosyalarında syntax hatası varsa commit’i durdurmak:

```bash
#!/bin/sh
flake8 . || exit 1
```

* Bu dosyayı `.git/hooks/pre-commit` içine koy ve **çalıştırılabilir yap**:

```bash
chmod +x .git/hooks/pre-commit
```

---

## 🔎 Branch Stratejileri

**Amaç:**

* Büyük ekiplerde branch yönetimini düzenli hale getirmek.
* En popüler stratejiler:

1. **Git Flow**

   * `main` → stabil kod
   * `develop` → geliştirme branch’i
   * `feature/*` → yeni özellik branch’i
   * `release/*`, `hotfix/*` → sürüm ve acil düzeltmeler

2. **Trunk-Based Development**

   * Kısa-lived feature branch’ler, sık merge
   * Continuous Integration ve deployment (CI/CD) ile hızlı teslim

---

### 🔑 Özet Avantajlar

* Hook’lar → Süreçleri otomatikleştirir, hata olasılığını düşürür.
* Branch stratejileri → Ekip projelerinde kaosu önler, merge/rebase çatışmalarını azaltır.

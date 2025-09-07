# Git Stash

**Amaç:**

* Çalışma alanındaki değişiklikleri **geçici olarak kenara almak**.
* Commit etmeden branch değiştirmek veya acil başka bir iş yapmak gerektiğinde kullanılır.

### Temel Komutlar

1. **Değişiklikleri saklamak**

```bash
git stash
```

* Tüm tracked dosyalar stash’e alınır.
* Çalışma dizini temizlenir → branch değiştirebilirsin.

2. **Saklanan stash’leri listelemek**

```bash
git stash list
```

* Örn: `stash@{0}: WIP on feature-login: 123abc Commit mesajı`

3. **Saklanan stash’i geri almak**

```bash
git stash apply
```

* Son stash’i uygular, stash listesinde kalır.

4. **Saklanan stash’i geri al ve listeden sil**

```bash
git stash pop
```

5. **Belirli stash’i uygulamak**

```bash
git stash apply stash@{2}
```

---

### 🔑 İpuçları

* `git stash` → çalışma alanını temizler, commit etmeden branch değiştirmene izin verir.
* Stash’ler geçici, unutulursa kaybolabilir.

---

### Mini Test

* Diyelim ki `feature-login` branch’inde çalışıyorsun.
* Bazı dosyaları değiştirdin ama commit yapmak istemiyorsun.
* Ama **main branch’e geçmen gerekiyor**.

Hangi komutu kullanırsın?

A) `git reset --soft`
B) `git stash`
C) `git commit --amend`

Cevap: **B) `git stash`**

* `git stash` → Çalışma alanındaki değişiklikleri geçici olarak saklar, böylece **branch değiştirebilirsin**.
* `git reset --soft` → Commit geçmişini değiştirir, branch değiştirmek için uygun değil.
* `git commit --amend` → Son commit’i düzenler, değişiklikleri saklamak için değil.

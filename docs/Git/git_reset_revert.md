# Commit’e Geri Dönmek ve Commit Silmek

Git’te “geçmişi değiştirme” ile ilgili birkaç farklı komut var. Aralarındaki farkı anlamak çok önemli.

---

## 🔹 git reset

* Commit geçmişini **geri alır**, çalışma dizini veya staging area’yı değiştirebilir.
* 3 türü vardır:

1. **--soft**

```bash
git reset --soft <commit-hash>
```

* Commit’leri geri alır ama değişiklikler **staging area’da kalır**.
* Yani tekrar commit edebilirsin.

2. **--mixed** (default)

```bash
git reset <commit-hash>
```

* Commit’leri geri alır, değişiklikler **staging area’dan çıkar**, çalışma dizininde kalır.
* `git status` ile fark görebilirsin.

3. **--hard**

```bash
git reset --hard <commit-hash>
```

* Commit’leri geri alır, staging ve çalışma dizinindeki değişiklikleri **tamamen siler**.
* Dikkat: Kaybolan değişiklikler kurtarılamaz!

---

## 🔹 git revert

* Mevcut commit’i **tersine çeviren yeni bir commit** oluşturur.
* Commit geçmişi **bozulmaz**, ekip projeleri için güvenli.

```bash
git revert <commit-hash>
```

---

### 🔹 Farklar

| İşlem      | Commit geçmişi değişir mi? | Staging/Çalışma dizini etkilenir mi? |
| ---------- | -------------------------- | ------------------------------------ |
| git reset  | Evet                       | Evet                                 |
| git revert | Hayır                      | Evet (yeni commit oluşturur)         |

### Mini Test

Diyelim ki son commit’inde yanlış bir kod var ve **henüz push etmedin**.

* Commit’i tamamen silmek ve değişiklikleri kaybetmek istemiyorsun.
  Hangi komutu kullanırsın?

A) `git reset --hard HEAD~1`
B) `git reset --soft HEAD~1`
C) `git revert HEAD`

Hangi seçeneği seçerdin?

* `git revert HEAD` → Son commit’i **tersine çeviren yeni bir commit** oluşturur, böylece commit geçmişi bozulmaz.
* `git reset --soft HEAD~1` → Commit’i geri alır ama değişiklikler staging area’da kalır.
* `git reset --hard HEAD~1` → Commit ve değişiklikler tamamen silinir, geri alınamaz.

---

💡 Özet:

* Ekip projelerinde **asla `--hard reset` ile geçmişi değiştirme**. Commit geçmişi bozulur ve diğerlerini etkileyebilir.
* Lokal branch’te ve tek başına çalışıyorsan `reset` kullanmak güvenlidir.

# 🌟 Senaryo: Model Geliştirme Projesi

* Projede:

  * `main` → production-ready branch
  * `develop` → geliştirme branch’i
  * `feature/*` → yeni modeller veya özellikler

* Ek olarak **CI/CD ve LFS** kullanılıyor çünkü büyük model dosyaları var.

---

## 1️⃣ Feature Branch Oluşturma

* Yeni bir model ekleyeceğiz (`feature-new-model`)

```bash
git checkout develop
git checkout -b feature-new-model
```

* Feature branch’i develop’in mevcut commit’inden başlar.
* LFS ile model dosyalarını takip et:

```bash
git lfs track "*.h5"
git add .gitattributes
git commit -m "LFS ile model dosyalarını takip et"
```

---

## 2️⃣ Geliştirme ve Commit

* Model dosyalarını ekle, veri hazırlık script’leri commit et:

```bash
git add model_v2.h5
git commit -m "Yeni model v2 eklendi"
```

* Eğer çalışma devam ederken main veya develop branch’inde değişiklik geldiyse:

```bash
git fetch origin
git rebase origin/develop
# veya
git merge origin/develop
```

---

## 3️⃣ Stash Kullanımı

* Eğer acil bir bugfix yapmak zorundaysan ve feature branch’inde bitmemiş değişiklikler varsa:

```bash
git stash
git checkout hotfix
# bug fix işlemleri
git commit -m "Hotfix uygulandı"
git checkout feature-new-model
git stash pop
```

---

## 4️⃣ Cherry-Pick Kullanımı

* Diyelim ki feature branch’inde bir commit, hotfix branch’ine de gerekli:

```bash
git checkout hotfix
git cherry-pick <commit-hash>
```

---

## 5️⃣ Tag ve Release

* Feature tamamlandı, develop’e merge edildi, testler geçti:

```bash
git checkout develop
git merge feature-new-model
git checkout main
git merge develop
git tag -a v2.0 -m "Model v2 release"
git push origin main --tags
```

---

## 6️⃣ Hook ve CI/CD

* Commit öncesi testler için `pre-commit` hook
* Push öncesi `pre-push` hook ile linter veya model testleri çalıştırılır
* CI/CD pipeline:

  * Commit veya PR açıldığında testler otomatik çalışır
  * Model deployment pipeline’ı tetiklenir

---

🎯 **Özet Workflow**

1. Develop’den feature branch aç
2. Geliştirme yap, commit ve LFS kullan
3. Main/develop güncel mi kontrol et → rebase/merge
4. Acil durum → stash ve hotfix
5. Gerekirse cherry-pick ile commit’i başka branch’e al
6. Feature tamamlandı → develop/main’e merge
7. Tag oluştur → release hazır

---

Bu workflow’u anladığını kontrol etmek için mini test:

* Diyelim ki yeni bir model geliştirdin ve commit yaptın.
* Ama develop branch’inde **2 yeni commit** gelmiş.
* Feature branch’in temiz ve güncel olsun istiyorsun.
  Hangi adımı uygularsın?

A) `git push origin feature-branch`
B) `git merge origin/develop` veya `git rebase origin/develop`
C) `git reset --hard HEAD~2`

Hangi seçeneği seçerdin?

* Cevap **B) `git merge origin/develop` veya `git rebase origin/develop`**

* `git merge origin/develop` → Feature branch’in üzerine develop’daki yeni commit’leri ekler, commit geçmişi dallı olur.
* `git rebase origin/develop` → Feature branch’in commit’lerini develop’ın en sonuna taşır, commit geçmişi **düz ve temiz** olur.
* `git push` → Sadece branch’i uzak repo’ya gönderir, branch’in güncel olup olmadığına bakmaz.
* `git reset --hard` → Geçmişi siler, kaybolan commit’ler geri alınamaz; ekip projelerinde riskli.
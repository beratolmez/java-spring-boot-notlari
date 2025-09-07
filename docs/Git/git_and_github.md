# Git ve GitHub

Git, yazılım projelerinde yapılan değişiklikleri izlemek ve yönetmek için kullanılan, dağıtık bir sürüm kontrol sistemidir. GitHub ise bu projelerin internet üzerinde barındırıldığı popüler bir platformdur.

---

## Temel Kurulum ve Komutlar

* **`git config --global user.name "[adınız]"`**: Git için global kullanıcı adınızı ayarlar.
* **`git config --global user.email "[e-postanız]"`**: Git için global e-posta adresinizi ayarlar.
* **`git init`**: Bulunduğunuz klasörü bir Git deposu (`repository`) haline getirir.
* **`git status`**: Çalışma dizininizdeki ve geçici alandaki (`staging area`) dosyaların durumunu gösterir.
* **`git add .`**: Mevcut dizindeki tüm dosyaları takip etmek üzere geçici alana ekler.
* **`git commit -m "[mesajınız]"`**: Geçici alandaki değişiklikleri bir anlık görüntü olarak kaydeder.

---

## Branch Yönetimi ve Uzak Depolar

**Branch'ler (Dallar)**, bir projenin ana kodundan bağımsız olarak çalışabileceğiniz paralel çalışma alanlarıdır.

* **`git branch`**: Yerel deponuzdaki tüm dalları listeler.
* **`git switch -c feature/login-system`**: `feature/login-system` adında yeni bir dal oluşturur ve o dala geçer.
* **`git remote add origin [repo-url]`**: Yerel deponuzu, `origin` adında uzak bir depoyla ilişkilendirir.
* **`git push -u origin master`**: Yerel değişiklikleri `origin` adlı uzak deponun `master` dalına gönderir.
* **`git fetch`**: Uzak depodaki güncellemeleri yerel kopyanıza indirir ancak çalışma dizininizdeki dosyalarla birleştirmez.
* **`git merge`**: İndirilen değişiklikleri mevcut dalınızla birleştirir.
* **`git pull`**: **`git fetch`** ve **`git merge`** komutlarını birleştirerek, uzak depodaki güncellemeleri alır ve mevcut dalınıza otomatik olarak entegre eder.
* **`git clone [repo-url]`**: Uzak bir depodaki tüm projeyi bilgisayarınıza indirir.
* **`git rebase`**: Bir dalın commit geçmişini, başka bir dalın üzerine taşıyarak daha temiz ve doğrusal bir geçmiş oluşturur.

---

## İleri Seviye Komutlar ve Geçmiş Yönetimi

* **`git log`**: Çalıştığınız dalın tüm commit geçmişini görüntüler.
* **`git show <commit-hash>`**: Belirtilen commit'in detaylarını (hangi dosyada ne değişmiş, mesaj, tarih, yazar vs.) gösterir.
* **`git diff`**: Yapılan değişiklikleri satır bazında gösterir. **`git diff [dosya-adı]`** ile belirli bir dosyadaki değişiklikleri görebilirsiniz.
* **`git restore`**: Çalışma dizinindeki değiştirilmiş bir dosyayı son kaydedilen haline döndürür.
* **`git reset`**: Bir dosyayı geçici alandan çıkarır veya belirli bir commite geri döner.
* **`git stash`**: Değişiklikleri saklar.
* **`git stash list`**: Saklanan değişiklikleri listeler.
* **`git stash apply`**: En son saklanan değişikliği geri getirir.
* **`git commit --amend`**: En son commit'in mesajını veya içeriğini günceller.
* **`git checkout [hash-id]`**: Belirli bir commit'in durumuna geçiş yapar.
* **`git revert [hash-id]`**: Belirli bir commiti geri almak için, o commit'in tam tersi yönde yeni bir commit oluşturur. Bu, geçmişi silmeden değişiklikleri geri almanın güvenli bir yoludur.
* **`git reflog`**: Git'teki tüm başlıkların (`HEAD`) hareket geçmişini kaydeder. Yanlışlıkla silinen commit'leri bulmak için çok kullanışlıdır.
* **`git cherry-pick <commit-hash>`**: Sadece belirli comiti alıp branch'e uygular.
* **`git tag v1.0`**: Sadece commit'e bir isim verir, ekstra bilgi içermez.
* **`git tag -a v1.0 -m "İlk stabil sürüm"`**: Commit'e ek olarak **yazar**, **tarih**, **mesaj** bilgisi ekler.

---

## AI ile README Dosyası Oluşturma

**`readmeai`** gibi araçlar, yapay zeka kullanarak projeleriniz için otomatik olarak açıklama dosyaları (`README.md`) oluşturmanıza yardımcı olur. Bu araçları kullanmak için genellikle **Ollama** gibi yerel bir dil modeline ihtiyacınız vardır.

* **`ollama serve`**: Bir HTTP sunucusu başlatarak yerel dil modelinin API çağrılarına hazır hale gelmesini sağlar.
* **`ollama run llama3`**: `llama3` gibi belirli bir modeli çalıştırır.
* **`readmeai --api ollama --model llama3 -r [repo-url]`**: Belirtilen depoyu, `ollama` üzerindeki `llama3` modelini kullanarak analiz eder ve bir README dosyası oluşturur.

---

## GitHub Cli ile İşlemler

* **`gh issue create`**: Mevcut proje ile ilgili bir issue açmaya yarar.
* **`gh issue list`**: Issueleri listeler.
* **`gh issue view [issue number]`**: Belirtilen issue içeriğini görüntüler.
* **`gh issue edit [issue number] --add-assignee @me`**: Issue kendine atar.
* **`gh pr create`**: Pull request oluşturur.
* **`gh pr list`**: Pull requestleri listeler.
* **`gh pr merge --delete-branch`**: Kullanılmayan branch'i siler.
* **`gh pr create`**: Pull request oluşturur.

---

## .gitignore Kullanımı

* **`.gitignore:`** 
  - Bu dosya, Git’e “şu dosya ya da klasörleri takip etme” demenin yoludur.

  - Proje kök dizinine .gitignore adında bir dosya açarsın.

  - İçine yazdığın kurallar, Git’in git add . ile staging area’ya dosyaları alırken görmezden gelmesini sağlar..

* Tek bir dosyayı yok saymak için sadece dosyanın ismini yazmanız yeterli: `data.csv`
* Bir klasörü yok saymak: `logs/`
* Belirli bir uzantıya sahip tüm dosyaları yok saymak: `*.log`
* İstisna yapmak istenirse:
```
*.log
!important.log
```
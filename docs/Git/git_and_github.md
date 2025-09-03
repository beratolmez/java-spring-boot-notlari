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
* **`git diff`**: Yapılan değişiklikleri satır bazında gösterir. **`git diff [dosya-adı]`** ile belirli bir dosyadaki değişiklikleri görebilirsiniz.
* **`git restore`**: Çalışma dizinindeki değiştirilmiş bir dosyayı son kaydedilen haline döndürür.
* **`git reset`**: Bir dosyayı geçici alandan çıkarır veya belirli bir commite geri döner.
* **`git commit --amend`**: En son commit'in mesajını veya içeriğini günceller.
* **`git checkout [hash-id]`**: Belirli bir commit'in durumuna geçiş yapar.
* **`git revert [hash-id]`**: Belirli bir commiti geri almak için, o commit'in tam tersi yönde yeni bir commit oluşturur. Bu, geçmişi silmeden değişiklikleri geri almanın güvenli bir yoludur.
* **`git reflog`**: Git'teki tüm başlıkların (`HEAD`) hareket geçmişini kaydeder. Yanlışlıkla silinen commit'leri bulmak için çok kullanışlıdır.

---

## AI ile README Dosyası Oluşturma

**`readmeai`** gibi araçlar, yapay zeka kullanarak projeleriniz için otomatik olarak açıklama dosyaları (`README.md`) oluşturmanıza yardımcı olur. Bu araçları kullanmak için genellikle **Ollama** gibi yerel bir dil modeline ihtiyacınız vardır.

* **`ollama serve`**: Bir HTTP sunucusu başlatarak yerel dil modelinin API çağrılarına hazır hale gelmesini sağlar.
* **`ollama run llama3`**: `llama3` gibi belirli bir modeli çalıştırır.
* **`readmeai --api ollama --model llama3 -r [repo-url]`**: Belirtilen depoyu, `ollama` üzerindeki `llama3` modelini kullanarak analiz eder ve bir README dosyası oluşturur.
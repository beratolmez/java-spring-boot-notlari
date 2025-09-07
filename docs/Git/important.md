# Önemli Bilgiler

## `fetch` + `merge` = `pull`:

* **`git fetch`** komutu uzak repodaki değişiklikleri edinir, yerel repoya dosya indirmez, sadece günlükleri edinir. 
* **`git merge`** komutu ise yapılan değişiklikleri uzak repodan çekeren yerel repoya belirtilen branch ile birleştirmek adına indirir. 
* **`git pull`** komutu ise **`git fetch`** ve **`git merge`** komutunun yaptığı işi tek başına yapar.

## Versiyon Hatalarını Gidermek

* **`git pull`** veya **`git merge`** yapıldığı esnada işlem yapılan daldaki versiyonun ileride olması durumunda hata veya uyarı çıkabilir.
* Bu gibi bir birleştirilmek istenen branche geçilip önce güncellemeler alınmalı, sonra birleştirilmeli:
1. **`git checkout <diğer branch>`**
2. **`git pull <diğer branch>`**
3. **`git merge <çalışılan branch`**
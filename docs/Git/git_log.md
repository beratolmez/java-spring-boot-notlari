# git log

* `git log` sadece **commit edilmiş değişikliklerin geçmişini** gösterir.

---

* 🔎 `git log` çıktısı

Örneğin şöyle görünür:

```
commit 1a2b3c4d5e...
Author: Berat Ölmez <berat@example.com>
Date:   Sat Sep 6 17:00 2025 +0300

    ilk commit
```

Gösterdiği bilgiler:

* **commit hash’i** (her commit’e özel uzun bir kimlik numarası)
* **author** (kim commit etti)
* **tarih**
* **commit mesajı**

Bunun yanında farklı parametrelerle daha okunabilir hale getirirsin:

* `git log --oneline` → her commit’i tek satırda özetler.
* `git log --graph --oneline --decorate --all` → branch yapısını görsel olarak gösterir (en sevilen komutlardan biridir).

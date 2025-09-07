# 🔎 Git Tag

**Amaç:**

* Önemli commit’lere **etiket (tag)** vermek.
* Örneğin: bir projede “v1.0” sürümü, bir modelin final hali gibi commit’leri işaretlemek için kullanılır.

### Temel Tag Türleri

1. **Lightweight Tag**

* Sadece commit’e bir isim verir, ekstra bilgi içermez.

```bash
git tag v1.0
```

2. **Annotated Tag**

* Commit’e ek olarak **yazar, tarih, mesaj** bilgisi ekler.

```bash
git tag -a v1.0 -m "İlk stabil sürüm"
```

---

### Tag’leri Gösterme ve Kullanma

* Tüm tag’leri listeleme:

```bash
git tag
```

* Tag’li commit’i inceleme:

```bash
git show v1.0
```

* Tag’i uzak repoya gönderme:

```bash
git push origin v1.0
```

* Tüm tag’leri gönderme:

```bash
git push origin --tags
```

---

### 🔑 Avantajları

* Sürüm takibi kolaylaşır → “hangi commit modeli eğitip deploy ettim” gibi sorular hızlı cevaplanır.
* Team workflow’larda release yönetimini netleştirir.
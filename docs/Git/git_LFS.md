# Büyük Repo Yönetimi ve Git LFS

### Sorun

* Yapay zekâ projelerinde modeller, dataset’ler ve ağırlık dosyaları genellikle **gigabaytlarca** olabilir.
* Normal commit ile eklersen repo çok yavaşlar ve clone/pull işlemleri zorlaşır.

---

### Çözüm: Git LFS

1. Git LFS’yi yükle:

```bash
git lfs install
```

2. Takip edilecek dosya tiplerini ekle:

```bash
git lfs track "*.h5"
git lfs track "*.pt"
```

3. `.gitattributes` dosyası oluşur, bunu commit et:

```bash
git add .gitattributes
git commit -m "LFS ile model dosyalarını takip et"
```

4. Artık büyük dosyaları normal commit gibi ekleyebilirsin:

```bash
git add model_v1.h5
git commit -m "Model v1 eklendi"
git push origin main
```

* Repo hafif kalır, dosyalar ayrı LFS storage’da tutulur.
* Takım arkadaşları da LFS ile kolayca çekebilir.
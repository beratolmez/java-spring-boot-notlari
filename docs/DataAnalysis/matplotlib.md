# Matplotlib ile Veri Görselleştirme

Matplotlib, Python'da verileri görselleştirmek için kullanılan en popüler kütüphanelerden biridir. Çizgi grafiklerinden histogramlara kadar birçok farklı grafik türünü oluşturmanıza olanak tanır. Genellikle **NumPy** dizileriyle birlikte kullanılır.

### Kurulum ve Başlangıç

Öncelikle, Matplotlib kütüphanesini içeri aktarmanız gerekir.

```python
import matplotlib.pyplot as plt
```

Eğer Jupyter Notebook kullanıyorsanız, grafiklerin doğrudan çıktı hücresinde görünmesi için aşağıdaki sihirli komutu ekleyebilirsiniz:

```python
%matplotlib inline
```

### Basit Bir Çizgi Grafiği Oluşturma

Bir grafik oluşturmak için `plt.plot()` fonksiyonu kullanılır. Bu fonksiyon, x ve y ekseni değerlerini alır.

```python
# Örnek NumPy dizileri
numpyYasListesi = [20, 25, 30, 35, 40]
numpyKiloListesi = [70, 75, 80, 85, 90]

# Grafiği çizme
plt.plot(numpyYasListesi, numpyKiloListesi, "g") 
# "g" parametresi, çizginin rengini yeşil (green) yapar.

# Eksen ve başlık ekleme
plt.xlabel("Yaş")
plt.ylabel("Kilo")
plt.title("Kilo'nun Yaşa Göre Değişim Grafiği")
plt.show() # Grafiği göstermek için kullanılır
```

### Gelişmiş Grafik Oluşturma: `figure` ve `axes`

Daha fazla kontrol ve özelleştirme için `plt.figure()` ve `myFigure.add_axes()` fonksiyonlarını kullanabilirsiniz. Bu yöntem, bir figürün üzerine farklı grafikler eklemenize olanak tanır.

```python
# Bir figür ve axes (eksen) nesnesi oluşturma
myFigure = plt.figure()
figureAxes = myFigure.add_axes([0.2, 0.2, 0.9, 0.9])
# [0.2, 0.2, 0.9, 0.9] değerleri, grafiğin figür içindeki konumunu ve boyutunu belirler.

# Axes üzerine grafiği çizme
figureAxes.plot(numpyDizisi1, numpyDizisi2, "g")

# Axes'i özelleştirme
figureAxes.set_xlabel("X ekseni Veri İsmi")
figureAxes.set_ylabel("Y ekseni Veri İsmi")
figureAxes.set_title("Grafik Başlığı")
```

Bu yöntem, grafiği daha ayrıntılı bir şekilde kontrol etmenizi ve birden fazla grafiği aynı figür içinde konumlandırmanızı sağlar.
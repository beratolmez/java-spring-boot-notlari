# Veri Seti Üzerinde Çalışmak

-----

## 1\. Veri Hazırlığı ve İnceleme

### Gerekli Kütüphaneleri Yükleme

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sbn
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import MinMaxScaler
from sklearn.metrics import mean_squared_error, mean_absolute_error
from sklearn.metrics import classification_report, confusion_matrix
import tensorflow as tf
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Activation, Dropout
from tensorflow.keras.callbacks import EarlyStopping
```

### Veri Setini Okuma ve Tanıma

  * `dataFrame = pd.read_excel("merc.xlsx")`: Belirtilen Excel dosyasını bir DataFrame'e okur.
  * `dataFrame.head()`: Veri setinin ilk 5 satırını görüntüler.
  * `dataFrame.describe()`: Sayısal verilerin istatistiksel özetini (ortalama, standart sapma vb.) sunar.
  * `dataFrame.isnull().sum()`: Her sütundaki eksik (boş) veri sayısını gösterir.

### Veri Keşfi ve Temizliği

  * `dataFrame.corr()`: Sütunlar arasındaki korelasyon matrisini hesaplar.
  * `dataFrame.corr()["price"].sort_values()`: `price` sütunu ile diğer sütunlar arasındaki korelasyonu küçükten büyüğe sıralar.
  * `dataFrame.sort_values("price", ascending=False).head(20)`: En yüksek fiyatlı ilk 20 veriyi listeler.
  * `dataFrame.groupby("year").mean()["price"]`: Her yıla göre ortalama fiyatı hesaplar.
  * `dataFrame = dataFrame.drop("transmission", axis=1)`: Belirtilen sütunu veri setinden siler.

-----

## 2\. Model Oluşturma ve Eğitim (Regresyon Problemi)

Bu kısım, bir aracın fiyatını tahmin etme gibi bir regresyon problemi için yapay sinir ağı modelinin oluşturulmasını içerir.

### Veriyi Bölme ve Ölçeklendirme

  * `y = dataFrame["price"].values`: Tahmin edilecek bağımlı değişkeni (`price`) tanımlar.
  * `x = dataFrame.drop("price", axis=1).values`: Bağımsız değişkenleri (`price` hariç tüm sütunlar) tanımlar.
  * `x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.3, random_state=10)`: Veriyi %70 eğitim ve %30 test verisi olarak ayırır.
  * `scaler = MinMaxScaler()` ve `scaler.fit_transform(x_train)`: Verileri 0-1 aralığına normalize eder.

### Model Mimarisi

  * `model = Sequential()`: Ardışık katmanlardan oluşan bir model oluşturur.
  * `model.add(Dense(12, activation="relu"))`: 12 nöronlu, "relu" aktivasyon fonksiyonu kullanan gizli katmanlar ekler.
  * `model.add(Dense(1))`: Tek nöronlu çıktı katmanı ekler.
  * `model.compile(optimizer="adam", loss="mse")`: Modelin optimizasyon algoritmasını (`adam`) ve hata fonksiyonunu (`mse` - ortalama karesel hata) belirler.

### Model Eğitimi ve Değerlendirme

  * `model.fit(...)`: Modeli, eğitim verisi üzerinde belirli sayıda `epochs` (dönem) boyunca eğitir.
  * `kayipVerisi = pd.DataFrame(model.history.history)` ve `kayipVerisi.plot()`: Eğitim sırasındaki kayıp değerlerini grafiklendirir.
  * `tahminDizisi = model.predict(x_test)`: Test verileri üzerinde tahmin yapar.
  * `mean_absolute_error(y_test, tahminDizisi)`: Tahminlerin gerçek değerlere ne kadar yakın olduğunu ölçer.
  * `plt.scatter(y_test, tahminDizisi)`: Gerçek ve tahmin edilen değerleri bir dağılım grafiğiyle görselleştirir.
  * `model.predict(yeniArabaSeries)`: Yeni bir verinin fiyatını tahmin eder.

-----

## 3\. Sınıflandırma Problemi ve Model Oluşturma

Bu kısım, bir verinin iyi huylu mu yoksa kötü huylu mu olduğunu belirleme gibi bir sınıflandırma problemi için yapay sinir ağı modelinin oluşturulmasını içerir.

### Veri Hazırlığı

  * `dataFrame = pd.read_excel("maliciousornot.xlsx")`: Yeni veri setini okur.
  * `dataFrame.corr()["Type"].sort_values()`: `Type` (tür) sütununa göre korelasyonu inceler.
  * `sbn.countplot(x="Type", data=dataFrame)`: Veri setindeki her sınıfın sayısını görselleştirir.

### Model Mimarisi

  * `model.add(Dense(units=1, activation="sigmoid"))`: Çıktı katmanına, 0 ve 1 arasında sonuç üreten **`sigmoid`** aktivasyon fonksiyonu ekler.
  * `model.compile(loss="binary_crossentropy", optimizer="adam")`: İkili sınıflandırma için uygun olan **`binary_crossentropy`** hata fonksiyonunu kullanır.

### Model Eğitimi ve İyileştirme

  * `model.fit(...)`: Modeli eğitir.
  * `EarlyStopping(patience=25)`: Eğitim sırasında hata değeri belirli bir süre düşmediğinde eğitimi erken durdurur, böylece aşırı uyumu (overfitting) önler.
  * `model.add(Dropout(0.6))`: Her bir katmandan sonra nöronların rastgele bir kısmını kapatarak aşırı uyumu önler.

### Sonuçların Değerlendirilmesi

  * `tahminlerimiz = model.predict_classes(x_test)`: Test verileri üzerinde sınıf tahmini yapar.
  * `print(classification_report(y_test, tahminlerimiz))`: Modelin hassasiyet, duyarlılık ve F1-skoru gibi performans metriklerini içeren bir rapor sunar.
  * `print(confusion_matrix(y_test, tahminlerimiz))`: Tahminlerin ne kadar doğru veya yanlış olduğunu matris şeklinde gösterir.
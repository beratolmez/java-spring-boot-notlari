# TensorFlow ve Yapay Sinir Ağları

TensorFlow, makine öğrenmesi ve derin öğrenme modelleri oluşturmak için kullanılan açık kaynaklı bir kütüphanedir. Keras, TensorFlow'un üstüne inşa edilmiş, model oluşturmayı kolaylaştıran yüksek seviyeli bir API'dir.

---

## Yapay Sinir Ağı Oluşturma

Bir yapay sinir ağı modeli oluşturmak için `Sequential` modeli ve `Dense` katmanları kullanılır. `Sequential` modeli, katmanların sırayla eklenmesine olanak tanır. `Dense` katmanları ise tam bağlı katmanlardır.

* **`model = Sequential()`**: Boş bir sıralı model oluşturulur.
* **`model.add(Dense(4, activation="relu"))`**: Modele bir `Dense` (tam bağlı) katman eklenir.
    * `4`: Bu katmandaki nöron (hücre) sayısını belirtir.
    * `activation="relu"`: Nöronun çıktı değerini belirleyen aktivasyon fonksiyonudur. `relu` (Rectified Linear Unit), yaygın olarak kullanılan bir fonksiyondur.
* **`model.add(Dense(1))`**: Çıkış katmanı eklenir. Bu katmanın nöron sayısı, modelin tahmin etmesi istenen çıktının boyutuna göre ayarlanır. (Örnekte tek bir değer tahmin edildiği için 1'dir.)

---

## Modeli Derleme ve Eğitme

Modeli kullanmadan önce, öğrenme sürecini tanımlayan bazı parametrelerle **derlenmesi** (`compile`) ve ardından **eğitilmesi** (`fit`) gerekir.

* **`model.compile(optimizer="rmsprop", loss="mse")`**: Modeli derler.
    * **`optimizer`**: Ağırlıkların nasıl güncelleneceğini belirleyen algoritmadır. `rmsprop` yaygın kullanılan bir optimizasyon algoritmasıdır.
    * **`loss`**: Modelin tahmin hatasını ölçen fonksiyondur. `mse` (Mean Squared Error), regresyon problemlerinde kullanılan bir kayıp fonksiyonudur.
* **`model.fit(x_train, y_train, epochs=250)`**: Modeli eğitim verileri (`x_train`, `y_train`) ile eğitir.
    * **`x_train`**: Eğitim verisindeki özelliklerdir (girdi).
    * **`y_train`**: Eğitim verisindeki hedef değerlerdir (çıktı).
    * **`epochs`**: Eğitim verisinin modelden kaç kez geçirileceğini belirtir. 250 `epoch`, tüm verinin 250 kez kullanıldığı anlamına gelir.

---

## Veriyi Test ve Eğitim Olarak Ayırma

Bir modelin performansını değerlendirmek için verinin bir kısmını eğitim için, bir kısmını da test için ayırmak önemlidir.

* **`from sklearn.model_selection import train_test_split`**: Veri setini ayırmak için kullanılan bu fonksiyon `scikit-learn` kütüphanesinden dahil edilir.
* **`train_test_split()`**: Veri kümesini eğitim ve test kümelerine böler.
    * **Örnek:** `x_train, x_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)`

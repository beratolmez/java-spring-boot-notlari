# Pekiştirmeli Öğrenmeye Giriş

Pekiştirmeli öğrenme, bir **ajanın** çevresiyle etkileşime girerek belirli bir hedef doğrultusunda en iyi kararları almayı öğrendiği bir makine öğrenmesi alanıdır.

## Temel Bileşenler

1.  **Ajan (Agent):** Karar verici olarak hareket eden ve eylemleri seçen yapıdır. Çevreden etkilenerek öğrenir. Amacı kümülatif ödülü maksimize etmektir.
2.  **Çevre (Environment):** Ajanın etkileşimde bulunduğu ve durumunun gözlemlenebildiği dış dünyadır.
3.  **Ödül (Reward):** Ajanın her eylemden sonra aldığı geri bildirimdir. Amaç, toplam ödülü maksimize etmektir. Ceza ise negatif ödüldür.

---

## Önemli Kavramlar

* **Keşif (Exploration):** Ajanın yeni eylemleri deneyerek çevreyi ve potansiyel ödülleri keşfetmesidir.
* **Sömürü (Exploitation):** Ajanın en yüksek ödülü almak için mevcut bilgilerden yararlanmasıdır.
* **Epsilon ($\epsilon$):** Keşfetme olasılığını temsil eden bir parametredir. Yüksek $\epsilon$ değeri keşfi, düşük $\epsilon$ değeri ise sömürüyü teşvik eder.
* **Politika (Policy):** Ajanın belirli bir durumda hangi eylemi seçeceğini belirleyen stratejidir.
* **Durum (State):** Çevrenin anlık durumudur. Ajan kararlarını buna göre alır.
* **Aksiyon (Action):** Ajanın çevrede yapabileceği hareketlerdir.

---

## Pekiştirmeli Öğrenme Ortamları

### Gözlemlenebilirlik

* **Tam Gözlemlenebilir Ortam:** Ajan, ortamın tüm durumunu algılayabilir.
    * **Özellikler:** Belirsizlik yoktur, geçmişi hatırlamaya gerek yoktur.
* **Kısmen Gözlemlenebilir Ortam:** Ajan ortamın sadece bir kısmını gözlemleyebilir.
    * **Özellikler:** Belirsizlik vardır, geçmiş durumları hatırlamak önemlidir.

### Determinizm

* **Deterministik Ortam:** Ajanın her eylemi kesin ve öngörülebilir bir sonuç doğurur.
* **Stokastik Ortam:** Aynı durum ve eylem, belirsizlik ve rastgelelik nedeniyle farklı sonuçlar üretebilir.

### Ardışıklık

* **Epizodik Ortam:** Ajanın deneyimi bağımsız bölümlere (epizodlara) ayrılır. Her epizodun sonucu diğerini etkilemez.
* **Sıralı (Sekansiyel) Ortam:** Mevcut kararlar gelecekteki durumları ve kararları etkiler. Uzun vadeli planlama gerektirir.

---

## Markov Süreçleri

* **Markov Özelliği:** Gelecekteki bir durumun sadece şimdiki duruma bağlı olmasıdır.
* **Markov Zinciri:** Geçiş olasılıklarının bir durum şeması veya geçiş matrisi ile gösterildiği, hafızasız rassal bir süreçtir.
* **Durum Uzayı:** Markov sürecindeki tüm olası durumların kümesidir.
* **Geçiş Olasılığı:** Bir durumdan diğerine geçme olasılığıdır.
* **Markov Ödül Süreci (MRP):** Markov zincirine ödül (reward) kavramının eklenmiş halidir. Ancak eylem (action) kavramı yoktur.
* **Markov Karar Süreci (MDP):** MRP'nin eylem (action) içeren halidir. Ajan her adımda bir eylem seçer.

---

## Ödül (Reward) ve Getiri (Return)

* **Ödül (Reward):** Bir tekil eylemin hemen ardından alınan anlık geri bildirimdir.
* **Getiri (Return):** Bir noktadan sonra gelecekteki tüm ödüllerin toplamıdır. Ajanın asıl amacı getiriyi maksimize etmektir.

---

## Pekiştirmeli Öğrenme Algoritmaları

* **Dinamik Programlama (DP):** Problemi alt problemlere bölerek optimal çözümü bulur. Bu yöntem, ortamın tam modelini gerektirir (**Model Tabanlı**). **Bellman'ın Optimalite İlkesi** bu yaklaşımın temelini oluşturur.
* **Model-Free RL:** Ortamın özellikleri tam olarak bilinmediğinde kullanılır.
* **Değer Fonksiyonu:** Bir duruma nicel olarak değer vermek için kullanılır.

*Daha fazla bilgi için **Policy Iteration** ve **Value Iteration** konularını inceleyebilirsiniz.*
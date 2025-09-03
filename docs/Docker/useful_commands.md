# İşe Yarar Komutlar

## Docker

  * `docker compose up -d`: `docker-compose.yml` dosyasını kullanarak konteynerleri arka planda (`-d`) çalıştırır.
  * `docker buildx build -t <imaj_adı> .`: Bulunulan dizindeki `Dockerfile`'ı kullanarak bir Docker imajı oluşturur ve ona etiket (`-t`) verir.
  * `docker buildx build -t <imaj_adı> -f <Dockerfile_yolu> .`: Eğer `Dockerfile` adı veya konumu farklıysa, `-f` parametresiyle belirtilen dosyayı kullanarak imajı oluşturur.
  * `docker ps -a`: Çalışan ve durdurulmuş tüm Docker konteynerlerini listeler.
  * `docker exec -it <konteyner_adı_veya_id> bash`: Belirtilen konteynerin içine interaktif bir terminal (`-it`) açar. `bash` yerine başka bir komut da çalıştırılabilir.
  * `docker network connect --ip <ip_adresi> <ağ_adı> <konteyner_adı>`: Bir konteyneri, belirtilen IP adresiyle bir Docker ağına bağlar.

### Konteyner İçi Komutlar

  * `ip route`: Konteynerin routing tablosunu kontrol eder.
  * `iptables -L -n -v`: Konteynerin `iptables` kurallarını listeler. Bu komut, ağlar arası forwarding kurallarının aktif olup olmadığını doğrulamak için faydalıdır.

-----

## ROS2

  * `ros2 topic list`: Çalışan tüm ROS2 konularını (topics) listeler.
  * `ros2 node list`: Ağdaki tüm ROS2 düğümlerini (nodes) listeler.
  * `ros2 topic echo <topic_adı>`: Belirtilen konuya gönderilen mesajları terminalde görüntüler.
  * `ros2 topic pub <topic_adı> <mesaj_türü> "<mesaj>"`: Belirtilen konuya manuel olarak mesaj gönderir.
  * `ros2 run <paket_adı> <yürütülebilir_dosya>`: Belirli bir paketin içindeki yürütülebilir dosyayı (düğümü) çalıştırır.

### Örnek Kullanım Senaryosu

Aşağıdaki komutlar, farklı Docker konteynerleri arasında ROS2 iletişimi kurmak için kullanılabilir.

1.  **İstanbul'daki talker konteynerine bağlanma:**
    ```bash
    docker compose exec ros2_istanbul_talker_1 bash
    ```
2.  **Mesaj yayınlama:** `/foo` adlı konuya her saniye iki adet "Test Mesaj" gönderir.
    ```bash
    ros2 topic pub /foo std_msgs/String "data: 'Test Mesaj' " -r 2
    ```
3.  **Ankara'daki listener konteynerinden dinleme:** Başka bir terminalde `/foo` konusundaki mesajları görüntüler.
    ```bash
    ros2 topic echo /foo
    ```
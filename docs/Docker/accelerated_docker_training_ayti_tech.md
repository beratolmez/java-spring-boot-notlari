# Hızlandırılmış Docker Eğitimi

---

## Docker'ın Amacı ve Avantajları

Docker, uygulamaları sanal ortamda çalıştırmak için kullanılan bir konteyner teknolojisidir. Temel amaçları şunlardır:

* **Kaynak Verimliliği:** Sunucu kaynaklarının daha verimli kullanılmasını sağlar.
* **İzolasyon:** Her konteyner birbirinden izole olduğu için, birinde meydana gelen sorun diğerlerini etkilemez.
* **Çoklu Test İmkanı:** Aynı ortamda birden fazla testi kolayca çalıştırma imkanı sunar.

Yeni nesil sunucu yönetiminde, bir sorun yaşandığında eski konteyner onarılmaya çalışılmaz; bunun yerine hızla yeni bir konteyner oluşturulup eskisinin yerine geçirilir.

### Konteyner Dosya Sistemi

Konteynerler çalıştırıldığında, tüm dosyaları **salt okunur (read-only)** olur. Yeni eklenen veya değiştirilen dosyalar, konteynerin **yazılabilir (writable)** katmanında bulunur. Bu sisteme **Union File System** denir.

### Veri Yönetimi

Konteynerler kapatıldığında, içindeki verileri silinir. Verilerin kalıcı olması için **volume** adı verilen objeler kullanılır.

---

## Docker'ın Platformlara Göre Farkı

* **Linux için Docker:** Linux uygulamaları çalıştırır. İmaj boyutları daha küçüktür ve sadece imajı içerir. **Süreç (process) izolasyonu** kullanır.
* **Windows için Docker:** Windows uygulamaları çalıştırır. İmaj boyutları daha büyüktür çünkü hem imajı hem de işletim sistemini içerir. **Süreç izolasyonu** ile birlikte **sanallaştırma** teknolojisini de kullanır.

## Docker Kurulum ve Kontrol

* **Kurulum:** Windows'da **Docker Desktop** kurulur. Linux'ta ise **Docker Engine** indirilir.
* **Kurulum Kontrolü:**
    * `sudo docker run hello-world`: Kurulumun başarılı olduğunu doğrulamak için bir test konteyneri çalıştırır.
    * `docker version`: Docker'ın versiyon bilgilerini gösterir.
    * `docker info`: Docker sistemi hakkında ayrıntılı bilgi verir.

---

## Temel Docker Komutları

* `docker`: Kullanılabilecek tüm Docker komut ve parametrelerini listeler.
* `docker pull <imaj_adı>`: Docker Hub'dan belirtilen imajı yerel sisteme indirir.
* `docker ps`: Sistemde **çalışan** konteynerleri listeler.
* `docker ps -a`: Çalışan ve geçmişte çalışmış **tüm** konteynerleri listeler.
* `docker run --name <isim> <imaj_adı>`: Bir konteyneri isimlendirerek çalıştırır.
* `docker rm <isim/ID>`: Belirtilen konteyneri siler.
* `docker rm -f <isim/ID>`: Çalışan bir konteyneri zorla siler.
* `docker start <isim/ID>`: Durdurulmuş bir konteyneri yeniden başlatır.
* `docker logs <isim/ID>`: Konteynerin loglarını görüntüler.
* `docker logs -f <isim/ID>`: Logları canlı (stream) olarak izler.
* `docker run -d ...`: Konteyneri arka planda (detached) çalıştırır.
* `docker exec <isim/ID> <komut>`: Çalışan bir konteyner içinde komut çalıştırır.
* `docker exec -it <isim/ID> sh`: Çalışan bir konteynerin shell'ine bağlanır.
* `docker container inspect <ID>`: Konteyner hakkında detaylı bilgi verir.
* `docker top <isim/ID>`: Konteynerin içinde çalışan süreçleri listeler.
* `docker stats`: Sistemdeki tüm konteynerlerin kaynak kullanımını canlı olarak gösterir.
* `docker container prune`: Çalışmayan tüm konteynerleri siler.

### Kaynak (CPU & Memory) Sınırlandırma

* `docker container run ... --memory=256m --cpus="2"`: Konteynerin bellek ve işlemci kullanımını sınırlar.
* `docker container run ... --cpuset-cpus="1,3"`: Konteynerin sadece belirli işlemci çekirdeklerini kullanmasını sağlar.

### Çevre Değişkenleri (Environment Variables)

* `docker container run ... --env KEY1=value`: Çevre değişkeni atar.
* `docker container run ... --env-file <dosya_yolu>`: Bir dosyadan çevre değişkenlerini okuyup atar.

---

## Docker Ağları ve Depolama (Volume)

### Volume Oluşturma ve Kullanımı

* `docker volume create <isim>`: Kalıcı veri saklamak için bir volume oluşturur.
* `docker volume inspect <isim>`: Volume'un detaylarını inceler.
* `docker container run -v <volume_ismi>:/<bağlanacak_klasör> ...`: Konteyneri bir volume'a bağlar.

### Bind Mount

* `docker container run -v /<yerel_dizin>:/<konteyner_dizini> ...`: Yerel makinedeki bir dizini doğrudan konteynere bağlar.

### Ağ Tipleri (Docker Network)

* **Bridge:** Varsayılan ağ ayarıdır. Konteynerler kendi içinde bir köprü ağ oluşturur.
* **Host:** Konteynerler, ana makinenin (host) ağını kullanır.
* **MacVlan:** Her konteynere fiziksel ağ üzerinde bir MAC adresi atar.
* **None:** Konteynerin ağ bağlantısı olmaz.
* **Overlay:** Birden fazla Docker hostu üzerinde çalışan konteynerleri birbirine bağlar.

**Ağ Yönetimi Komutları:**
* `docker network ls`: Mevcut ağları listeler.
* `docker network inspect <ağ_adı>`: Bir ağ hakkında detaylı bilgi verir.
* `docker network create ...`: Yeni bir ağ oluşturur.
* `docker network connect <ağ_adı> <konteyner_adı>`: Çalışan bir konteyneri bir ağa bağlar.

### Port Yayınlama (Port Publishing)

* `docker run -p <host_portu>:<konteyner_portu> ...`: Ana makinenin portunu konteynerin portuna yönlendirir. Bu, dışarıdan erişim sağlar.

---

## Docker İmajları (Images) ve Dockerfile

* **İmaj İsimlendirme:** `kullanıcı/uygulama:versiyon` formatındadır. `/` içeren imajlar özel, içermeyenler ise resmi Docker Hub imajlarıdır.
* **İmaj Yönetimi:**
    * `docker image ls`: Yerel imajları listeler.
    * `docker image pull <imaj:tag>`: Belirli bir etikete (`tag`) sahip imajı indirir.
    * `docker image push <imaj:tag>`: Yerel imajı bir registry'ye yükler.
    * `docker image tag <eski_imaj:tag> <yeni_imaj:tag>`: Bir imaja yeni bir etiket ekler.

### Dockerfile Komutları

Bir Dockerfile, bir imaj oluşturmak için kullanılan talimatları içeren bir metin dosyasıdır.
* `FROM <imaj_adı>:<tag>`: İmajın hangi temel imajdan oluşturulacağını belirtir (Zorunludur).
* `RUN <komut>`: İmaj içinde bir komut çalıştırır.
* `WORKDIR /<dizin>`: Çalışma dizinini ayarlar.
* `COPY <kaynak> <hedef>`: Yerel dosyaları imaja kopyalar.
* `EXPOSE <port>`: Konteynerin dinleyeceği portları belirtir.
* `CMD <komut>`: Konteyner başlatıldığında çalışacak varsayılan komutu belirler.
* `HEALTHCHECK <komut>`: Konteynerin sağlık durumunu kontrol eder.

**İmaj Oluşturma Komutu:**
* `docker image build -t <repository:tag> .`: Bulunulan dizindeki `Dockerfile`'ı kullanarak bir imaj oluşturur.
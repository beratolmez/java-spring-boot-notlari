Aşağıda, Docker Compose notlarınızın Markdown formatına dönüştürülmüş halini bulabilirsiniz.

# Docker Compose

---

## Docker Compose Nedir?

**Docker Compose**, birden fazla **Docker** konteynerini veya birbirine bağımlı konteynerleri tek bir komutla yönetmenizi sağlayan bir araçtır. Bu konteynerler, bir `YAML` dosyasında tanımlanır.

---

## Temel Docker Compose Komutları

* `docker-compose up`: Belirtilen dizinde bulunan `docker-compose.yml` dosyasını çalıştırır ve tanımlı tüm servisleri (konteynerleri) başlatır.
* `docker-compose up -d`: Aynı işlemi yapar ancak konteynerleri arka planda (`-d` parametresi) başlatarak terminali serbest bırakır.
* `docker-compose down`: Çalışan veya durdurulmuş tüm Docker Compose konteynerlerini kapatır ve kaldırır.
* `docker-compose ps`: Sadece `docker-compose.yml` dosyasıyla başlatılmış konteynerlerin durumunu listeler.
* `docker-compose build <servis_adı>`: Belirtilen servisten yeni bir konteyner imajı oluşturur. Bu komutu çalıştırdıktan sonra `docker-compose up` komutu, yeni imajı kullanarak konteynerleri yeniden oluşturur.
* `docker-compose logs <konteyner_adı>`: Belirtilen konteynerin veya konteynerlerin loglarını görüntüler.
* `docker-compose stop <servis_adı>`: Çalışan bir servisi durdurmak için kullanılır.
* `docker-compose exec <servis_adı> <komut>`: Çalışmakta olan bir konteynerin içinde bir komut çalıştırmak için kullanılır.

---

## Docker Compose Dosya Yapısı

Bir `docker-compose.yml` dosyasının temel yapısı, konteynerleri, ağları ve depolama birimlerini tanımlayan etiketlerden oluşur.

* `services`: Konteynerlerin tanımını içerir. Her servis, bir Docker imajından oluşturulacak bir konteyneri temsil eder.
* `volumes`: Konteynerler arasında veri paylaşımını veya kalıcı depolama sağlamak için kullanılır.
* `networks`: Konteynerler arası iletişimi sağlamak için ağları tanımlar.
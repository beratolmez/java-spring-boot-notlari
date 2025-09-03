# DNS Değiştirme

Linux sistemlerde DNS (Domain Name System) ayarlarını değiştirmek için genellikle `/etc/dhcp/dhclient.conf` dosyasını düzenlemeniz gerekir.

-----

## 1\. DNS Ayarlarını Değiştirme

1.  Bir metin düzenleyici ile `dhclient.conf` dosyasını açın:
    ```bash
    nano /etc/dhcp/dhclient.conf
    ```
2.  Dosya içinde `#prepend domain-name-servers` satırını bulun.
3.  Bu satırın başındaki **yorum işareti (`#`)** kaldırın.
4.  Ardından, **istediğiniz DNS sunucusu adreslerini** aralarında virgül bırakarak yazın.
      * **Örnek:**
        ```bash
        prepend domain-name-servers 8.8.8.8, 8.8.4.4;
        ```
5.  Dosyayı kaydedin ve kapatın.

-----

## 2\. Ağ Bağlantısını Yeniden Başlatma

Yaptığınız değişikliklerin etkin olması için ağ bağlantısını yeniden başlatmanız gerekir. Bu işlemi aşağıdaki komutlarla gerçekleştirebilirsiniz:

1.  Ağ istemcisini serbest bırakın:
    ```bash
    dhclient -r
    ```
2.  Yeni ayarları alarak ağı yeniden başlatın:
    ```bash
    dhclient -v
    ```

Bu adımları tamamladığınızda, sisteminiz yeni DNS sunucularını kullanmaya başlayacaktır.
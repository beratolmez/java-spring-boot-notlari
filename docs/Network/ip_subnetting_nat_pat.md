# IP Subnetting, NAT ve PAT

---

## IP Subnetting (Alt Ağ Oluşturma)

**Neden kullanılır?**

* **IPv4 Adres Verimliliği:** Sınırlı IPv4 adreslerini daha verimli kullanmak için.
* **Trafik Azaltma:** Ağdaki broadcast (yayın) trafiğini azaltmak.
* **Yönetim Kolaylığı:** Ağı daha küçük, yönetilebilir parçalara ayırarak yönetimi kolaylaştırmak.
* **Güvenlik:** Her bir alt ağın izole edilerek güvenliğin artırılması.

### Subnet Mask (Alt Ağ Maskesi)
Bir IP adresinin hangi ağa ait olduğunu belirlemek için kullanılan 32-bitlik bir adrestir.

**Örnek:** `192.168.1.10/24` adresi için:
* **Ağ Adresi (Network Adresi):** `192.168.1.0`
* **Broadcast Adresi:** `192.168.1.255`
* **Kullanılabilir İlk Adres:** `192.168.1.1`
* **Kullanılabilir Son Adres:** `192.168.1.254`

Bu örnekte, `192.168.1` kısmı **Ağ (Network)**, `10` kısmı ise **Cihaz (Host)** kısmıdır.

---

## NAT (Network Address Translation)

* **NAT**, özel (private) IP adreslerini genel (public) IP adreslerine dönüştürerek yerel ağdaki cihazların internete erişmesini sağlar.

---

## NAT ve PAT Farkları

| Ağ Adresi Çevirisi (NAT) | Bağlantı Noktası Adresi Çevirisi (PAT) |
| :--- | :--- |
| **NAT** (Network Address Translation) anlamına gelir. | **PAT** (Port Address Translation) anlamına gelir. |
| **Özel IP adresleri, genel bir IP adresine çevrilir.** | **Özel IP adresleri, bağlantı noktası numaraları aracılığıyla genel IP adresine çevrilir.** |
| Her bir özel IP adresi için en az bir genel IP adresi gerekir. | Tek bir genel IP adresi, birçok özel IP adresi için kullanılabilir. |
| PAT, NAT'ın bir türü ve dinamik bir çeşididir. | Birçok özel cihazın internete erişimini tek bir genel IP adresi üzerinden sağlar. |
| IPv4 adreslerini kullanır. | IPv4 adreslerinin yanı sıra bağlantı noktası numaralarını da kullanır. |
| 3 türü vardır: Statik, Dinamik NAT ve PAT (NAT Overload/IP Masking). | 2 türü vardır: Statik ve Aşırı Yüklenmiş (Overloaded) PAT. |
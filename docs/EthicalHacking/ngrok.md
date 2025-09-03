# Ngrok ile Yerel Sunucuları Dışa Açmak

Ngrok, yerel bir sunucuyu internet üzerinden erişilebilir hale getiren bir araçtır. Bu, özellikle web uygulamalarını test etmek veya başkalarına göstermek için çok kullanışlıdır.

-----

## Ngrok Kullanım Adımları

1.  **Hesap Oluşturma ve Kurulum:** Ngrok'u kullanmak için öncelikle bir hesap açmanız ve sisteminize kurmanız gerekir.
2.  **Kimlik Doğrulama:** Terminal üzerinden hesabınıza ait token bilgisi girilerek kimlik doğrulama yapılır.
    ```bash
    ./ngrok authtoken <token>
    ```
3.  **Tünel Başlatma:** Uygulamanızın çalıştığı protokol ve port numarası belirtilerek bir tünel başlatılır.
      * **Örnek:** Eğer siteniz `http://localhost:8888` adresinde çalışıyorsa, aşağıdaki komutu kullanırsınız:
    <!-- end list -->
    ```bash
    ./ngrok http 8888
    ```
4.  **Erişim:** Komutu çalıştırdıktan sonra terminalde size özel `http` ve `https` adresleri (`örneğin, http://123456789.ngrok.io/`) görünür. Bu adresleri başkalarıyla paylaşarak uygulamanıza her yerden erişim sağlayabilirsiniz.

### Faydalı Bilgiler

  * **İstek Günlüğü:** Ngrok tüneli aktifken terminaliniz, gelen istekleri anlık olarak gösterir.
  * **Kontrol Paneli:** `dashboard.ngrok.com/endpoints/status` adresindeki panelden aktif URL'leri ve istemci IP adreslerini görebilirsiniz.
  * **Çıkış:** Ngrok'tan çıkmak için `Ctrl + C` (Mac'te `Cmd + C`) tuş kombinasyonunu kullanabilirsiniz.
  * **Yardım:** Daha fazla yardım almak için terminale `./ngrok help` yazabilirsiniz.

-----

## Ngrok Alternatifleri

Ngrok dışında da benzer amaçlarla kullanabileceğiniz birçok araç bulunur.

  * **LocalXpose**: Ücretsiz seçenekleri olan ticari bir hizmettir. Terminal tabanlı ve grafik arayüzlü istemcileri mevcuttur.
  * **localhost.run**: SSH üzerinden çalışan, istemci kurulumu veya kayıt gerektirmeyen ücretsiz bir servistir.
  * **localtunnel**: Açık kaynaklı bir Node.js istemcisidir. Kayıt gerektirmez.
  * **JPRQ**: Açık kaynaklı bir Python istemcisidir. Kayıt gerektirmez.
  * **sish**: Açık kaynaklı, Docker tabanlı bir istemcidir. Kayıt gerektirmez.

Ngrok ve benzeri tünel hizmetleri, özellikle geliştirme ve test süreçlerinde büyük kolaylık sağlar ve geri bildirim gecikmelerini önemli ölçüde azaltır.
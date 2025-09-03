# Maven komutları

- mvn validate: Projenin target dosyasını siler ve daha sonra hatalı kısımları tarayarak Projenin doğruluğunu kontrol eder.
- mvn compile: Projeyi clean ve validate eder ardından Kaynak kodu derler.
- mvn test: Derlenmiş koda uygun bir unit test ile test eder.
- mvn package: Projeyi testlerini yapar ve eğer hata yoksa projeyi paketler. jar dosyasını oluşturur.
- mvn verify: Entegrasyon teslerinin sonuçlarını kontrol ederek kalite kriterine ulaşıldığından emin olur.
- mvn install: Diğer projelerde dependency olarak kullanmak için paketleri local depoya yükler.
- mvn deploy: Projeyi uygulama sunucusuna yükler.
- mvn clean : Projenin derlenmesi sırasında oluşan target klasörünün(build işlemi sonucunda üretilen) silinmesini sağlar.
- mvn pre-clean: Temizlik öncesi gerekli olan prosesleri çalıştırır
- mvn post-clean: Temizlik işlemini bitirmek için gerekli olan prosesleri çalıştırır
- mvn pre-site: Site oluşturma öncesi gerekli olan prosesleri çalıştırır
- mvn site: Projenin site dökümantasyonunu oluşturur
- mvn post-site: Site oluşturma işlemini bitirmek için gerekli olan prosesleri çalıştırır
- mvn site-deploy: Üretilen siteyi belirtilen web sunucusuna yerleştirir
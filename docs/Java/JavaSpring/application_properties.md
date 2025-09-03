# 6. application.properties Dosyası Nedir?

- Java Spring Boot uygulamasının veritabanı ayarlarını tespit edebilmesi için içinde veri tabanı ayarlarını barındıran dosyadır.
- ```@PropertySource(value = "classpath:app.properties)``` anotasyonu ile application.properties dosyasının adının app.properties olarak çalıştırılabilmesini sağlar. Yani dosyanın adı app.properties ise uygulama ayağa kalkabilir. Bu anotasyon ana sınıfa yazılır.
- ```@Value``` anotasyonu, properties içindeki değerlere ihtiyacımız olduğunda kullanılır.
 ```@Value("${spring.datasource.url}")``` anotasyonu da url değerini, anotasyon yazılan değişkene çeker.
- @ConfigurationProperties anotasyonu, veritabanındaki array değişkenleri tutabilir.

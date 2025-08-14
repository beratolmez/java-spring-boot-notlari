# 8. @Scheduled Anotasyonu

- Görevleri zamanlamayı sağlayan bir anotasyondur.
- Ana sınıfta (@SpringBootApplication ile işaretlenmiş) @EnableScheduling anotasyonu ile aktif edilir.
- Zamanlama görevleri için "scheduled" adında bir paket açılır.
- Bir sınıfa @Component anotasyonu verilmesi gerekir.

```Java
public class ScheduledExample {
    // Saat 15:20'de aşağıdaki fonksiyonu çalıştırmak için ayarlamıştır.
    @Scheduled(cron = "0 15 20 * * *")
    public void write1To10() {
    }
}
```


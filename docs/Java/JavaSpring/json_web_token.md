# 10. JWT (JSON Web Token) Nedir?

- JWT, kimliklendirme/yetkilendirme sağlar. Kullanıcının doğrulanması, web servis güvenliği, bilgi güvenliği gibi bir çok konuda kullanılır.
- JWT kullanıldığında bir "FILTER" katmanı eklenir. Bu durumda bir isteğin yönlendirmesi şu şekilde olacaktır:  
**Filter ↔ Controller ↔ Service ↔ Repository ↔ Database**
- Yapılan isteğe göre eğer isteği yapan kişi sahip olduğu token ile yetkili ise isteği filter katmanından geçerek işlenmeye devam eder.

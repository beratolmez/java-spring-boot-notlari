# 9. JUnit Nedir?

- JUnit en çok tercih edilen Java test yazılım iskeletidir (framework).
- src/test/java içerisindeki paketin içerisine test sınıfları yazılabilir. Metotlar ```@Test``` anotasyonu ile işaretlenmelidir.
- Açılan sınıflar ```@SpringBootTest``` anotasyonu ile işaretlenmesi lazım.
- Bazen projenin ana sınıfını bulamayabilir. Bu durumlarda ```@SpringBootTest(classes = {ExceptionManagementStarter.class})``` olarak düzenlenerek bu sorunun üstesinden gelinebilir.
- Test metotlarının yazılımı için standart **"test"+"işlem adı"** şeklinde olmalıdır. Örnek olarak **"testFindEmployeeById"** verilebilir.
- Test sınıfı ile direk servise bağlanılır.
- Assert metotları ile kontroller sağlanabilir.
- AfterEach ve BeforeEach kavramları.
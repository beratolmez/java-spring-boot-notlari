# 4. Spring Validation

- Kontrolleri sağlamak için kullanılır.  
- Spring Validation için belirli anotasyonlar vardır. Kütüphane içerisindeki anotasyonlar ile kontroller sağlanabilir.  
- Dto için değişkene anotasyon atanır.  
- Servis tarafında parametrenin önüne @Valid anotasyonu yazılmalıdır.


## 4.1. DTO Nedir ve DTO ile Validation

Data Transfer Object (DTO), veri transferi için kullanılan bir tasarım desenidir. DTO'lar, nesnelerin verilerini bir yerden başka bir yere aktarmak için kullanılır. Genellikle bir veritabanından veri çekilirken veya bir web hizmetine veri gönderilirken DTO'lar kullanılır.

**DTO kullanılmasının başlıca nedenleri:**  
1. Kritik verileri korumak.  
2. Veritabanındaki verileri yönetebilmek.  

```Java
public class DtoStudentIU {
    @NotEmpty(message = "Firstname alanı boş bırakılamaz!")
    @Size(min = 3, max = 10, message = "En az 3, en fazla 10 karakter olmalıdır.")
    private String firstName;
    
    @Size(min = 3, max = 30, message = "En az 3, en fazla 30 karakter olmalıdır.")
    private String lastName;
    
    private Date birthOfDate;
}
```


## 4.2. Global Exception Handling

- Spring Validation'dan fırlatılan hataları alıp yönetmek ve anlamlı cevaplar (response) dönmek yazılımın yönetimi ve müşteriye sunulması için önemlidir.
- Bu hataları yakalamak için yazılım geliştirme standartlarına uygun olması açısından "exception" adında bir paket açılır. Bu paketin içerisine "GlobalExceptionHandler" adında da bir sınıf oluşturulur ve **@ControllerAdvice** anotasyonu ile işaretlenir.

```Java
@ExceptionsHandler(value = MethodArgumentNotValidException.class)
public void handleMethodArgumentsNotValidExceptions(MethodArgumentNotValidException ex) {
    Map<String, List<String>> errorsMap = new HashMap<>();
    for (ObjectError objError : ex.getBindingResult().getAllErrors()) {
            // ((FieldError)objError).getField(); ifadesi yaklananan hatanın tipini yakalar.
            Sring fieldName = ((FieldError)objError).getField();
            if(errorsMap.containsKey(fieldName)) {
            
            }
            else {    }
    }
}
```


# 7. Exception Yönetimi

- Hata yakalama, bir bilgisayar programının çalıştığı sırada hata ya da istisnai bir durumla karşılaşması durumunda meydana gelen özel durumda yapılması gereken işlemlerin genel adıdır.


## 7.1. BaseException (Hata Oluşturma)

```Java 
public class BaseException extends RuntimeException {
    public BaseException () {
    }
}
public class ErrorMessage {
    NO_RECORD_EXIST("1001", "Kayıt bulunamadı!"),
    GENERAL_EXCEPTION("9999", "Genel bir hata oluştu.");
    private String code;
    private String message;
    MessageType(String code, String message) {
         this.code = code;
         this.message = message;
    }
}
```


## 7.2. GlobalExceptionHandler (Hata Yakalama)

```Java
@ControllerAdvice
public class GlobalExceptionHandler {
    @ExceptionHandler(value = {BaseException.class})
    public void handleBaseException(BaseException exception){
        return ResponseEntity.badRequest().body(exception.getMessage());
    }
}
```


### 7.3. Controller'dan Aynı Formatta Cevap Dönmek

- Hatanın generic tipte olması önemlidir.
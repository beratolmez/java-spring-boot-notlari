# 1.Temel Anotasyonlar


## 1.1 @PathVariable

URL'nin parçası olan değerleri almak için kullanılır.

```Java
@GetMapping("/users/{id}")
public ResponseEntity<User> getUserById(@PathVariable Long id) {
    return ResponseEntity.ok(userService.getById(id));
}
```

- **GET: /users/42** → "42" değeri @PathVariable Long id ile yakalanır.

## 1.2. @RequestParam

URL'nin sonunda **?** ile başlayan ve **&** ile ayrılan query string parametrelerini almak için kullanılır.  

```Java
@GetMapping("/search")
public ResponseEntity<List<User>> searchUsers(@RequestParam String name) {
    return ResponseEntity.ok(userService.searchByName(name));
}
```

- **GET: /search?name=enes** → name=enes → @RequestParam String name ile alınır.

## 1.3. @RequestBody

Client tarafından POST veya PUT isteklerinde gönderilen JSON verilerini nesneye dönüştürür.

```Java
@PostMapping("/users")
public ResponseEntity<String> createUser(@RequestBody User user) {
    userService.createUser(user);
    return ResponseEntity.ok("Kullanıcı oluşturuldu");
}
```

Gönderilen JSON:  
```JSON
{
  "name": "Enes",
  "email": "enes@example.com"
}
```

## 1.4. @RequestMapping (Sınıf Düzeyinde)

HTTP isteklerini denetleyici sınıfınızdaki yöntemlere eşleyen Spring Framework'te çok yönlü bir açıklamadır.

```Java
// Tüm metodlara bu kök path eklenir
@RequestMapping("/rest/api")
```

!!! info "MVC İstek Haritası"  
    **Controller (@RestController) ↔ Service (@Service) ↔ Repository (@Repository) ↔ Database**


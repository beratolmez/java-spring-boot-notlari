# 2. HTTP Metotları


## 2.1. GET ISTEGI

Bir GET isteği, sunucudan belirli bir bilgi veya kaynak ister. Bir web sitesine bağlandığınızda, tarayıcınız genellikle sayfanın yüklenmesi için ihtiyaç duyduğu verileri almak üzere birkaç GET isteği gönderir.

```Java
@GetMapping(path = "/employee-list/{id}")
public Employee getEmployeeById(@PathVariable(name = "id", required = true) String id)
```


## 2.2. POST ISTEGI

Herhangi bir amaçla bilgi göndermek istediğinizde, bilgiyi hedefe göndermek için POST isteğini kullanırsınız.

```Java
@PostMapping(path = "/save-employee")
public Employee saveEmployee(@RequestBody Employee newEmployee) {
    return employeeService.saveEmployee(newEmployee);
}
```


## 2.3. DELETE ISTEGI

DELETE yöntemi, bir veritabanından veri kaldırmak için kullanılır. Bir istemci bir DELETE isteği gönderdiğinde, belirtilen URL'deki kaynağın kaldırılmasını talep eder.

```Java
@DeleteMapping(path = "/delete-employee/{id}")
public boolean deleteEmployee(@PathVariable(name = "id") String id) {
   return employeeService.deleteEmployee(id);
}
```


## 2.4. PUT ISTEGI

PUT istekleri sunucudaki mevcut bir kaynağı güncellemek veya değiştirmek için kullanılır.

```Java
@PutMapping(path = "/update-employee/{id}")
public Employee updateEmployee(@PathVariable String id, 
                                @RequestBody UpdateEmployeeRequest request) {
    return employeeService.updateEmployee(id, request);
}
```


# 5. Relations Nedir?

Entityler arasındaki ilişkiyi sağlar.  

- @OneToOne = Customer ↔ Adress
- @OnetToMany = Department ↔ Employee
- @ManyToOne = Employee ↔ Department
- @ManyToMany = Student ↔ Course


## 5.1. @OneToOne

- Eklenen objeyi o objeye birebir olarak bağlar.
- Ek bir kolon açarak ilişkilendirir.

```Java
public class Customer {
    @OneToOne
    private Adress adress;
}
```


## 5.2. @OneToMany

- Bir evin birden fazla odaya sahip olması durumu. Birden çoka ilişkisi.
- Yeni bir tablo açar.

```Java
public class Home {
    @OneToMany
    private Room room;
}
```


## 5.3. @ManyToOne

- Birden çok çalışanın, bir departmana bağlı olması durumu. Çoktan bire ilişkisi.
- Ek bir kolon açarak ilişkilendirir.

```Java
public class Employee {
    @ManyToOne
    private Department department;
}
```


## 5.4. @ManyToMany

- Birden çok öğrencinin, birden çok ders alabilmesi durumu. Çoktan çoka ilişkisi.
- Yeni bir tablo açar.

```Java
public class Student {
    @ManyToMany
    @JoinTable(name = "student_course",
    joinColumns = @JoinColumn(name="student_id)
    inverseJoinColums = @JoinColumn(name = "course_id))
    private list<Course> course;
}
```


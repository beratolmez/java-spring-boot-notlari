# 3. Spring Data JPA


## 3.1. Genel Bilgi

- Veritabanı ayarları ```application.properties``` dosyasında tutulur.
- ```spring.jpa.hibernate.ddl-auto=create``` sadece ilk tablo oluşturma aşamasında kullanılmalı. Daha sonra ```update``` veya ```none``` yapılmalıdır.  


## 3.2. Repository Yapısı

```Java
public interface StudentRepository extends JpaRepository<Student, Integer> {
}
```

- İlk parametre Entity tipi (Student)
- İkinci parametre ID tipi (Integer)


## 3.3. @Query Anotasyonu

HQL (Hibernate Query Language) veya native SQL yazmak için kullanılır.

```Java
// Student tablosundan tüm öğrencileri alır.
@Query(value = "from Student", nativeQuery = false)
List<Student> findAllStudents();

// Student tablosundan id değeri, parametre olarak alınan studentId ile eşleşen öğrenciyi alır.
@Query(value = "from Student s WHERE s.id = :studentId")
Optional<Student> findStudentById(Integer studentId);
```


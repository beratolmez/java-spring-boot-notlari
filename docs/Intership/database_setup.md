# Spring-Boot Projesi İçin Veri Tabanı Kurulumu

**Oracle 23ai** kurulduktan sonra yapılması aşağıda yapılması gerekenlerin listesi yer almaktadır. Bu komutlar `sqlplus` komutunun çalışabileceği herhangi bir komut satırı ile çalıştırılabilir.


## Veri Tabanı Kullanıcı Oluşturma ve Yetkilendirme  
'C:EXPORT' olarak klasör oluşturduktan ve .dmp uzantılı veritabanı dosyası klasörün içine kopyalandıktan sonra aşağıdaki komutların sırası ile çalıştırılmasıyla veri tabanında kullanıcı oluşturulur ve gerekli yetkiler verilir, EXPORT klasörü tanıtılır ve veriler içeri aktarılır:

```sh
sqlplus / as sysdba;
```
```sh
CREATE USER C##<Username> IDENTIFIED BY <Password>
```
```sh
GRANT CONNECT, RESOURCE TO C##<Username>
```
```sh
GRANT DBA TO C##<Username>
```
```sh
CREATE OR REPLACE DIRECTORY EXPORT_DIR AS 'C:\EXPORT';
```
```sh
impdp C##<Username>/<Password>@localhost:1521/FREE schemas=C##MUSA remap_schema=C##MUSA:C##<Username> directory=EXPORT_DIR dumpfile=EXPORT_FILE.dmp logfile=my_import.log content=ALL
```

## Veri Tabanı İçeri ve Dışa Aktarma (Import / Export)  
Proje Oracle veritabanı kullandığı için, veritabanı yedeği almak veya başka bir ortama aktarmak için Oracle'ın `exp` ve `imp` (veya daha güncel olarak `expdp` ve `impdp`) araçları kullanılabilir. Bu işlemler sonucunda `.dmp` uzantılı dump dosyaları elde edilir.

1. ### Export (Yedek Alma)  
Aşağıdaki komut ile ilgili kullanıcıya ait tüm veritabanı nesneleri bir DMP dosyasına aktarılır:
```sh
expdp <Username>/<Password>@localhost:1521/FREE schemas=<Username> directory=EXPORT_DIR dumpfile=backup.dmp logfile=backup.log
```

2. ### Import (Yedekten Geri Yükleme)
Alınan dump dosyasını başka bir veritabanına yüklemek için:
```sh
impdp C##<Username>/<Password>@localhost:1521/FREE schemas=C##<Username> directory=EXPORT_DIR dumpfile=backup.dmp logfile=import.log
```

# Oracle Database SQLPlus Giriş Yapma

Aşağıdaki işlemleri mac cihazınızda terminal üzerinde çalıştırabilirsiniz.

1. Docker üzerinde bulunan mevcut imajlarını görüntüler.
 
    ```sh
    docker image ls
    ```

2. Docker için oracle veritabanı konteynırını ayağa kaldırır.

    ```sh
    docker run <konteynır id veya konteynır ismi>
    ```

3. Docker üzerinde çalışan konteynırları görüntüler.

    ```sh
    docker image ps
    ```

4. Hedeflenen konteynırın terminaline giriş yapar.

    ```sh
    docker exec -it <konteynır id veya ismi> bash
    ```

5. Oracle konteynır içinde SQLPlus komutunu çalıştırarak veritabanında yönetici ayrıcalıkları ile işlem yapılabilir.

    ```sh
    sqlplus / as sysdba
    ```

6. Belirtilen kullanıcı adı ve şifre ile veritabanı yönetimi için bir hesap oluşturur. (Blokları yazmayınız.)

    ```sh
    CREATE USER <Username> IDENTIFIED BY <Password>;
    ```

7. Aşağıdaki komutlar ile yetki verin.

    ```sh
    GRANT CONNECT, RESOURCE TO <Username>;
    ```

8. ...

    ```sh
    GRANT DBA TO <Username>;
    ```

9.  Belirtilen dizinde dizin yolu oluşturun.

    ```sh
    CREATE OR REPLACE DIRECTORY EXPORT_DIR AS 'C:\EXPORT;
    ```

10. SQLPlus içerisinden çıkın.
    
    ```sh
    exit
    ```

11. Şemayı aktarın.

    ```
    impdp <Username>/<Password>@localhost:1521/FREE schemas=C##MUSA remap_schema=C##MUSA:<Username> directory=EXPORT_DIR dumpfile=EXPORT_FILE.dmp logfile=my_import.log content=ALL
    ```


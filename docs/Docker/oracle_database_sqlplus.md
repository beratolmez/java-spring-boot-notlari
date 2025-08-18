# Oracle Database SQLPlus Giriş Yapma

Aşağıdaki işlemleri mac cihazınızda terminal üzerinde çalıştırabilirsiniz.

1. Docker üzerinde bulunan mevcut imajlarını görüntüler.
 
    ```zsh
    docker image ls
    ```

2. Docker için oracle veritabanı konteynırını ayağa kaldırır.

    ```zsh
    docker run <konteynır id veya konteynır ismi>
    ```

3. Docker üzerinde çalışan konteynırları görüntüler.

    ```zsh
    docker image ps
    ```

4. Hedeflenen konteynırın terminaline giriş yapar.

    ```zsh
    docker exec -it <konteynır id veya ismi> bash
    ```

5. Oracle konteynır içinde SQLPlus komutunu çalıştırarak veritabanında yönetici ayrıcalıkları ile işlem yapılabilir.

    ```zsh
    sqlplus / as sysdba
    ```

6. Belirtilen kullanıcı adı ve şifre ile veritabanı yönetimi için bir hesap oluşturur. (Blokları yazmayınız.)

    ```zsh
    CREATE USER <Username> IDENTIFIED BY <Password>;
    ```

7. 
    ```zsh
    GRANT CONNECT, RESOURCE TO <Username>;
    ```

8. 
    ```zsh
    GRANT DBA TO <Username>;
    ```

9. 
    ```zsh
    CREATE OR REPLACE DIRECTORY EXPORT_DIR AS 'C:\EXPORT;
    ```

10. SQLPlus içerisinden çıkın.
    
    ```zsh
    exit
    ```

11. 
    ```
    impdp <Username>/<Password>@localhost:1521/FREE schemas=C##MUSA remap_schema=C##MUSA:<Username> directory=EXPORT_DIR dumpfile=EXPORT_FILE.dmp logfile=my_import.log content=ALL
    ```


Komande za kreiranje korisnika (user-a) i dodavanje svih privilegija

u mysql terminalu uneti sledece
```mysql
CREATE USER `john`@`localhost` IDENTIFIED BY `password`;
```

dodavanje privilegija
```mysql
GRANT ALL PRIVILEGES ON *.* TO 'john'@'localhost' WITH GRANT OPTION;
```
ukoliko je potreban samo jedan baza umesto zvezdica dodati ime baze i tabelu ili sve tabele  `*`

Primetiti sve izmene u bazi (apply)
```mysql 
FLUSH PRIVILEGES;
```
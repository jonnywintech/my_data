prikaz svih databaza
```sql
SHOW DATABASES;
```

pravljenje databaze komandom 

```sql
CREATE DATABASE [ime_databaze];
```

brisanje database komandom

```sql
DROP DATABASE [ime_database];
```

koriscenje USE  databaze
```sql
USE DATABASE [ime_databaze];
```


# Import sql fajla tj databaze u SQL
to se radi sledecom komandom
1. Najpre se Kreira dabaza u sql-u;
```sql
CREATE DATABASE world;
```
2. onda se van sql-a kuca sledeca komanda
```bash
mysql -u root -p ime_baze_koja_se_kreira <  ime_fajla_koji_se_importuje.sql
```

`primer`
```bash
mysql -u root -p world < world_2017-10-16.sql
```



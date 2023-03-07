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


### Nacin 2
1. Ulogovati se u mysql
```bash
mysql -u root
```

2. Napraviti novu bazu u mysql-u
```mysql
CREATE DATABASE test;
```

3. Selektirati bazu
``` mysql
USE test;
```

4. Napisati `source` i ime fajla 
```mysql
source backup-file.sql;
```
(u zavisnosti gde je otvoren terminal zavisi putanja do fajla koji se importuje)

## Export Databaze

```bash
mysqldump -u YourUser -p YourDatabaseName > wantedsqlfile.sql
```

## GZ Import / Export

Export
```bash
mysqldump -u [user] -p [db_name] | gzip > [filename_to_compress.sql.gz] 
```

Import
```bash
gunzip < [compressed_filename.sql.gz]  | mysql -u [user] -p[password] [databasename]
```

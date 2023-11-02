Svaka databaza ima tabele u kojoj su smesteni podaci
svaka od tabela ima ime i vrstu podataka u koju se smestaju


primer
![[Pasted image 20220902173553.png]]

sastoji se od kolona i redova

kolona ima naslov a red sadrzi podatke o koloni

![[Pasted image 20220902173709.png]]



# Kreiranje tabele

kreiranje tabele se vrsi komandom
```sql
CREATE TABLE table_name ( column1 datatype, column2 datatype, .... );
```

Tipovi Datoteka 

| Tip Podataka | Opis|
|---|---|
|CHARACTER(n)| Character string. Fixed-length n|
|VARCHAR(n)|Character string. Variable length. Maximum length n|
|BOOLEAN|Stores TRUE or FALSE values|
|INTEGER|Integer numerical (no decimal)|
|DECIMAL(l,s)|Exact numerical, length (l), scale (s); e.g. (5,2)|
|DATE|Stores year, month, and day values|
|TIME|TIME|
|TIMESTAMP|Stores year, month, day, hour, minute, and second values|

## Pirkaz svih tablea u  [[Databaze|databazi]]
```sql
use database [ime_databaze];
show tables;
```

## Primer Kreiranja Tabele

```sql
CREATE TABLE posts (
	id int,
	title varchar(100),
	content text,
	created_at datetime,
	updated_at datetime
);
```

## Prikaz iliti ispis sta se nalazi u Tabeli

```sql
DESCRIBE [table_name];
```

![[Pasted image 20220902174642.png]]

## Brisanje Tabele
```sql
DROP TABLE [table_name];
```

## Brisanje Podataka iz Tabele
```sql
TRUNCADE TABLE [ime_tabele];
```

## Izmena Tabele
```sql
ALTER TABLE [table_name] ADD [column_name] [datatype];
// dodavanje polja u tabelu;

ALTER TABLE [table_name] DROP COLUMN [column_name];
//brisanje polja iz tabele;

ALTER TABLE [table_name] MODIFY COLUMN [column_name] [datatype];
//menjanje tipa podataka unutar polja u tabeli;
```

primeri
```sql

ALTER TABLE posts ADD teaser varchar(300);

ALTER TABLE posts MODIFY COLUMN teaser varchar(200);

ALTER TABLE posts DROP COLUMN teaser;

* test after each statement with: DESCRIBE table_name

```


[[4. Sql|Nazad]] 
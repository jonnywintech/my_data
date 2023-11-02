## Select Statement

primer 1
```sql
SELECT column1, column2, … FROM table_name;
```

primer 2

```sql
SELECT id, title FROM posts;

SELECT id, title, content, category, created_at FROM posts;

SELECT * FROM posts;
```

## Select Distinct 
Vraca razlicite stvari izmedju tabela

```sql
SELECT DISTINCT column1, column2, … FROM table_name;
```

primer 2

```sql
SELECT DISTINCT category FROM posts;

SELECT DISTINCT category, rating FROM posts;
```

## Select WHERE filter

rec `where` oznacava prvi uslov koji tabela mora da ispuni
```sql
SELECT column1, column2, … FROM table_name WHERE condition;
```
Mapa USLOVA

|OPerator|Description|
|---|---|
|=| Jednako|
|<>|Nejednako - Not equal|
|>|Vece od|
|<|Manje od|
|>=| Vece od ili jednako|
|<=|Manje od ili jednako|
|BETWEEN| Between an inclusive range|
|LIKE| Trazi Pattern|
|IN|vezvivanje vise  polja; u zagradama se pisu vise polja iz tabele ('apple','food')|
|AND| koristi se da chainuje vise vrednosti a kao povratnu informaciju imaju `TRUE`|
|OR| ili operator koji se koristi  izmedju prvog ili drugog uslova a da jedan od njih ima `TRUE`|
|NOT| Negiranje stavki tj(uslova) koji se postavlja|


### Primeri za WHERE
```sql
SELECT category, rating, title FROM posts WHERE category = ‘fashion’;
SELECT category, rating, title FROM posts WHERE category <> ‘sports’;
SELECT category, rating, title, created_at FROM posts WHERE rating > 8;
SELECT category, rating, title, created_at FROM posts WHERE rating < 5;
SELECT * FROM posts WHERE rating >= 5;
SELECT * FROM posts WHERE rating <= 3;
```


### Primeri za BETWEEN operator

```sql
SELECT column_name(s) FROM table_name WHERE column_name BETWEEN value1 AND value2;
```

### Primeri za IN Operator

```sql
SELECT column_name(s) FROM table_name WHERE column_name IN (value1, value2, ...);
SELECT column_name(s) FROM table_name WHERE column_name IN (SELECT STATEMENT);
```

### Primeri za LIKE Operator
```sql
SELECT column1, column2, … FROM table_name WHERE column LIKE pattern;
```
Koristi whildcard `%` on predstavla jedan ili vise karaktera u zavisnosti od pozicije
wildcard  `_`  predstavlja jedan karakter

### Tabela za WHILDCARD
|wildcard|Opis|
|---|---|
|'eur%'| nalazi vrednosti `koji pocinju sa` 'eur'|
|'%la'|nalazi vrednosti `koji se zavrsavaju sa` 'la'|
|'%or%'| nalazi vrednosti koje imaju 'or' u `bilo kojoj pozicii`|
| `'_r%'` |  nalazi vrednosti koje imaju 'r' `kao drugu poziciju`|
|`'a_%_%'`| nalazi vrednosti koje pocinju slovom 'a'  i imaju `najmanje 3 karaktera`|
|'a%r'|nalazi vrednosti koje `pocinju` slovom 'a' a `zavrsavaju` se sa 'r'|


### primeri za BETWEEN, IN i LIKE operatore

```sql
SELECT title, category, rating, teaser FROM posts WHERE rating BETWEEN 3 AND 7;

SELECT title, created_at FROM posts WHERE created_at BETWEEN ‘2015-01-01’ AND ‘2016-01-01’;

SELECT title, category, teaser FROM posts WHERE category LIKE ‘%s’;

SELECT title, category, teaser FROM posts WHERE title LIKE ‘Object%’;

SELECT title, category, teaser FROM posts WHERE category LIKE ‘f _ _ d’;

SELECT * FROM posts WHERE category IN (‘sports’, ‘health’);

SELECT * FROM posts WHERE category IN (SELECT category FROM posts WHERE rating = 3);
```


### Primeri za AND, OR  i NOT Operatore

```sql
SELECT title, category, rating FROM posts WHERE category = ‘fashion’ AND rating < 5;

SELECT title, category, rating FROM posts WHERE rating BETWEEN 6 AND 10 AND category  IN (‘food’, ‘health’, ‘fashion’);

SELECT title, category, rating FROM posts WHERE category IN (‘sports’, ‘politics’) OR title LIKE ‘%implementation’ OR rating <= 3;

SELECT * FROM posts WHERE NOT rating = 5;

SELECT * FROM posts WHERE rating NOT IN (1, 3, 5, 7, 9);
```

## Sortiranje podataka
sortiranje se vrsi po ASC i DESC
ASC primer sortiranja  =  12345;
DESC primer sortiranja = 54321;


## Primeri sortiranja podataka

```sql
SELECT title, category, rating FROM posts ORDER BY rating;

SELECT * FROM posts ORDER BY category DESC;

SELECT rating, category, title FROM posts ORDER BY rating ASC, category DESC;

SELECT id, category, rating, title FROM posts WHERE rating > 7 ORDER BY title DESC;
```

# Limit  
### Ogranicava broj podataka  u izlistanoj tabeli 
```sql
SELECT column1, column2, … FROM table_name LIMIT number;
```
primeri za limit
```sql
SELECT title, category, rating FROM posts LIMIT 20;

SELECT * FROM posts WHERE rating > 8 LIMIT 10;

SELECT category, rating, title FROM posts WHERE rating > 8 ORDER BY rating DESC LIMIT 20;
```

#### ovo ogranicava broj podataka koji ce biti vracen iz baze

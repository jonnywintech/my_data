1. Posle instalacije Composera i Laravela /// za creiranje novog projekta

```bash
laravel new [ime_projekta]
```

2. Napraviti databazu za projekat u mysql-u

```sql
CREATE DATABASE   [database_name]       ;
```

3. Proveriti .env fajl koji sadrzi podatke o databazi na koju se konektuje
   
   .env fajl se nalazi u  folderu koji ste kreirali

## [[ pravljenje table u databazi]]

## U slucaju da pullujete neciji projekat > git clone

```bash
git clone https://github.com/drstvnvc/nk16-blog.git
cd nk16-blog

composer install
cp .env.example .env
php artisan key:generate
```

popuniti .env fajl sa podacima iz databaze i onda

```bash
php artisan migrate
php artisan serve
```

u .env fajlu u slucaju da se radi u produkciji promeniti APP_ENV= production

u ovom slucaju daje upozorenje u slucaju da slucajno ukucate komande koje

mogu da izbrisu databaze ili tabele i time obrisete podatke
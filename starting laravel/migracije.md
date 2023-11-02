#### Osnovna komanda za pravljenje tabele u databazi kada se popune svi podac
```bash
php artisan migrate
```

#### provera statusa migracija 
```bash
php artisan migrate:status
```


### brisanje stare tabele iz databaze i primena nove
```bash
php artisan migrate:fresh
```


### migracija  sa seedovanjem factory methoda - popunjavanje podataka u databazi (faker)
```bash
php artisan migrate:fresh --seed
```



[[1. Laravel List|Nazad]]

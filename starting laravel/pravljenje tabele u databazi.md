 4.Napraviti novi fajl koji se koristi kao template za  mysql table

### konvekcija za pisanje imena tabela je sledeca
### create_ime tabele_table

   
   ```bash
   php artisan make:migration [ime_tabele] ## create_user_table
   ## primer
   php artisan make:migration create_books_table
   ```

## dokumentacija sa opisom tabele kada se pravi
## https://laravel.com/docs/4.2/schema#adding-columns

laravel 9.x verzija
https://laravel.com/docs/9.x/migrations#available-column-types


5  Popuniti fajl na lokaciji database/migration/[ime_fajla_bice_datum+ime__tabele]
```php
    public function up()
        {
            Schema::create('books', function (Blueprint $table) {
                $table->id();
                $table->string('title');
                $table->string('author');
                // foreign key
                $table->foreignId('user_id')
                ->constrained()
                ->onDelete('cascade');
                $table->timestamps();
            });
        }
    
    // function down sluzi za dropovanje databaze
     public function down()
        {
            Schema::dropIfExists('books');
        }
```


```php
    ->constrained() // je isto sto i 
    ->references('id')->on('author') // moze se koristiti i kao
    ->constrained('ime_tabele')
```

### quick copy foreign key
```php
$table->foreignId('user_id')
->constrained()
->onDelete('cascade');
```

#### sledeći korak je [[migracije]]


[[1. Laravel List|Back]]

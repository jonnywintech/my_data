### quick copy foreign key
```php
$table->foreignId('user_id')
->constrained()
->onDelete('cascade');
```


stara verzija 
```php
    ->constrained() // je isto sto i 
    ->references('id')->on('author') // moze se koristiti i kao
    ->constrained('ime_tabele')
```


[[1. Laravel List|Nazad]]

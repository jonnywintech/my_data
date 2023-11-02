Setup bilo kog Testa
```php
use RefreshDatabase;
// use RefreshDatabase; obavezno je za laravel kada se koristi mysqlite 
// a ne prava baza
	public function setUp(): void
    {
        $this->queue = new Queue();
    }
    // setUp()
    //inicijalno podesavanje pre izvrsavanje bilo kog testa
```


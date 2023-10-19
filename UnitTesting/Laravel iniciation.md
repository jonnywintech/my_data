```php
    public function setUp(): void
    {
        parent::setUp();

        // Run migrations
        \Artisan::call('migrate:fresh');

        // Run seeders
        \Artisan::call('db:seed');
	  $this->queue = new Queue;
      $this->user = new User();
      $this->user->first_name = 'John';
      $this->user->last_name = 'Wicker';
      $this->user->email = 'john@example.com';
      $this->user->password = password_hash('password', PASSWORD_BCRYPT);
      $this->user->is_verified = true;

      $this->user->save();
    }
```

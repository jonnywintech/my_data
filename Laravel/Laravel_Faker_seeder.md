# Laravel Faker i Seeder

prvo napraviti factory za zeljeni kontroller

```php
php artisan make:factory CarFactory
```

pogledati kako je napisan UserFactory i prema njemu napisati

Dokumentacija za faker [GitHub - fzaninotto/Faker: Faker is a PHP library that generates fake data for you](https://github.com/fzaninotto/Faker#basic-usage)

```php

    public function definition()
    {
        return [
            'name' => $this->faker->name(),
            'email' => $this->faker->unique()->safeEmail(),
            'email_verified_at' => now(),
            'password' => '$2y$10$92IXUNpkjO0rOQ5byMi.Ye4oKoEa3Ro9llC/.og/at2.uheWG/igi', // password
            'remember_token' => Str::random(10),
        ];
    }
```

pokrece se tako sto se dodaje zeljena klasa u DatabaseSeed.php 

importuje se i onda se zove create i broj zeljenih polja

```php
//hardcode primer koji se koristi jednom
Car::create([
    'model' => 'model',
    'hardcoding' =>'data'
])


//factory

Car::factory(6)->create();
```

komada za seedovanje

```bash
php artisan db:seed
## alternativno za migrate fresh

php artisan migrate:fresh --seed
```

[[1. Laravel List|Nazad]]

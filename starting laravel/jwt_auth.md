# JWT Auth Instalacija i konfiguracija

```bash
composer require php-open-source-saver/jwt-auth
```

kada se instalira potrebno je konfigurisati

```bash
php artisan vendor:publish --provider="PHPOpenSourceSaver\JWTAuth\Providers\LaravelServiceProvider"
```

ili samo

```bash
php artisan vendor:publish # i izabrati opciju 8 ili koja vec odgovara
```

generisanje kljuca u .env fajlu

```bash
php artisan jwt:secret
```

generisanje certifikata (ovo nam netreba)

```bash
php artisan jwt:generate-certs
```

dokumentacija o jw pogledati detaljno radi dalje konfiguracije oko korisnika

[Home - Laravel JWT Auth](https://laravel-jwt-auth.readthedocs.io/en/latest/)

Za dužinu trajanja tokena iz jwt.php fajla  ne unosi se direktno vrednost nego se dodaje u .env fajl kako je  i naznačena putanja gde pointuje

Updejt User modela da bi radio

```php
use PHPOpenSourceSaver\JWTAuth\Contracts\JWTSubject;
// dodaje se pri vrhu u User.php
```

```php
class User extends Authenticatable implements JWTSubject
//ovo se menja umesto postojeće clase user
// ispratiti dokumentaciju i dodati sva polja
```

```php
 //primeri sa casa
   public function getJWTIdentifier()
    {
      ///  return $this->getKey();
          return $this->id;
      // kada nam treba id pri logovanju usera
    }

  public function getJWTCustomClaims()
    {
        return [
            'email' => $this->email,
        ];
    }
```

auth gard konfiguracija

```php
// auth.php

// defaultni guard koji je 'web' vrsi autentikaciju preko sesije 
//pomeniti defaultni guard na 'api'

    'defaults' => [
        'guard' => 'api',
        'passwords' => 'users',
    ],



   'guards' => [
        'web' => [
            'driver' => 'session',
            'provider' => 'users',
        ],// sve dole je novo dodato jer vrsimo api verifikaciju
            'api' => [
            'driver' => 'jwt',
            'provider' => 'users'
        ],

    ],


//u slucaju da nam trebaju i web i api guard 
// moze se takodje ostaviti gore navedeni web kao defaultni a u User.php
// pri dnu dodati 
Auth::guard('api')->login($user);
//ili helper funkcija
auth('api')->login($login);
```

```php
//u slucaju kada imamo i laravel aplikaciju a takodje i eksternu aplikaciju
Auth:guard()
Auth::guard('api')->login($user);
//ili helper funkcija
auth('api')->login($login);
```

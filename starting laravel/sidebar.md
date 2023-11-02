## sidebar sa odredjenim brojem postova
1. pravi se provider 
```bash
php artisan make:provider ViewServiceProvider
```

on sadrzi mini controler i view modul zajedno 
primer providera
```php
<?php

namespace App\Providers;

use App\Models\Team;
use Illuminate\Support\Facades\View;
use Illuminate\Support\ServiceProvider;

class ViewServiceProvider extends ServiceProvider
{
    
    public function register()
    {
        //
    }

    public function boot()
    {
        $teamsWithNews = Team::whereHas('news')->get();
        View::share('teamsWithNews', $teamsWithNews);
        // $errors View::share('errors', $errors);
    }
}
```

u `config/app.php` tu se dodaje provider
```php
/*
         * Application Service Providers...
         */
        // App\Providers\BroadcastServiceProvider::class,
    
        App\Providers\ViewServiceProvider::class,
```

pravi se partial i veze se na zeljeni blade fajl na kome se unosi


[[1. Laravel List|Nazad]]

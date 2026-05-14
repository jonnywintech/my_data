na linux serveru pokrenuti crontab -e
u slucaju da je shared hosting naci u ui gde se nalazi cronjob testirati i prilagoditi komandu po potrebi

```cmd
* * * * * cd /home/john/development/suzuki && php artisan schedule:run >> /dev/null 2>&1
  
  
* * * * * cd /home/john/development/suzuki && php artisan queue:work --stop-when-empty >> /dev/null 2>&1
```

napraviti custom komandu

```bash
php artisan make:command ExecuteTask
```

u handle metodi  popuniti sa stvarima koje zelite da se izvrse

`routes/console.php`

ovde onda odraditi schedule i pozvati komandu

```php
<?php

use Illuminate\Foundation\Inspiring;
use Illuminate\Support\Facades\Artisan;
use Illuminate\Support\Facades\Schedule;

// Artisan::command('inspire', function () {
//     $this->comment(Inspiring::quote());
// })->purpose('Display an inspiring quote');


Schedule::call(function(){
    Artisan::call('app:generate-sitemap', [
        '--path' => 'sitemap.xml',
    ]);
})->everyMinute();
```
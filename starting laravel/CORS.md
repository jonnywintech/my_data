dozvola browseru da salje podatke sa vise lokacije
primer facebook.com na twitter.com

```bash
php artisan make:middleware MyCors
```

MyCors.php

```php
public function handle(Request $request, Closure $next): Response
{
	$response = $next($request);
	$response->header('Allow-Controll-Allow-Origin','localhost:3000');
	return $response;
}
```

ili da svi budu srecni :D

```php
public function handle(Request $request, Closure $next): Response
{
	$response = $next($request);
	$response->header('Allow-Controll-Allow-Origin','*');
	return $response;
}
```

ako neradi onda dodati jos :)
```php
    public function handle(Request $request, Closure $next): Response
    {
        return $next($request)
        ->header('Access-Control-Allow-Origin', '*')
        ->header('Access-Control-Allow-Methods', 'PUT', 'POST', 
        'DELETE', 'GET', 'OPTIONS')
        ->header('Access-Control-Allow-Headers', 'Accept,Authorization,Content-Type');
    }
```


dodati middleware u kernel.php

```php
protected $routeMiddleware = [
        'auth'          => \Illuminate\Auth\Middleware\Authenticate::class,
        'auth.basic'    => \Illuminate\Auth\Middleware\AuthenticateWithBasicAuth::class,
        'bindings'      => \Illuminate\Routing\Middleware\SubstituteBindings::class,
        'cache.headers' => \Illuminate\Http\Middleware\SetCacheHeaders::class,
        'can'           => \Illuminate\Auth\Middleware\Authorize::class,
        'guest'         => \App\Http\Middleware\RedirectIfAuthenticated::class,
        'signed'        => \Illuminate\Routing\Middleware\ValidateSignature::class,
        'throttle'      => \Illuminate\Routing\Middleware\ThrottleRequests::class,
        'cors'          => \App\Http\Middleware\MyCors::class, // ovo je dodato
    ];
```
 ima dva nacina  
 `1` je dodati globalno u $middleware 
 -ovde nije potrebno dodavati po rutama jer je dodeljen globalno

 `2` je dodati gde je samo potrebno kao middleware
 -ovde je potrebno dodati samo na odredjene rute koje imaju cors greske
 ```php
#1 
protected $middleware = [];

#2
protected $routeMiddleware = [];
```
i onda se dodaje kao middleware u ruti

```php
Route::middleware(['cors'])->group(function () {
    Route::post('/hogehoge', 'Controller@hogehoge');
});
```

[[1. Laravel List|Nazad]]

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
        'cors'          => \App\Http\Middleware\Cors::class, // ovo je dodato
    ];
```

i onda se dodaje kao middleware u ruti

```php
Route::middleware(['cors'])->group(function () {
    Route::post('/hogehoge', 'Controller@hogehoge');
});
```

[[1. Laravel List|Nazad]]

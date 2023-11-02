### Laravel middleware postavlja se u view 
primer
```php
Route::get('/team/{id}', [TeamController::class, 'show'])->middleware('auth');
```

pristup ruti je dozvoljen samo ako je korisnik ulogovan

## Grupacija Middlewera
```php

Route::group([
    'middleware' => 'auth'
], function () {
    Route::get('/', [TeamController::class, 'index']);
    Route::get('/teams/{team}', [TeamController::class, 'show']);
    Route::get('/players/{player}', [PlayerController::class, 'show']);
    Route::post('/logout', [AuthController::class, 'logout']);
});

Route::group([
    'middleware' => 'guest'
], function () {
    Route::get('/register', [AuthController::class, 'getRegisterForm']);
    Route::post('/register', [AuthController::class, 'register']);
    Route::get('/login', [AuthController::class, 'getLoginForm'])->name('login');
    Route::post('/login', [AuthController::class, 'login']);
});
```
ime rute je bitno kada se postavlja middleware 
`->name('login')`

### `Postavljanje home rute  na putanji `
```copy
app/Providers/RouteServiceProvider.php
```

```php
  * @var string
     */
    public const HOME = '/';

    /**
```

Laravel primer

### u blejd templejtu se moze prikazati na primer register samo ako je korisnik guest
```php
@guest

<a href="/register"> Register </a>

@endguest
```
a ako je korisnik ulogovan 
```php
@auth
<a href="/register">Welcome {{ auth->user()->name }}</a>
@endauth
```
logout
```php
<form method='POST' action='/logout'>
@crsf
<button type='submit'> Logout </button>
</form>
```
### [Global Mihttps://laravel.com/docs/8.x/middleware#global-middlewareddleware](https://laravel.com/docs/8.x/middleware#global-middleware)

If you want a middleware to run during every HTTP request to your application, list the middleware class in the `$middleware` property of your `app/Http/Kernel.php` class.

### [Assigning Middleware To Routes](https://laravel.com/docs/8.x/middleware#assigning-middleware-to-routes)

If you would like to assign middleware to specific routes, you should first assign the middleware a key in your application's `app/Http/Kernel.php` file. By default, the `$routeMiddleware` property of this class contains entries for the middleware included with Laravel. You may add your own middleware to this list and assign it a key of your choosing:

```php
// Within App\Http\Kernel class... 
protected $routeMiddleware = [

'auth' => \App\Http\Middleware\Authenticate::class,

'auth.basic' => \Illuminate\Auth\Middleware\AuthenticateWithBasicAuth::class,

'bindings' => \Illuminate\Routing\Middleware\SubstituteBindings::class,

'cache.headers' => \Illuminate\Http\Middleware\SetCacheHeaders::class,

'can' => \Illuminate\Auth\Middleware\Authorize::class,

'guest' => \App\Http\Middleware\RedirectIfAuthenticated::class,

'signed' => \Illuminate\Routing\Middleware\ValidateSignature::class,

'throttle' => \Illuminate\Routing\Middleware\ThrottleRequests::class,

'verified' => \Illuminate\Auth\Middleware\EnsureEmailIsVerified::class,

];
```

Once the middleware has been defined in the HTTP kernel, you may use the `middleware` method to assign middleware to a route:

```php
Route::get('/', function () {

//

})->middleware(['first', 'second']);
```

#### [Excluding Middleware](https://laravel.com/docs/8.x/middleware#excluding-middleware)

When assigning middleware to a group of routes, you may occasionally need to prevent the middleware from being applied to an individual route within the group. You may accomplish this using the `withoutMiddleware` method:

```php
use App\Http\Middleware\EnsureTokenIsValid;
Route::middleware([EnsureTokenIsValid::class])->group(function () {

Route::get('/', function () {

//

});

Route::get('/profile', function () {

//

})->withoutMiddleware([EnsureTokenIsValid::class]);

});


```

You may also exclude a given set of middleware from an entire [group](https://laravel.com/docs/8.x/routing#route-groups) of route definitions:

``` php
use App\Http\Middleware\EnsureTokenIsValid;

Route::withoutMiddleware([EnsureTokenIsValid::class])->group(function () {

Route::get('/profile', function () {

//

});

});
```



[[1. Laravel List|Nazad]]

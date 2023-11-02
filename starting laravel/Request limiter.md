### Dokumentacija sa lravelovog sajta
https://laravel.com/docs/8.x/routing#rate-limiting

kratki primeri

```php
protected function configureRateLimiting()

{

RateLimiter::for('global', function (Request $request) {

return Limit::perMinute(1000);

});

}
```


[[1. Laravel List|Nazad]]

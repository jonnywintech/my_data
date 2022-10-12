### U rutama kada se korisi whildcard iliti {ime}
po deafalt-u ide prvi parametar iz funkcije ili sa sistim imenom
https://joshanthony.info/2017/12/28/wildcards-in-laravel-routes/

takodje moze imati limite ili se rucno postaviti
ovo u linku je za chainovanje istog sa istog controllera

```php
Route::get('some/route/{whatever}', function(){ // do your stuff here
})->where('whatever', '.+');
```

## `?` se koristi kada neznamo da li ce postojati naziv u ruti

```php
// Use a question mark when the wildcard won't always show up in the route.
Route::get('some/route{whatever?}', function(){ // do your stuff here
})->where('whatever', '.+');
```

[[1. Laravel List|Nazad]]

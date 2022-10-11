## View
iz controllera importovati zeljenu klasu koja se prikazuje i njenu funciju iliti querry

```php
Route::get('/posts', [PostController::class, 'index']);
Route::get('/posts/{id}', [PostController::class, 'show']);
```

### ruta se prikazuje u blade templejtu  posts.blade.php

## View sa nazivom `name` ruta koji kasnije moze da se iskoristi
```php
Route::get('/news', [NewsController::class, 'index'])->name('show_news');
```

name se poziva u 
[[blade templates]]


[[1. Laravel List|Nazad]]

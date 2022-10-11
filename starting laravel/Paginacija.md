### Paginacija se radi u Controllery kada se poziva metoda
primer
```php
 public function index()
    {
        $allNews = News::with('user')->paginate(15);
        return view('news.index', compact('allNews'));
    }
```

u app/Providers/AppServiceProvider.php ukljucuje se bootstrap paginacija

primer

```php
namespace App\Providers;

use Illuminate\Pagination\Paginator;
use Illuminate\Support\ServiceProvider;

class AppServiceProvider extends ServiceProvider
{
    public function boot()
    {
        Paginator::useBootstrap();
    }
}
```

u blade templejtu se prikazuje sa sledecom komandom
```php
{{$allNews->links()}}
```

eager loading
```php
$news = News::with('user')->orderBy('created_at', 'desc')->paginate(5); //eager loading
```


[[1. Laravel List|Nazad]]

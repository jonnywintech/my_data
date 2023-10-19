Listanje svih ruta koje postoje

takodje  se moze iskoristiti  $route->getName()
da se dobije naziv route `route('ime-rute')`

ovo je jako korsno kada se pravi odobravanje ruta u admin panelu
```php
namespace App\Http\Controllers;

use Illuminate\Http\Request;
use Illuminate\Support\Facades\Route;

class TestController extends Controller
{
    public function index()
    {
        $arr = [];
        $all_routes = Route::getRoutes();
        foreach ($all_routes as $route) {
            array_push($arr,$route);
        }
        dd($arr);

    }
}

```

return code 
```d
 +uri: "logout"
              +methods: array:2 [▼
                0 => "GET"
                1 => "HEAD"
              ]
              +action: array:7 [▼
                "middleware" => array:3 [▶]
                "uses" => "App\Http\Controllers\UserController@logOff"
                "controller" => "App\Http\Controllers\UserController@logOff"
                "namespace" => null
                "prefix" => ""
                "where" => []
                "as" => "logOff"
              ]
              +isFallback: false
              +controller: null
              +defaults: []
              +wheres: []
              +parameters: null
              +parameterNames: null
              #originalParameters: null
              #withTrashedBindings: false
              #lockSeconds: null
              #waitSeconds: null
              +computedMiddleware: null
              +compiled: null
              #router: Illuminate\Routing\Router {[#26](http://127.0.0.1:8000/test#sf-dump-179225005-ref226 "30 occurrences")}
              #container: Illuminate\Foundation\Application {[#3](http://127.0.0.1:8000/test#sf-dump-179225005-ref23 "31 occurrences") …40}
              #bindingFields: []
```
# Pravljenje kontrollera
konvekcija je jednina i pocetno slovo je veliko a druga rec je Controller
```bash
php artisan make:controller PostController
```

controller sa crud funkcijama CRUD
```bash
php artisan make:controller PostController --resource
```

Postavljanje ruta - putanje url   primera  https:127.0.0.1/books i kako on izgleda u kontroleru

## sledeca akcija se zove  eloquent querry builder
## dokumentacija za zeljeni query  kada se pravi
https://laravel.com/docs/9.x/queries#introduction

prvo se importuje zeljeni table iz databaze iliti model 
```php 
use App\Models\Post;
```

imamo imena konvekcije za pisanje u svakom kontorlleru   index() show() create() store() delete() update()

## index
nova verzija
```php
public function index()
{$teams = Team::all();
 return view('teams.index', compact('teams'));
 }
```

strara verzija
```php
public function index()
{
$posts = Post::where('is_published', true)->get(); return view('posts', compact('posts')); // [ 'posts' => posts] }
}
```


## show 
findOrFail  u slucaju da ne nadje nista u databazi vratice 404 gresku umesto da crasure

```php
public function show($id)
{
$post = Post::findOrFail($id);
return view('post', compact('post'));
}

```

## create
```php
public function create(Request $request)
{
return view('create-post');
}
```

## store
!!! za store je bitno da se omoguci unos u dtabazu u [[Model]]-u

```php
public function store(Request request)
{
    $data = $request->only(['title', 'body', 'is_published']);

    $post = Post::create($data);

    return redirect("/posts/$post->id");
}
```

## Store sa foreign key-om
```php 
  public function store(CreateNewsRequest $request)

    {

        $data = $request->validated();

        $news = auth()->user()->news()->create($data);

        $news->teams()->attach($data['teams']);

        session()->flash('status_message',"Thank you for publishing the article on www.nba.com");

        return redirect('/news');

    }
```


### Redirekcija  
```php
return redirect("/posts/$post->id");
```

info je za debugovanje querija i starija verzija kako se pisalo
```php
public function store(Request request)
{
	DB::listen(function (query)
	{
		info($query->sql);
	});

    // $post = new Post();
    // $post->title = $request->get('title', '');
    // $post->body = $request->get('body', '');
    // $post->is_published = $request->get('is_published', false);
    // $post->save();

    // $data = [
    //     'title' => $request->get('title', ''),
    //     'body' => $request->get('body', ''),
    //     'is_published' => $request->get('is_published', false),
    // ];
    $data = $request->only(['title', 'body', 'is_published']);

    $post = Post::create($data);

    // return view('post', compact('post'));
    return redirect("/posts/$post->id");
}
```

podaci se salju na [[view]] 

[[napredno routovanje  iz  view-a]]

[[1. Laravel List|Back]]

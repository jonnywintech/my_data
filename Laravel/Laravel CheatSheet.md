# Laravel CheatSheet > Databaza

// umesto zagrada [   ]  uneti svoje podatke//

1. Posle instalacije Composera i Laravela /// za creiranje novog projekta

```bash
laravel new [ime_projekta]
```

2. Napraviti databazu za projekat u mysql-u

```sql
CREATE DATABASE   [database_name]       ;
```

3. Proveriti .env fajl koji sadrzi podatke o databazi na koju se konektuje
   
   .env fajl se nalazi u  folderu koji ste kreirali

4. Napraviti novi fajl koji se koristi kao template za  mysql table
   
   ```bash
   php artisan make:migration [ime_tabele] ## create_user_table
   ## primer
   php artisan make:migration create_books_table
   ```

5. Popuniti fajl  na lokaciji <mark>database/migration/[ime_fajla_bice_datum+ime__tabele]</mark>
   
   ```php
   public function up()
       {
           Schema::create('books', function (Blueprint $table) {
               $table->id();
               $table->string('title');
               $table->string('author');
               $table->foreignId('user_id')
               ->constrained()
               ->onDelete('cascade');
               $table->timestamps();
           });
       }
   
   // function down sluzi za dropovanje databaze
    public function down()
       {
           Schema::dropIfExists('books');
       }
   ```

6. ```php
   ->constrained() // je isto sto i 
   ->references('id')->on('author') // moze se koristiti i kao
   ->constrained('ime_tabele')
   ```
   
   <mark>Model za tabele </mark>
   
   [Database: Migrations - Laravel - The PHP Framework For Web Artisans](https://laravel.com/docs/9.x/migrations#creating-columns)
   
   Kada se popuni fajl sa odgovarajucim parametrima izvrsiti sledecu komandu da bi se tabela dodala u databazu
   
   ```bash
   php artisan migrate:fresh ##brise sve tabele i ponovo ih postavlja
   php artisan migrate:rollback #vraca tabele u predhodno stanje migracij
   php artisan migrate
   ```

Svak-a migracija prati redosled datuma fajla I sistem prati to

A belezi u tabeli migration

## U slucaju da pullujete neciji projekat > git clone

```bash
git clone https://github.com/drstvnvc/nk16-blog.git
cd nk16-blog

composer install
cp .env.example .env
php artisan key:generate
```

popuniti .env fajl sa podacima iz databaze i onda 

```bash
php artisan migrate
php artisan serve
```

u .env fajlu u slucaju da se radi u produkciji promeniti APP_ENV= production

u ovom slucaju daje upozorenje  u slucaju da slucajno ukucate komande koje 

mogu da izbrisu databaze ili tabele i time obrisete podatke

## za Pravljenje php modela i controlera

```bash
php artisan make:model Post #--migration
php artisan make:controller [imeControlora] #pravi kontroler fajl !!

php artisan migrate:status  #status migracija 
php artisan migrate:fresh #izvrsava reset nad databazom 
#i ponovu upisuje iste , (samo u slucaju nuzde)!!!
```

Podesavanja u Controlleru app/Http/Controllers

```php
namespace App\Http\Controllers;
use App\Models\Post; // ime Post zavisi od projekta do projekta i moze se menjati
use Illuminate\Http\Request;
class PostController extends Controller
{
    public function index()
    {
        $posts = Post::where('is_published', true)->get();
        return view('posts', compact('posts')); // [ 'posts' => $posts]
    }
// or 
     public function index()
  {
    $teams = Team::all();
    return view('teams.index', compact('teams'));
  }


    public function show($id)
    {
        // $post = Post::where('id', $id)->first();
        $post = Post::findOrFail($id);
        return view('post', compact('post')); // [ 'post' => $post]
    }
}
```

Ove dve funkcije se posle toga pozivaju u routes/web.php

```php
use App\Http\Controllers\PostController;
use Illuminate\Support\Facades\Route;
/*
|--------------------------------------------------------------------------
| Web Routes
|--------------------------------------------------------------------------
| Here is where you can register web routes for your application. These
| routes are loaded by the RouteServiceProvider within a group which
| contains the "web" middleware group. Now create something great!
|
*/
Route::get('/posts', [PostController::class, 'index']);
Route::get('/posts/{id}', [PostController::class, 'show']);
```

Creiranje posta ili cega vec

```php
 public function create(Request $request)
    {
        return view('create-post');
    }

    public function store(Request $request)
    {
        DB::listen(function ($query) {
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
}
```

A u Modelu se dodaje fillable

```php
  protected $fillable = [
        'title',
        'body',
        'is_published',
    ];
```

Primer forme

```php
<form method="POST" action="/posts">
    @csrf

    <input name="title" placeholder="Title" />
    <br/>
    <textarea name="body" placeholder="Body"></textarea>
    <br/>
    <input type="checkbox" name="is_published" value="1" id="is_published">
    <label for="is_published">Publish immediately</label>
    <br/>

    <button type="submit">Create a post</button>
</form>
```

### Validacija podataka -> middleware

```bash
# Generate a new form request validation request class.
php artisan make:request StoreDrinksPostRequest
```

unutar requesta

```php
public function rules()
    {
        return [
            'title' => 'required|string|max:255|unique:posts',
            'body' => 'required|string',
            'is_published' => 'sometimes',
        ];
    }
```

U ruti se dodaje <mark>StorePostReuquest</mark> umesto Requesta u store funkciji 

i importuje se <mark>klasa</mark>

```php
$data = request->only(['title', 'body', 'is_published']);
// ovo se brise i onda se pise sledece pri validaciji
 $data = $request->validated();
```

### Prikazivanje gresaka bojom u html-u

```php
@if ($errors->any())
<div class="alert alert-danger">
    <ul>
        @foreach ($errors->all() as $error)
        <li>{{ $error }}</li>
        @endforeach
    </ul>
</div>
@endif

<form method="POST" action="/posts">
    @csrf

    <input name="title" placeholder="Title" value="{{ old('title') }}" class="@error('title') alert-danger @enderror" /><br />
    @error('title')
    <div class="alert alert-danger">
        {{$message}}
    </div>
    @enderror

    <textarea name="body" placeholder="Body" class="@error('body') alert-danger @enderror">{{ old('body') }}</textarea><br />
    @error('body')
    <div class="alert alert-danger">
        {{$message}}
    </div>
    @enderror

    <input type="checkbox" name="is_published" value="1" id="is_published">
    <label for="is_published">Publish immediately</label>
    <br />

    <button type="submit">Create a post</button>
</form>
```

Pravljenje  stranice iz delova tako da sadrzaj bude dinamican i nema previse ponavljanja  u folderu  /resources/views prave se dva foldera  'layouts' i 'partials'

U layoutu se nalazi glavna sekcija webstranice head i   telo koje sadrzi 'partials'

```php
//main.blade.php
<!doctype html>
<html lang="en">
  <head>
    <title>@yield('title')</title>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS v5.0.2 -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css"  integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">

    <style>
        li{
            list-style: none;
        }
        .link {
            text-decoration: none;

        }

    </style>
  </head>
  <body style="background-image: url(https://wallpaperaccess.com/full/7317651.jpg)">
      @include('partials.navbar')
   <div class="main">
   @yield('main')
   </div>

    <!-- Bootstrap JavaScript Libraries -->
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.2/dist/umd/popper.min.js" integrity="sha384-IQsoLXl5PILFhosVNubq5LC7Qb9DXgDA9i+tQ8Zj3iwWAwPtgFTxbJ8NT4GN1R8p" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.min.js" integrity="sha384-cVKIPhGWiC2Al4u+LWgxfKTRIcfu0JTxR+EQDz/bgldoEyl4H0zUF0QKbrJ0EcQF" crossorigin="anonymous"></script>
  </body>
</html>
```

U partials se nalaze delovi stranice koji male sekcije koje se  @include u layouts

i uglavnom su header(navbar) i footer

oni su uglavnom cist HTML bez php-a

Komande  u stranicama

@include  ---  deo stranice koji se prilkjucuje glavnom sadrzaju (navbar / footer)

```php
 @include('partials.navbar')
```

@extends ---  iskoristi  napravljeni template  (header/footer)

```php
@extends('layouts.app')
```

@yield -- nalazi se u delu stranice gde su dinamicni podaci  i pozivaju se 

sa @section u novoj stranici

```php
<title>@yield('title')</title>
// onda ide druga stranica u kojoj je @include i onda -->
```

stranica na kojoj se poziva @yeld

```php
<!-- // nadogradnja na napravljeni template za header  -->
@extends('layouts/main')
<!-- // dodavanje imena naslovu stranice (Title) -->
@section('title','List of Cars')


@section('main')
<div class="container pt-5">
    <ul>
        @foreach ($cars as $car)
  <a class="link" href="/cars/{{$car->id}}"><li class="text-light  fs-3 m-2">{{$car->title}}</li></a>
        @endforeach
    </ul>

</div>
@endsection
```

Veze izmedju Tabela

1. hasone

2. hasMany

3. belongsTo

4. belongsToMany

ovo se izgugla ili istrazi eloquent relationship u laravel dokumentaciji

#### Relacija se pravi u Model folderu i pise se ovako

```php
public function team()
    {
        return $this->belongsTo(Team::class);
    }
```

ovo je  u  modelu igrac 

dalje se pise u kontroleru 

```php
 public function show($id)
  {
      $team = Teams::with('players')->findOrFail($id);//::with je relacija
 //izmedju databaza i smesta se u team variablu koja se prosledjue u view
    //   dd($team);
      return view('pages.team', compact('team'));
  }
```

random copy

```php
u web  routama je bitan redosled da jedna ruta ne upadne u drugu i nemoze izaci iz loop-a

https://laravel.com/docs/9.x/blade#forms

@csrf garantuje da je forma poslata sa laravelovog sajta

celokupan donji sadrzaj nalazi se u create funkciji  u  http controllera
https://laravel.com/docs/9.x/container#method-invocation-and-injection
illuminate\fasades\db

info("store a post')

DB:listen(function($query){


    info($query->sql)
})


storage/logs/laravel logs


u modelu php 

git --diff  //komanda za ispisati  razlike izmedju fajlova

https://laravel.com/docs/9.x/validation

validacija requsta da li su ispravni podaci 


$date  = $request->validate([
    'title'=> 'required|string|max:255|unique:posts';
    'category'=> 'required|integer|exist:categories,id';  za relacije verovatno
    'body'=> 'required|string';
]);

error validacija 

ispis 

@if ($errors->any())
    <div class="alert alert-danger">
        <ul>
            @foreach ($errors->all() as $error)
                <li>{{ $error }}</li>
            @endforeach
        </ul>
    </div>
@endif

klasa moze da se zacrveni kao nije ispravna tako sto se wrapuje class = " @error(title) danger @enderror"


@error ('title')

@enderror



https://laravel.com/docs/9.x/validation#form-request-validation


php artisan make:request StorePostRequest


$data  = $request->validated();

$post =Post::create($data);

return redirect("/posts/$post->id");

da se forma ne bi brisala iskoristiti Laravel repopulating u form

https://laravel.com/docs/9.x/validation#repopulating-forms




https://laravel.com/docs/9.x/validation#repopulating-forms

relacije izmedju tabela
php artisan make:model  -m  Comment

Schema::create('coments', function(Blueprint $table){
    $table->id();
    $table->text('body');
    $table->foreign('user_id)->references ('id')->on('users');
    // kraca verzija sa opcijom kada se obrise post da se brise i komentar
    $table-foreignId('user_id)->constainstrainde()
     ->onUpdate('cascade')
      ->onDelete('cascade');
    $table->timestamp();

})


php artisan migrate ;
```

### Factory  Method za Popunjavanje Databaze

pravljenje factorija

```bash
php artisan make:factory MovieFactory
```

```php
public function definition()
    {
        return [
            //
        ];

}
//popunjava se sa podacima iz tabele na sledeci nacin


return [
            'title' => $this->faker->word(),
            'genre' => $this->faker->word(),
            'director' => $this->faker->name(),
            'year' => $this->faker->year('now'),
            'storyline' => $this->faker->text(200),
            'url' => $this->faker->imageUrl($width = 640, $height = 480),
       ];
// v2

return [
            'first_name' => $this->faker->firstNameMale(),
            'last_name' => $this->faker->lastName(),
            'email' => $this->faker->email(),
            'teams_id' => $this->faker->numberBetween($min = 1, $max = 10),
        ];
```

[GitHub - fzaninotto/Faker: Faker is a PHP library that generates fake data for you](https://github.com/fzaninotto/Faker)

istraziti potrebne komande sa ovog linka u zavisnosti koja je sintaksa ptrebna

kada se popune sva polja onda se u fajlu DatabaseSeeder.php dodaje sledece u run funkciju

```php
 public function run()
    {
        // \App\Models\User::factory(10)->create();

        // \App\Models\User::factory()->create([
        //     'name' => 'Test User',
        //     'email' => 'test@example.com',
        // ]);

        Movie::factory(10)->create();
        Comment::factory(50)->create();
    }
```

```bash
php artisan migrate:fresh --seed
```

### Povezivanje Tabela

Povezivanje modela

u Modelu dodati sledece

```php
 public function team()
    {
        return $this->belongsTo(Team::class);
  
 }
 
// Team model koji sadrzi vise igraca 
 public function players()
    {
        return $this->hasMany(Player::class);
    }
  
```

povezivanje u show($id) funkciji 

```php

```

## Pivot tabela se creira sa komandom
```bash
php artisan make:migration create_news_team_table
```

drugrim recima  imena dve table odvojene _ znakom

ova tabela uglavnom sadrzi samo foreign id od dve tabele
### u modelu se dodaje funkcija sa imenom druge tabele koju vezujemo i ima 
News.php
```php
public function teams()
    {
        return $this->belongsToMany(Team::class, 'news_teams');
    }

```
Team.php

```php
    public function news()
    {
        return $this->belongsToMany(News::class, 'news_teams');
    }
```

u slucaju da imamo nazive koji nisu u jednini kada dodajemo tabelu , da bi laravel prepoznao potrebno je dodati tacne nazive tabela kako bi moga prepoznati 

```php
    public function teams()

    {

        return $this->hasMany(Team::class, ##table
         'news_team',
         ##foreign pivot key
         'news_id', 
         ##related pivot key
         'team_id');

    }
```

# Popunjavanje pivot tabele sa seederom
```php
   foreach(Team::all() as $team){

            $news = \App\Models\News::inRandomOrder()->take(rand(1,3))->pluck('id');

            $team->news()->attach($news);

        }
```


[[1. Laravel List|Nazad]]

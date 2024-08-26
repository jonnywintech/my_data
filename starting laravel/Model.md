### Konvekcija za pisanje modela je Veliko početno slovo i ime mora biti u jednini
```bash
php artisan make:model ImeModela
```
### `u modelu se tabele vezuju jedna za drugu funkcijama koje se napisu
### `posle toga ide ime modela -> ime funkcije koja povezuje drugu tabelu

### Dozvola za unosenje podataka u databazu
```php
protected $fillable = [ 'title', 'body', 'is_published', ];
```
## Alternativa
```php
protected $guarded = [];
```
ovo je suprotno od fillable, imenuju se polja koja su zasticena od unosa

### Mutator funkcija za validaciju passworda
```php
public function setPasswordAttribute($password)
{
	$this->attributes['password'] = bcrypt($password);
}
```

### Akcessor funkcija za  menjanje pocetnog slova u databazi
```php
public function getUsernameAttributes($username)
{
	return ucwords($username);
}
```
##### veze između databaza kada su povezane (relacije)
## kada tabela sadrzi više tabela
##### importovati klasu od relacione tabele 
players je samo jedan primer izmeniti sa vasim imenom modela

```php
public function players()
{
	return $this->hasMany(Player::class);
}
```


### kada tabela pripada drugoj tabeli
##### importovati klasu od relacione tabele 
players je samo jedan primer izmeniti sa vasim imenom modela

```php
//nezaboravite 
use App\Models\User;

public function team()
{
	return $this->belongsTo(Team::class);
}
```

Ako ne prepoznaje model mora se dodati 'foreign_id' koje je vezan za klasu koja je upravo napisana i onda strani kljuc u trenutnoj tabeli

```php
public function team()
{
	return $this->belongsTo(Team::class,'id', 'team_id');
	//			vezano je za klasu koja je upravo napisana
	//				prvo njen id pa onda strani kljuc u tabeli
}
```

#### Napredne relacije u  pivot tabeli kada se ne koristi model za pivot tabelu
```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Model;
use Illuminate\Database\Eloquent\Factories\HasFactory;

class Post extends Model
{
    use HasFactory;

    protected $guarded = [];

    public function categories()
    {
        return $this->belongsToMany(BlogCategory::class, 'blog_category_post', 'post_id', 'category_id');
    }

    public function tags()
    {
        return $this->belongsToMany(BlogTag::class, 'blog_post_tag', 'post_id', 'tag_id');
    }
    public function user()
    {
        return $this->belongsTo(User::class);
    }
}

```
blog_category_post -- naziv tabele
post_id -- naziv kolone iz koje se cita ili upisuje
category_id -- naziv kolone iz koje se cita ili upisuje

bitno je upisate obe kolone iz pivot tabele jer ce se desiti greska pri upisivanju ako se upise samo jedna

[[Controller]]



[[1. Laravel List|Nazad]]

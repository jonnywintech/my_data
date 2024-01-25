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


[[Controller]]



[[1. Laravel List|Nazad]]

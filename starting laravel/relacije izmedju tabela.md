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
//importovati
public function team()
{
	return $this->belongsTo(Team::class);
}
```


#### ovim se vezuju tabele jedne za drugu 

na primer kada  se kasnije pristupa iz team contorllera
$team->`players`  <-ime funkcije

ovime se pristupa podacima


[[1. Laravel List|Nazad]]

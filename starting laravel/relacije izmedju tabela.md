## kada tabela sadrzi više tabela
##### importovati klasu od relacione tabele 
players je samo jedan primer izmeniti sa vasim imenom modela
### Pri pravljenju relacija samo se zapitate Koja je Funkcija trenutnog Modela u kome se pise funkcija
`hasOne, hasMany, belongsTo, belongsToMany` koristimo odgovarajuce recia za konekciju
```

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

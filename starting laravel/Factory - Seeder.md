# Popunjavanje databaze Automatski
### 1. Najpre se pravi Factory za zeljenji model
```bash
php artisan make:factory NewsFactory
```
u factoriju se unose polja iz databaze na sledeci nacin

```php
 public function definition()

    {

        return [

            'title' => $this->faker
            ->realTextBetween($minNbChars = 7, $maxNbChars = 20, $indexSize = 2),

            'content' => $this->faker
            ->realTextBetween($minNbChars = 160, $maxNbChars = 200, $indexSize = 2),

            'user_id' => User::inRandomOrder()->select('id')->first()

        ];

    }
```
za faker  komande pogledati  <a href="https://github.com/fzaninotto/Faker"> Ovde </a> (faker dokumentacija na gitu)

### `onda se u Seederu tacnije DatabaseSeeder.php instacira klasa na sledeci nacin`

```php
 Team::factory(10)->create();
```
zeljeni broj u bazi koliko ce biti polja

# za pivot tabelu se koristi foreach metoda da popuni podatke ili se zove klasa
primer loopa za popunjavanje pivot tabele

```php
  

        foreach(Team::all() as $team){

            $news = \App\Models\News::inRandomOrder()
            ->take(rand(1,100))->pluck('id');

            $team->news()->attach($news);

        }
```

### primer pozivanje clase factory
```php
public function definition()
{
	'user_id' => User::factory(),
	'category_id' => Category::factory(),
	'title' => $this->faker->senence,
	'excerpt' => $this->faker->sentence,
	'body' => $this->faker->paragraph
}
```

ukoliko se samo databaze seeduje i potrebno je refreshovati podatke svaki put
da bi se  dropovale tabele dodati
```php
User::truncate();
Post::truncate();
Category::truncate();
```

ukoliko je potrebno dodati samo specificno polje na primer ime to se moze uraditi u DatabaseSeeder.php
```php
User::factory()->create([
'name' => 'John Doe'
]);
```
ovo ce se odnositi samo za ovo polje


[[1. Laravel List|Nazad]]

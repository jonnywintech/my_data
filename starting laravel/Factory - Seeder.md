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

            'title' => $this->faker->realTextBetween($minNbChars = 7, $maxNbChars = 20, $indexSize = 2),

            'content' => $this->faker->realTextBetween($minNbChars = 160, $maxNbChars = 200, $indexSize = 2),

            'user_id' => User::inRandomOrder()->select('id')->first()

        ];

    }
```
za faker  komande pogledati  <a href="https://github.com/fzaninotto/Faker"> Ovde </a> (faker dokumentacija na gitu)

onda se u Seederu tacnije DatabaseSeeder.php instacira klasa na sledeci nacin

```php
 Team::factory(10)->create();
```
zeljeni broj u bazi koliko ce biti polja

## za pivot tabelu se koristi foreach metoda da popuni podatke
primer loopa za popunjavanje pivot tabele

```php
  

        foreach(Team::all() as $team){

            $news = \App\Models\News::inRandomOrder()->take(rand(1,100))->pluck('id');

            $team->news()->attach($news);

        }
```


[[1. Laravel List|Nazad]]

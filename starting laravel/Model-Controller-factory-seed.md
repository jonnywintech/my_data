### Shortcut to generate a model, migration, factory, seeder, policy, controller, and form requests...
```bash
php artisan make:model Flight --all
```


### Generate a model and a migration, factory, seeder, and controller...
```bash
php artisan make:model Flight -mfsc
```


[[Laravel_Faker_seeder|Faker]]

sve ostale funkcije

```bash
# Generate a model and a FlightFactory class...

php artisan make:model Flight --factory

php artisan make:model Flight -f

# Generate a model and a FlightSeeder class...

php artisan make:model Flight --seed

php artisan make:model Flight -s

# Generate a model and a FlightController class...

php artisan make:model Flight --controller

php artisan make:model Flight -c

# Generate a model, FlightController resource class, and form request classes...

php artisan make:model Flight --controller --resource --requests

php artisan make:model Flight -crR

# Generate a model and a FlightPolicy class...

php artisan make:model Flight --policy

# Generate a model and a migration, factory, seeder, and controller...

php artisan make:model Flight -mfsc

# Shortcut to generate a model, migration, factory, seeder, policy, controller, and form requests...

php artisan make:model Flight --all

# Generate a pivot model...

php artisan make:model Member --pivot
```



[[1. Laravel List|Nazad]]

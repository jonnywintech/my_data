Prikaz gresaka na frontendu se vrsi preko `@error('ime_polja')` u blade templjetu

primeri za formu

```php
<input type='text' name='username' id='username' value ='{{old ('usernname')}}' required>

@error('name')
<p class='text-red-500'> {{$message}} </p>
@enderror
```
`value = '{{ old('username') }}'` u slucaju da se pogresno popuni forma, kada da se refreshuje stranica zadrzani su stari podaci. ovo je dobro koristiti za sva polja osim `password` polja

### Alternativno SpitOut errors
```php
@foreach ($errors->all() as $error)
	<li> {{$error}} </li>
@endforeach
```

[[1. Laravel List|Nazad]] 


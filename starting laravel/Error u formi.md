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
if($errors->any())
<ul>

@foreach ($errors->all() as $error)
	<li> {{$error}} </li>
@endforeach

</ul>

@endif
```


# Flash Messages
session flash su poruke koje ostaju u sesiji samo jedan reload paga zato su jako korisne
kljuc koji se dodeljuje sesiji moze biti bilo sta  u ovom slucaju je success

```php
session()->flash('success', 'Your account has been created.');
```
i onda se u blade templejtu dodaje
```php
if(session->has('success'))

<div>

<p> {{ session()->get('success') }} </p>
// ili shorthand session 
<p> {{ session('success') }} </p>

</div>
```

u slucaju redirekcije 
```php
return redirect('/')->with('success', 'Your account has been created.');
```

[[1. Laravel List|Nazad]] 
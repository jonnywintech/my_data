# Blade templates

#### nalazi se u ruti /resurces/view
imamo vise vrsta komandi i redosled je sledeci  (model kako bi trebao da sadrzi blade fajl)
```php
@yield('title')
@include('partials.navbar')

// glavni faj koji prikljucuje  fajlove iz /layout
@extends('layouts.home')   // nadogradjuje ovaj template koji vec sadrzi neke
//komponente koji mogu da se menjaju ako sadrze @yield funkciju

@section('title', 'blog') 
// kada se unese ovako nema potrebe da se zatvara sa @endsection
@section('main')
// sadrzaj koji se izvrsava na ovom delu
@endsection 
//kraj ove sekcije
```

konvekcija za pravljenje foldera
Navbar i Footer se odvajaju u poseban folder takodje Sidebar ili drugi elementi ako postoje
#### /resurces/view/partials
to su obicni html fajlovi koji se dodaju

#### /resurces/view/layout
glavni fajl koji se koristi kao template koji povezuje sve ostale delove

### @yield je deo koji je promenljiv i prikljucuje se sa nove stranice koja se napravi
```php
@yield('title')
```

### @include je deo koji je statican i prikljucen je uvek staticno
```php
@include ('partials.navbar')
```
## Primeri 
### Primer glavnog fajla na ruti /resources/view

```php
@extends('layout.home')

@section('title', 'Teams')

  

@section('content')

<div class="container mx-auto px-2">

<h1 class="my-4">List of All Teams</h1>

  

<div class="list-group">

    @foreach ($teams as $team)

  

    <a href="/team/{{$team->id}}" class="list-group-item list-group-item-action">{{$team->name}}</a>

    @endforeach

</div>

</div>

  

@endsection
```



### primer layouta (u mom slucaju  main.blade.php)

```php
//main.blade.php
<!doctype html>
<html lang="en">
  <head>
  // title koji se menja u novom
    <title>@yield('title')</title>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS v5.0.2 -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css"  integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">

    <style>
        li{
            list-style: none;
        }
        .link {
            text-decoration: none;

        }

    </style>
  </head>
  <body style="background-image: url(https://wallpaperaccess.com/full/7317651.jpg)">
      @include('partials.navbar')
   <div class="main">
   @yield('main')
   </div>

    <!-- Bootstrap JavaScript Libraries -->
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.2/dist/umd/popper.min.js" integrity="sha384-IQsoLXl5PILFhosVNubq5LC7Qb9DXgDA9i+tQ8Zj3iwWAwPtgFTxbJ8NT4GN1R8p" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.min.js" integrity="sha384-cVKIPhGWiC2Al4u+LWgxfKTRIcfu0JTxR+EQDz/bgldoEyl4H0zUF0QKbrJ0EcQF" crossorigin="anonymous"></script>
  </body>
</html>
```


primer za header koji ukljucuje Navbar     navbar.blade.php


```php
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">

    <div class="container-fluid">

      <a class="navbar-brand" href="/">NBA Teams</a>

      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarText" aria-controls="navbarText" aria-expanded="false" aria-label="Toggle navigation">

        <span class="navbar-toggler-icon"></span>

      </button>

      <div class="collapse navbar-collapse" id="navbarText">

        <ul class="navbar-nav me-auto mb-2 mb-lg-0">

          <li class="nav-item">

            <a class="nav-link active" aria-current="page" href="/">Home</a>

          </li>

          <li class="nav-item">

            <a class="nav-link" href="/">Teams</a>

          </li>

          <li class="nav-item">

            <a class="nav-link" href="/create">Create</a>

          </li>

          <li class="nav-item">

            <a class="nav-link" href="/about">About</a>

          </li>

        </ul>

        <span class="navbar-text">

          Lorem ipsum dolor sit amet consectetur, adipisicing elit.

        </span>

      </div>

    </div>

  </nav>
```



[[1. Laravel List|Back]]

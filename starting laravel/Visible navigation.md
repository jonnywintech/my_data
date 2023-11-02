## `@auth` je ruta vidljiva samo ulogovanom korisniku

## `@guest` ruta je vidljiva samo neulogovanom korisniku

live primeri

```php
           @auth
            <li class="nav-item">
                <span class="nav-link">{{auth()->user()->name}}</a>
            </li>
            <li class="nav-item">
                <form method="POST" action="/logout">
                    @csrf
                    <button class="btn btn-link nav-link" type="submit">Logout</button>
                </form>
            </li>
            @endauth

            @guest
            <li class="nav-item">
                <a class="nav-link" href="/register">Register</a>
            </li>

            <li class="nav-item">
                <a class="nav-link" href="/login">Login</a>
            </li>
            @endguest
```


[[1. Laravel List|Nazad]]

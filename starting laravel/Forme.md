Login / Register primeri forme


## Login Forma
najbitnija stavka je @csrf token bez kojeg forma nece raditi
```php
 <form method="POST" action="/login">
        @csrf
        {{-- email --}}
        <input type="email" name="email" placeholder="Email">
        <br>
        {{-- password --}}
        <input type="password" name="password" placeholder="Password">
        <br>
        {{-- Invalid Credentials --}}
        @if (isset($invalidCredentials) && $invalidCredentials == true)
            <div>
                Invalid email or password!
            </div>
            <br>
        @endif
        <button type="submit">Register!</button>
    </form>
```

## Logout
```php
   <div>
        <form method="POST" action="/logout">
            @csrf
            <button type="submit">Logout</button>
        </form>
    </div>
```

## Register Forma

```php
 <form method="POST" action="/register">
            @csrf
            {{-- name --}}
            <input type="text" required name="name" placeholder="Name">
            <br>
            @error('name')
                <div>
                    {{ $message }}
                </div>
                <br>
            @enderror
            {{-- email --}}
            <input type="email" required name="email" placeholder="Email">
            <br>
            @error('email')
                <div>
                    {{ $message }}
                </div>
                <br>
            @enderror
            {{-- password --}}
            <input type="password" required name="password" placeholder="Password">
            <br>
            @error('password')
                <div>
                    {{ $message }}
                </div>
                <br>
            @enderror
            {{-- password confirmation --}}
            <input type="password" required name="password_confirmation" placeholder="Confirm password">
            <br>
            @error('password_confirmation')
                <div>
                    {{ $message }}
                </div>
                <br>
            @enderror
            <button type="submit">Register!</button>

        </form>
```



[[1. Laravel List|Nazad]]

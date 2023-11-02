## Register  / Login
najpre napraviti kontroller koji ce se koristiti za login i register

primer

```bash
php artisan make:controller AuthController
```

vracanje view-a iz AuthControllera sa register formom
```php
 public function getRegisterForm()
    {
        return view('auth.register');
    }
```

registracija korisnika
```php
  public function register(RegisterRequest $request)
    {
        $data = $request->validated();
        $data['password'] = Hash::make($data['password']);
        $user = User::create($data);
        Auth::login($user);
        return redirect('/');
    }
```

login forma -get
```php
public function getLoginForm()
    {
        return view('auth.login');
    }
```

logovanje korisnika
```php
public function login(Request $request)
    {
        $credentials = $request->only('email', 'password');
        if (Auth::attempt($credentials)) {
	        session()->regenerate();
            return redirect('/')->with('success', 'Welcome back!');
        } else {
            view('login', ['invalidCredentials' => true]);
        }
    }
```

logout
```php
public function logout()
    {
        Auth::logout();
        return redirect('/login');
    }
}
```

### Sledeci korak je register request iliti validacija unetih podataka pre unosenja u databazu [[RegisterRequest]]



celokupan primer controllera
```php
<?php

namespace App\Http\Controllers;

use App\Http\Requests\RegisterRequest;
use Illuminate\Http\Request;
use Illuminate\Support\Facades\Hash;
use App\Models\User;
use Illuminate\Support\Facades\Auth;

class AuthController extends Controller
{
    public function getRegisterForm()
    {
        return view('auth.register');
    }
    public function register(RegisterRequest $request)
    {
        $data = $request->validated();
        $data['password'] = Hash::make($data['password']);
        $user = User::create($data);
        Auth::login($user);
        return redirect('/');
    }
    public function getLoginForm()
    {
        return view('auth.login');
    }
    public function login(Request $request)
    {
        $credentials = $request->only('email', 'password');
        if (Auth::attempt($credentials)) {
            return redirect('/');
        } else {
            view('login', ['invalidCredentials' => true]);
        }
    }
    public function logout()
    {
        Auth::logout();
        return redirect('/login');
    }
}
```

## `bitna stavka je dodati u [[we]]`


[[1. Laravel List|Back]]

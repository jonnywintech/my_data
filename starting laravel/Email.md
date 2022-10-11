# Konfiguracija Za Mailtrap
## `-napraviti account na mailtrapu
## `-kopirati configuraciju u .env fajl`

### Kreira se UserController i VerificationMail

```bash
php artisan make:controller UserController;

php artisan make:mail VerificationMail;
```
### dodavanje migracije za verifikovanog korisnika
```bash
php artisan make:migration alter_user_table_add_is_verified_column
```
```php
    public function up()
    {
        Schema::table('users', function (Blueprint $table) {
            $table->boolean('is_verified')->default(false);
        });

	 public function down()
    {
        Schema::table('users', function (Blueprint $table) {
            $table->dropColumn('is_verified');
        });
    }
```

### U auth controlleru dodati klase

```php
use App\Mail\VerificationMail;
use Illuminate\Support\Facades\Mail;
```

pri registraciji se dodaje sledece     pre redirecta na login
```php
Mail::to($user->email)->send(new VerificationMail($user));
```
primer cele funkcije
```php
 public function register(RegisterRequest $request)

    {

        $data = $request->validated();

        $data['password'] = Hash::make($data['password']);

        $user = User::create($data);

        Mail::to($user->email)->send(new VerificationMail($user));

        return redirect('/login');

    }
```

### login funkcija primer

```php
 public function login(Request $request)

    {

        $credentials = $request->only('email', 'password');

        if (Auth::attempt($credentials)) {

            return redirect('/');

        } else {

           return view('login', ['invalidCredentials' => true]);

        }

    }
```


### User Controller
```php
 public function store($id)

    {

        $user = User::findOrFail($id);

        $user->is_verified = true;

        $user->email_verified_at = now();

        $user->save();

        return redirect('/login');

    }
```


## Primer VerificationMail.php

```php
class VerificationMail extends Mailable
{
    use Queueable, SerializesModels;
    private $user;
    /**
     * Create a new message instance.
     *
     * @return void
     */
    public function __construct($user)
    {
        $this->user = $user;
    }

    /**
     * Build the message.
     *
     * @return $this
     */
    public function build()
    {
        return $this->view('email.verification_mail')->with(['userId' => $this->user->id]);
    }
}
```

#### verification_mail.blade.php
model kako izgleda mail
```php
<html>

<head>
</head>

<body>
    <div>
        Click on <a href="http://127.0.0.1:8000/verify/{{ $userId }}">this</a> to verify your account
    </div>
</body>

</html>
```

### dodavanje rute za verifikaciju  u view
```php
use App\Http\Controllers\UserController;

Route::get('/verify/{id}', [UserController::class, 'store']);
```


[[1. Laravel List|Nazad]]


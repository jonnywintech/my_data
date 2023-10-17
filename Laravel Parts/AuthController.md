```php
class AuthController extends Controller
{

    // Auth::login($user) - setuj ulogovanog korisnika na sesiju
    // Auth::attempt($credentials) - provjeri da li postoji korisnik sa datim kredincijalima i uloguj ga
    // Auth::check() - provjeri da li postoji ulogovani korisnik (da li na sesiji postoji id ulogovanog korisnika)
    // Auth::id() - dobavi id ulogovanog korisnika sa sesije
    // Auth::user() - dobavi korisnika iz baze koji ima id ulogovanog korisnika sa sesije
    // Auth::logout() - ukloni ulogovanog korisnika sa sesije
    // sve metode mogu da se koriste i kao auth()-><method>()


    // Auth::user()
    // Provjerimo da li je token potpisan našim secretom
    // Raspakujemo token i provjerimo da li je istekao
    // Provjerimo da li je token blacklistovan
    // Provjerimo da li u bazi postoji user sa ID-em iz "sub" atributa u tokenu

    public function login(Request $request)
    {
        $credentials = $request->only(['email', 'password']);

        // $user = User::where('email', $credentials['email'])->first();
        // if ($user == null) {
        //     return response()->json([
        //         'message' => 'Invalid credentials'
        //     ], Response::HTTP_UNAUTHORIZED);
        // }
        // $password_correct = Hash::check($credentials['password'], $user->password);
        // if (!$password_correct) {
        //     return response()->json([
        //         'message' => 'Invalid credentials'
        //     ], Response::HTTP_UNAUTHORIZED);
        // }
        // Auth::login($user);

        // Auth::attempt($credential) trazi korisnika po emailu $credentials['email']
        // provjerava da li se $credentials['password'] poklapa sa hash-om korisnikovog passworda u bazi
        // ako je sve ok - uloguje korisnika, tj upise id ulogovanog korisnika na sesiju
        // ako nesto od provjera nije ok - vraca false
        $token = Auth::attempt($credentials);

        if ($token) {
            return response()->json([
                'token' => $token,
                'user' => Auth::user(),
            ]);
        } else {
            return response()->json([
                'message' => 'Invalid credentials'
            ], Response::HTTP_UNAUTHORIZED);
        }
    }

    public function register(RegisterRequest $request)
    {
        $data = $request->validated();
        $data['password'] = Hash::make($data['password']);
        $user = User::create($data);

        $token = Auth::login($user);

        return response()->json([
            'token' => $token,
            'user' => $user,
        ]);
    }

    public function getActiveUser()
    {
        return response()->json(Auth::user());
    }

    public function logout()
    {
        Auth::logout();
    }
}
```
# weback.mix.js
prva komanda koja je potrebna je instaliranje npm paketa 
```bash
npm install
```

nalazi se u root direktorijumu laravela

ovaj fajl sadrzi kompajler za sass i css i menja se njegov sadrzaj u

```javaScript
mix.js('resurces/js/app.js', 'public/js')
	.sass('resources/sass/app.scss', 'public/css')
```

glavni fajl se naziva app.css i nalazi se u `resources/sass`

u app.scss moze se takodje importovati bootstrap direktno sa komandom
```sass
@import '~bootstrap/scss/bootstrap';
```

pokrece sa kao i gulp sa npm komandama

```bash
npm run dev
```

u glavnom fajlu (index.blade.php) iskoriscava se link za stylesheed i koristi se blade direktiva za postavljanje dinamicnog css fajla

```php
<link rel="stylesheet" href="{{ mix('/css/app.css') }}" >
```

komanda koja non-stop prati dogadjaje na css fajlu i kompajluje kako se promeni slicna je gulp-u

```bash
npm run watch
```



[[1. Laravel List|Nazad]]

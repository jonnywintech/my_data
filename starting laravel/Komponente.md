### Instrukcije
napravi se blade template u `partials` folderu
sa sadrzajem 
```php 
<div class="title m-b-md">

	{{ $slot }}
	
</div>
```

## `Slot`  variabla se koristi za dinamican tekst koji unosimo u componentu

```php
@component('patials.hero')

	This is my Home Page
	
@endcomponent
```



[[1. Laravel List|Nazad]]

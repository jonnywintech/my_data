

### Primer za layout

Pravljenje `View layouta`
```bash
php artisan make:component App --view
```
### Primer za komponentu

Komponente i layouti se prave artisan komandom
```bash
php artisan make:component CustomComponent
```
ovo pravi 2 fajla

Prvi je klasa koja vraca view a drugi je sam view

Klasa
```php
// app/View/Components/CustomComponent.php

namespace App\View\Components;

use Illuminate\View\Component;

class CustomComponent extends Component
{
    public function render()
    {
        return view('components.custom-component');
    }
}
```

blade gde  je kreirana komponenta
```html
<!-- resources/views/components/custom-component.blade.php -->
<div>
    <!-- Your component HTML goes here -->
    This is a custom component.
</div>
```

blade gde se poziva
```html
<x-app-layout>
    <x-slot name="header">
        <h2 class="font-semibold text-xl text-gray-800 leading-tight">
            {{ __('Dashboard') }}
        </h2>
    </x-slot>

    <!-- OSTALE KOMPONENTE -->

    <!-- OVDE  SE POZIVA -->
    <x-custom-component />
    <!-- samo zatvarajuca komponenta slican react-u -->
</x-app-layout>
```

### Komponente sa podacima koji se prosledjuju

Klasa
```php
// app/View/Components/UserProfile.php

namespace App\View\Components;

use Illuminate\View\Component;

class UserProfile extends Component
{
    public $name;
    public $email;

    public function __construct($name, $email)
    {
        $this->name = $name;
        $this->email = $email;
    }

    public function render()
    {
        return view('components.user-profile');
    }
}

```

blade 
```html
<!-- resources/views/components/user-profile.blade.php -->

<div>
    <p>Name: {{ $name }}</p>
    <p>Email: {{ $email }}</p>
</div>

```

blade gde se poziva
```html
<!-- resources/views/layouts/app.blade.php -->

<x-user-profile name="John Doe" email="john@example.com" />

```

### Ovo je primer za Layout

layout se kreira i onda se extenduje
umesto `@content('content')`
`@endcontent`

Controller zove componentu koja sadrzi sledece
```php
<x-app-web-layout>
	<h4> Welcome </h4>
</x-app-web-layout>
```

`x-app-web-layout` je naziv layouta i time se ovom layoutu prosledjuje `<h4> Welcome</h4>`

`x-app-web-layout` ima `{{$slots}}` variablu koja je placeholder za data koj i se prosledjuje 

[[1. Laravel List|Nazad]]
komanda za pravljenje formi
```bash
php artisan livewire:form <formName>
```

u novoj kreiranoj formi dodati
```php
class LivewireForm extends form {
	# [Rule( ' required Imin:3 Imax: 255 ' ) ]
	public $subject;
	# [Rule( required Imin:5 Imax: 255 ' ) ]
	public $message;
}
```

onda se dodaje u stranici
```php

class SimplePage {

public LivewireForm $form; // kljucna rec form onda se onda koristi u blejdu
}
```

validacija
```php
public function submitForm(){
	$this->form->validate();
	// sending email
	session()->flash('success', 'form submited!');
	$this->form->reset ( ) ;
}
```

u blejdu se poziva
```php
<label for="email"> email </label>
<input wire:model"form.email" type="email" id="email" class="shadow-sm bg-...">
@error('form.email')
	<span class="text-red-500 text-xs"> {{ $message }} </span>
@enderror
```
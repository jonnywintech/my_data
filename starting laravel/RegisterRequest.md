## Validacija unetih podataka pre inserta u databazu

pravljenje requesta  (konvekcija je da se napise puno ime requesta za sta se koristi)
```bash
php artisan make:request RegisterRequest
```

u ruti app/Http/Requests/RegisterRequest.php

```php
 public function authorize()
    {
        return true;
    }
```

polja za validaciju se unosi ovde 
```php
 public function rules()
    {
        return [
            'name' => 'required|string|max:255',
            'email' => 'required|email|unique:users',
            'password' => 'required|string|confirmed',
        ];
    }
```
dokumentacija za validation rules

https://laravel.com/docs/9.x/validation#available-validation-rules

codegrepper
```php
$rules = [
        'name' => 'required',
        'email' => 'required|email',
        'message' => 'required|max:250',
    ];

    $customMessages = [
        'required' => 'The :attribute field is required.'
    ];

    $this->validate($request, $rules, $customMessages);
```


sva pravila
```
# <values> = foo,bar,...
# <field> = array field
# <characters> = amount of characters

# accepted					           # active_url
# after:<tomorrow>			           # after_or_equal:<tomorrow>
# alpha						           # alpha_dash
# alpha_num					           # array
# bail 					               # before:<today>
# before_or_equal:<today>              # between:min,max
# boolean					           # confirmed
# date						           # date_equals:<today>
# date_format:<format> 		           # different:<name>
# digits:<value>			           # digits_between:min,max
# dimensions:<min/max_with>	           # distinct
# email						           # ends_with:<values>
# exclude_if:<field>,<value>           # exclude_unless:<field>,<value>
# exists:<table>,<column>	           # file
# filled					           # gt:<field>
# gte:<field>				           # image
# in:<values>				           # in_array:<field>
# integer					           # ip
# ipv4                                 # ipv6  
# json						           # lt:<field>
# lte:<field>       		           # max:<value>
# mimetypes:video/avi,...	           # mimes:jpeg,bmp,png
# min:<value>				           # not_in:<values>
# not_regex:<pattern> 		           # nullable
# numeric					           # password:<auth guard>
# present					           # regex:<pattern>
# required					           # required_if:<field>,<value>
# required_unless:<field>,<value>      # required_with:<fields>
# required_with_all:<fields>	       # required_without:<fields>
# required_without_all:<fields>        # same:<field>
# size:<characters>			           # starts_with:<values>
# string						       # timezone
# unique:<table>,<column>		       # url
# uuid
```



[[1. Laravel List|Nazad]]

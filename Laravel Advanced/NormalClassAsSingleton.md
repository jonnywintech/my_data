# Koristiti laravel CLass as Singleton

u zagalvlju php fajla kada se `use #putanjaKontrollera` dodati `Facades` ispred \App

primer
```php
<?php

use Illuminate\Http\Request;
use Illuminate\Support\MessageBag;

use App\Http\Controllers\Controller;
use Illuminate\Support\Facades\DB;

/// 
//singleton deo
//

use Facades\App\Http\Request;


```
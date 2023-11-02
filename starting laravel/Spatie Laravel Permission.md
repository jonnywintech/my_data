### u User.php dodajemo sledece
```php
// pored 
class User extends Authenticatable

{

    use HasApiTokens, HasFactory, Notifiable //ovde;
//dodaje se sledece;
HasRoles
// takodje se importuje klasa;

```

finalni izgled

```php
 use HasApiTokens, HasFactory, Notifiable, HasRoles;
```
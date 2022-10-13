# moze se dodati na 2 nacina 
### 1. u view-u u ovom primeru desava se odprilike sledece
```php
Route::get('posts/{post:slug}',function(Post $post){
return view('post', ['post' => $post]);
});

```
// `Post::where('slug',$post)->firstOrFail()`
trazi prvi slug na koji naidje u postu

### 2. U modelu se dodaje sledeca funkcija i apsolutno je nebitno sta stoji kao {whildcard} u ruti
```php
public function getRouteKeyName()
{
	// return parent::getRouteKeyName();
	return 'slug';
}
```


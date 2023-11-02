## Napraviti  novo pravilo sa komandom
```bash
php artisan make:rule NoInappropriateWordsRule

```

app/Http/Request/CreateCommentRequest.php
u requestu za commente sa kojim filtriramo reci dodati
```php
use App\Rules\NoInappropriateWordsRule;

public function rules()
    {
        return [
            'content' => ['required', 'string', new NoInappropriateWordsRule ]
        ];
    }
```

u app/Rules/NoInappropriateWordsRule.php dodati sledece komande za filterovanje

```php

	private $field;
    private const BAD_WORDS = ['hate', 'idiot', 'stupid'];

 public function passes($attribute, $value)
    {
        $this->field = $attribute;
        foreach (self::BAD_WORDS as $badWord) {
            if (str_contains($value, $badWord)) {
                return false;
            }
        }
        return true;
    }

 public function message()
    {
        return "The {$this->field} field has inappropriate content.";
    }

```

u blade templejtu  dodati error
```php
@include('partials.error-message', [ 'field' => 'content' ])
```

ceo primer templejta
resources/views/teams/show.blade.php
```php
        <div class="form-group">
            <label for="content">Comment</label>
            <textarea name="content" class="form-control" id="content" rows="3" placeholder="Write your comment here..."></textarea>
            @include('partials.error-message', [ 'field' => 'content' ])
        </div>
        <button type="submit" class="btn btn-primary">Submit</button>
    </form>
```


[[1. Laravel List|Nazad]]

## Napraviti novi mail sa komandom
```bash
php artisan make:mail CommentReceived
```

u app/Http/Controllers/CommentController.php  `u store ()` dodati

```php
use App\Mail\CommentReceived;

Mail::to($team)->send(new CommentReceived($comment));
```

### u CommentReceived.php dodati
```php
private $comment;





 public function __construct(Comment $comment)
  {
    $this->comment = $comment;
  }




public function build()
  {
    return $this->view('emails.comment-received')->with([
      'comment' => $this->comment->content,
      'team' => $this->comment->team->name,
      'user' => $this->comment->user->name
    ]);
  }

```

napraviti blade template  resources/views/emails/comment-received.blade.php    i u njega dodati 

```php
<h3>Comment received</h3>
<p>Hello, {{$team}}</p>
<p>You have received a new comment:</p>
<blockquote>{{$comment}}</blockquote>
<p>from: {{$user}}</p>
```


[[1. Laravel List|Nazad]]

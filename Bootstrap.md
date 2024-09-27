Navbar
```html
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-fluid">
        <a class="navbar-brand" href="/">Galleries</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarText"
            aria-controls="navbarText" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarText">
            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                <li class="nav-item">
                    <a class="nav-link active" aria-current="page" href="/">Home</a>
                </li>
                @if (session('user_id'))
                    <li class="nav-item">
                        <a class="nav-link" href="/my-galleries">My Galleries</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="{{route('profile',['id'=> session('user_id')])}}">Profile</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="{{route('get.gallery')}}">Create gallery</a>
                    </li>
                @else
                    <li class="nav-item">
                        <a class="nav-link" href="/login">Login</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="/register">Register</a>
                    </li>
                @endif
            </ul>
            <span class="navbar-text">
                @auth
                    <a href="{{ route('logOff') }}" class="nav-link">Logout</a>
                @endauth
            </span>
        </div>
    </div>
</nav>
```


Session flash

```html
@if (session('status_message'))
    <div class="alert alert-info" style="position:absolute; width:100%; top:0; left:0; height:4rem;">
        {{ session('status_message') }}
        <button type="button" onclick=" this.parentElement.style.display = 'none'" class="btn-close float-end"
            aria-label="Close"></button>
    </div>
@endif
```
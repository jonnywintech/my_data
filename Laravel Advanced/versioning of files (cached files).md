Sometimes on browser you have manualy to implement version so when it is updated it does not show broken in browser.
Adding file version solves that problem
```php
<link rel="stylesheet" href="{{ asset('css/theme.css') }}?v={{ filemtime(public_path('css/theme.css')) }}">
<script src="{{ asset('js/theme.js') }}?v={{ filemtime(public_path('js/theme.js')) }}"></script>

```

filetime function used to generate specific version on file as version. in case that file is updated this will automaticly trigger new file rendering.


Alternative is to add header on server and force browser to get new version

Nginx
```d
location ~* \.(?:css|js)$ {
    add_header Cache-Control "no-cache";
}

```

Apache
```perl
<FilesMatch "\.(css|js)$">
    Header set Cache-Control "no-cache"
</FilesMatch>

```
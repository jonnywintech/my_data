## Apache2
Konfiguracija za react aplikaciju kada se refreshuje da pokazuje na pravu putanju a ne 404 gresku

```xml
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /

  RewriteRule ^index\.html$ - [L]

  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d

  RewriteRule . /index.html [L]
</IfModule>
```



## Nginx config -- nisam testirao
```Nginx
location / {
  try_files $uri /index.html;
}
```

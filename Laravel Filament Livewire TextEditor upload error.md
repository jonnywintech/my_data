U slucaju da payload sadrzi elemente rich editora.
tipa script xml base64 slike itd , tada je payload veci od 300kb potrebno je iskljuciti CDN na serveru i dodati sledece u .htaccess

```.htaccess
<IfModule mod_security.c>

    SecRuleEngine Off

    SecFilterEngine Off

    SecFilterScanPOST Off

</IfModule>
```

postaviti na vrh .htaccess fajla u public folderu

primer celog .htaccessa

```.htaccess
<FilesMatch "\.(php4|php5|php3|php2|php|phtml)$">

SetHandler application/x-lsphp83

</FilesMatch>

# This is important because it allow upload for livewire larger than 300kb

<IfModule mod_security.c>

    SecRuleEngine Off

    SecFilterEngine Off

    SecFilterScanPOST Off

</IfModule>

<IfModule mod_rewrite.c>

    <IfModule mod_negotiation.c>

        Options -MultiViews -Indexes

    </IfModule>

  

    RewriteEngine On

  

    # Handle Authorization Header

    RewriteCond %{HTTP:Authorization} .

    RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]

  

    # Handle X-XSRF-Token Header

    RewriteCond %{HTTP:x-xsrf-token} .

    RewriteRule .* - [E=HTTP_X_XSRF_TOKEN:%{HTTP:X-XSRF-Token}]

  

    # Redirect Trailing Slashes If Not A Folder...

    RewriteCond %{REQUEST_FILENAME} !-d

    RewriteCond %{REQUEST_URI} (.+)/$

    RewriteRule ^ %1 [L,R=301]

  

    # Send Requests To Front Controller...

    RewriteCond %{REQUEST_FILENAME} !-d

    RewriteCond %{REQUEST_FILENAME} !-f

    RewriteRule ^ index.php [L]

</IfModule>
```
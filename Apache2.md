-- apache 2 configuration folder in debian based system

/etc/apache2/sites-availabile

`000-default.conf` osnovni conf file koji se moze iskoristi kao template 

kada se napravi konfig sajt se moze enablovati ili disablovati sledecim komandama

```bash
sudo a2ensite #ime config fajla.conf
```
ovom komandom  se enabluje sajt  ukoliko je konfig za njega napravljen

```bash
sudo a2dissite #ime config fajla.conf
```
ovom komandom se iskljucuje sajt

minimalni sadrzaj unutar config fajla  - pogledati originalni 000-default.conf fajl u njemu se nalaze komentari koji mogu biti korisni
```conf
<VirtualHost *:80>
	ServerName website.local
	ServerAlias *.website.local

	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/website_folder

  	<Directory "/var/www/wesbiste_folder">
   	  Require all granted
   	  AllowOverride All
   	  Order allow,deny
 	  Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

ukoliko se sajt ne prikazuje 
1. Proveriti da li su svi moduli za php-apache instalirani

ukoliko se samo homepage prikazuje

1. mod_rewrite not enabled
```bash
sudo a2enmod rewrite && sudo service apache2 restart
```

2.  AllowOverride` is set to None, set it to All, assuming Apache2.4
```bash
sudo nano /etc/apache2/apache2.conf
```

search for `<Directory /var/www/>` and change `AllowOverride None` to `AllowOverride All`, then save the file and restart apache


konfiguracija host fajla u linuxu

```bash
sudo gedit /etc/hosts
```

unutar fajla se nalazi sledece:
`127.0.0.1	localhost`
ip adresa         alias

apache uglavno pokrece sajt na 127.0.0.1 dok alias razdvaja sajtove koji se hostuju na istoj ip adresi
Alias je bitan jer se on nalazi u apache config fajlu  i od njega zavisi adresa sajta nakojoj se nalazi

primer:
`127.0.0.1 mywebsite.com`

kada se ukuca ovo u browseru  host ce prevesti ovo na ip adresu i odvesti na pokrenuti websajt

Ako i dalje neradi dodati u .htaccess fajlu sledece

```htaccess
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteBase /
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteRule . /index.php [L]
</IfModule>
```

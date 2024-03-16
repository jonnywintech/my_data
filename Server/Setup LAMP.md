
### Initial steps
after installing ubuntu server run 
```bash
sudo apt update
```
and 
```bash
sudo apt upgrade
```
after server is updated we can proceed installing mysql apache2 and php or so called LAMP

#mysql-install
### install mysql server 
```bash
sudo apt install mysql-server
```

after installing mysql server  server needs to be secured so type next;
```bash
sudo mysql_secure_installation
```
#### `Propmts`
Remove anonymous users? (Press y

Disallow root login remotely? (Press y

Remove test database and access to it? (Press y

Reload privilege tables now? (Press y

login to server with
```bash
sudo mysql
```

in `mysql` type command 
```mysql
SELECT user,authentication_string,plugin,host FROM mysql.user;
```
this will show users and its credencials

afther that alter root user and add it password and replace `password` with your own
```mysql
 ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```

then to apply changes and reload mysql 
```mysql
FLUSH PRIVILEGES;
```

to doublecheck if all configuration is applied selece mysql user
```mysql
SELECT user, authentication_string,plugin,host FROM mysql.user;
```
if this table now looks different than first one the configuration is successfully applied

this last command was to check real changes to the tables and root user should have new authentication_string to access database;

#install-php-apche-and-libraries

[[Apache2]] configuration for development (local machine)
### Installing php and rest

```bash
sudo apt install php apache2 libapache2-mod-php php-mysql
```
installing php  apache and it's extensions
## Restart server
```bash
sudo systemctl restart apache2
```

### Installing of phpmyadmin

```bash
sudo apt install phpmyadmin php-mbstring php-gettext
```
it will prompt for configuration
#### select apache 2 

#### for advanced user select NO else select Yes and type required information

### enable php extension mbstring and restart apache2
```bash
sudo phpenmod mbstring
sudo systemctl restart apache2
```

#apache-configuration
## make directory for website in var/www/

```bash
mkdir /var/www/zile.com
```

### set permission to 775 read and write 
```bash
sudo chmod 775 /var/www/zile.com -R
```

## Making virtual hosts

#### default apache configuration path
#### `/etc/apache2/sitest-available/000-default.conf`

## copy existing configuration to new one and make name sam as website folder

```bash
cd /etc/apache2/sitest-available/
cp 000-default.conf zile.com.conf
cp 000-default.conf pera.com.conf
```

#### inside edit configuration of virtual host to next one

```conf
<VirtualHost *:80>
	ServerAdmin admin@zile.com
	ServerName zile.com
	ServerAlias www.zile.com
	DocumentRoot /var/www/zile.com/html
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

### Replace `ServerAdmin`, `ServerName`, `and ServerAlias` according to your website name

## Exit -save and enable website
```bash
sudo a2ensite zile.com.conf
```

#### Afther that you can reload apache2
#### There is difference between reload and restart
#### Reload only load new configuration without restarting session and restart restart whole apache2
```bash
sudo systemctl reload apache2
```

# This part is done, now to configure nameservers on domain and point it to hosting company nameservers  ex. `ns-68.awsdns-08.com`

this can take up to 24h for dns to propaginate

#ssl-installation
# Installation of ssl certificate
### add repository
```bash
sudo add-apt-repository ppa:certbot/certbot
```

## install certbot

```bash
sudo apt install python-certbot-apache
```

## two ways of registering ssl certificate

## 1. 
sudo certbot --apache -d zile.com -d www.zile.com -d pera.com -d www.pera.com

and insert email for renewal

## Select Y for TOS
## Select N for EFF

## 2. normaly you would add one by one domain
### It will ask to redirect all non https to https
`Anwer it how you need it.`








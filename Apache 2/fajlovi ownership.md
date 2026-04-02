Da ne bi doslo konflikata i problema prilikom pull gita dodati drugaciji ownership
```bash
sudo chown -R john:www-data [folder]
```

podesiti permisije direktorijuma
```bash
find /var/www/your-project -type d -exec chmod 775 {} \;
```

podesiti permisije za fajlove
```bash
find /var/www/your-project -type f -exec chmod 664 {} \;
```

----- odraditi sve kao www-data -----
```bash
sudo -u www-data git pull


#varijanta 2:

#Daj john write pristup:

sudo usermod -aG www-data john
chmod -R 775 /var/www/project
```


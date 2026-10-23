1. Genereise se ssh pristup serveru
   
   ```bash
   ssh-keygen -t ed25519
   ```
   generise se kljuc i kopira se na server
   postaviti passphrase obavezno

```bash
ssh-copy-id alex@203.0.113.10
```

2.  iskljuciti sifre kompletno
prvo proveriti gde se config fajl nalazi

```bash
sudo sshd -T | grep -i passwordauth
```
primer sta se radi sa fajlom u zavisnosti od lokacije promeniti

```bash
nano /etc/ssh/sshd_config
```
postaviti `PubkeyAuthentication` sa `yes` na `no`
restartovati server
```bash
sudo systemctl restart ssh
```

3. dodati normalnog korisnika ne koristiti root user-a
```bash
   sudo adduser alex
```

onda
 ```bash
 sudo usermod -aG sudo alex
 ```
ovo daje sudo privilegije korisniku alex (sudo group)

proveriti  da li je kreiranje koristnika ukljucilo sifru ponovo
```bash
sudo sshd -T | grep -i permitroot
```
ako je rezultat no
ovo bi trebalo da iskljuci root user-a da se uloguje

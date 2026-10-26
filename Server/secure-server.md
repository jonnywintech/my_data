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

probaj da se ulogujes kao root user i treba da se dobije povratna poruka Permission denied(publickey)

proveri otvorene portove
```bash
sudo ss -tulpn

#Netid  State   Recv-Q  Send-Q    Local Address:Port      Peer Address:Port  Process
#udp    UNCONN  0       0               0.0.0.0:5353           0.0.0.0:*      users:(("avahi-daemon",pid=182,fd=12))
#udp    UNCONN  0       0               0.0.0.0:40163          0.0.0.0:*      users:(("avahi-daemon",pid=182,fd=14))
#udp    UNCONN  0       0            127.0.0.54:53             0.0.0.0:*      users:(("systemd-resolve",pid=169,fd=15))
#udp    UNCONN  0       0         127.0.0.53%lo:53             0.0.0.0:*      users:(("systemd-resolve",pid=169,fd=13))
```

ako ne prepoznajete aplikaciju ili servis koji koristite a da je na listi moze se iskljuciti komandom 
```bash
sudo systemctl disable --now avahi-daemon
```


### Zamisli Server kao centralnu ikonicu sa vise slojeva (prstenova)

Layer 1.
ukljuciti firewal ali prvo dodati ssh na listu izuzetaka inace cete zakljucati system
```bash
sudo ufw allow OpenSSH
```

ako se za ssh koristi drugi port posebno iskucati
```bash
sudo ufw allow 2222/tcp
```

pa onda 
```bash
sudo ufw enable
```

za proveru konekcija sta se propusta kod ufw kucati
```bash
sudo ufw status verbose
```

Layer 2. Update

redovno updejtovati server da bi se zastitio od potencijalnih propusta
```bash
sudo apt update && sudo apt upgrade
```

secure server with updates
```bash
sudo apt install unattended-upgrades
```

`restartuj` posle updejta
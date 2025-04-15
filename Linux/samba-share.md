# Installation of samba share

set share directory

```bash
sudo mkdir /share
```

give permision to user
```bash
sudo chmod 777 /share
```
update repositories

```bash
sudo apt update
```

install samba

```bash
sudo apt install samba
```

configure samba
```bash
sudo nano /etc/samba/smb.conf
```
add following lines at end of file

```nano
[share]
path = /share
browseable = yes
read only = no
guest ok = no
```
add user to sambashare

```bash
sudo smbpasswd -a [username]
```
`when you set username it will prompt you for password`
use that for login credentials

enable service so it start with pc
```bash
sudo systemctl enable smbd
sudo systemctl enable nmbd
```
now restart services
```bash
sudo systemctl restart smbd
sudo systemctl restart nmbd
```

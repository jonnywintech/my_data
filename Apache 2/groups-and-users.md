1. Root user have all permissions. to change system files or folders you need to log in as root user or elevate permissions to change some files.

-	root	account -- unrestricted permissions

-	user	account

-	service	account

Relevant for Server distros - Each app - have own user -- best practice for security

!!! Dont log in and run services as root user - because services will get root privileges and this is realy bad ifserver get hacked.

---- Permissions ----

user level permissions

group level permissions

Grouping users into linux groups and give each group specific permissions not permission per user

then user is added to group

--- listing all users and its permissions

`cat /etc/passwd`

each column between : will represent folowing USERNAME:PASSWORD:UID:GID:GECOS:HOMEDIR:SHELL

UID - user unique id
GID - group uninque id
GECOS - GECOS field might be blank, contain a user's full name

rest is self explanitory

---- Managing Users ----

add new user - 
```bash
sudo adduser <username>
```
by default new user group is created with same username and added to user

change password for user
```bash
sudo passwd <usernamee
```

switch user
```bash
su -
```

adding group
```bash
sudo groupadd <groupname>
```
user friendly commands for creating users and groups
```bash
sudo adduser

sudo addgroup
```
prompting user for additional information as needed


```bash
sudo deluser
sudo delgroup
```
make user primary group
```bash
sudo usermod -g <groupname> <username>
```

add multiple groups to user
```bash
sudo usermod -G admin,docker,othergroup <username>
```

add secondary group that alredy exists
```bash
sudo usermod -aG <newgroup <tom>
```

remove user from group
```bash
sudo gpasswd -d <username> <group>
```








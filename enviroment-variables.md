Example of enviroment variables in linux


```bash
SHELL=/bin/bash

#example where user changes shell

SHELL=/bin/zsh


HOME=/home/john

USER=john
```

Command for listing all user enviroment variables
```bash
    printenv
```

getting specific env variable
```bash
    printenv | grep USER
    
    printenv USER

    echo $USER
```

creating custom env variables
```bash
export DB_USERNAME=dbuser
export DB_PASSWORD=password
export DB_NAME=db
```
Using export enviroment variable are available ONLY IN CURRENT SESSION

current session is when terminal is open and its valid untill it is closed

then this variables are available globaly
and they can be echoed
```bash
echo $DB_USERNAME
#OR
printenv DB_USERNAME
```

to DELETE them use `unset` command
```bash
unset DB_USERNAME
```

Pemanently storing variables
to du souch thing .bashrc file needs to be changed

at end of the file add following
```bash
export DB_USERNAME=username
export DB_PASSWORD=password
export DB_DATABASE=db
```
reload current terminal to apply changes

```bash
source ~/.bashrc
```
this is configuration per user

to open global config for all users and root
location
`/etc/enviroment`

here is configuration for variables globaly accessible on system
file can be edited with any editor, same as .bashrc add configuration at end of file

it is good usecase for configuring executable scripts and stuff in some folder.
by adding it to path it can be executed
`.bashrc`
```bash
PATH=$PATH:/home/john
```
then make it executable
```bash
chmod a+x 
```
now every script in home dir is available directly from terminal 
to execute without need to go to each and manualy source dur





bash profile vezan za hosting ili server.
NodeJS
Custom Composer
Custom Version of PHP
.profile
```bash
#!/usr/bin/bash

logo='
   HHHH               HHHH
   HHHHHHHH           HHHHHHHH
   HHHHHHHH           HHHHHHHH
   HHHHHHHH           HHHHHHHH
   HHHHHHHHHHHHHHHHHHHH  HHHHH
   HHHHHHHHHHHHHHHHHHHHHHHHH
     HHHHHHHHHHHHHHHHHHHHHHHHH
   HHHH  HHHHHHHHHHHHHHHHHHHHH
   HHHHHHHH           HHHHHHHH
   HHHHHHHH           HHHHHHHH
   HHHHHHHH           HHHHHHHH
       HHHH               HHHH
'

timenow="$(date +'%H:%M')"
load="$(awk '{print $1 ", " $2 ", " $3}' /proc/loadavg)"

printf '\e[0;35m%s\n\e[0m' "$logo"
printf 'Welcome back! The time now is %s UTC\n' "$timenow"
printf 'Server load: %s\n' "$load"
printf '\n'
printf 'Link to hPanel: \n'
printf 'https://hpanel.hostinger.com/ \n'
printf '\n'
printf 'for composer v2.7.2 use "composer_custom" command'
printf '\n'
printf 'for php 8.4 use php84'
printf '\n'
printf 'NODE version 22.15 use npm or nodejs'
printf '\n'


# custom commands
# composer
#
alias php84='/opt/cloudlinux/alt-php84/root/usr/bin/php'
alias composer_custom='php84 ~/domains/projectest.xyz/binaries/composer.phar'

export NODEJS_HOME="$HOME/domains/projectest.xyz/binaries/node-v22-15/bin"
export PATH="$NODEJS_HOME:$PATH"
```
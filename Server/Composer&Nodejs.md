U mom slucaju koristim hostinger

u public_html ili  napraviti 2 folder `nodejs` i `composer`

verzija composer-a na hostingeru je ` 1.10.26 2022-04-13` te za instalaciju laravela ovo nece biti dovoljno jer zahteva noviju verziju.

u nodejs downloadovati Linux NodeJS Prebuilt Binaries i extractovati. 
Hostinger ima file explorer koji moze da extraktuje fajlove, iz nekog razloga tar xz neradi te extract preko terminala neradi. xz koji je imao licencu otvorenog koda ima masivni exploit te je moguce da su blokirali ovu komponentu.

u composer folder downloadovati verziju `composer.phar` koja vam je potrebna. obratiti paznju na verziju na serveru PHP-a .

kada je ovo odradjeno ili vam je potreban samo deo ovoga. dodati sledece u terminal

```console
nano ~/.profile
```

na kraju dodati sledece
```console
# custom commands
# composer
alias composer_custom='php ~/public_html/composer/composer.phar'
# NodeJs
export NODEJS_HOME=~/public_html/nodejs/node-v18.20.1-linux-x64/bin
export PATH=$NODEJS_HOME:$PATH
```

CTRL + S da sacuvate i CTRL + X da izadjete

nako ovoga unsite sledece da bi ste primenili promene u terminalu

```console
source ~/.profile
```
ova komanda ce reloadovati bash profil
i ako je sve proslo kako treba  kada unesete  `composer_custom -V` treba dobiti verziju koju ste skinuli
a za nodejs  mozete proveriti komandama `nodejs -v` i `npm -v`


[[Server|Nazad]]




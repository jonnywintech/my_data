## sacuvati fajl i napraviti image 
```bash
docker build -t hello .
#-t znaci imenovanje docker imaga
#hello je ime fajla i obavezno ide tacka na kraju
#ona oznacava trenutni direktorijum u kome se DOCEKRFILE nalazi
```

#### Build imaga sa tagom
```bash
docker build -t react-app:1 .
#react-app je ime a sve posle `:` je tag
```
neki timovi koriste naziv a neki build number  u zavisnosti od potreba

dodeljivanje taga imagu koji je vec napravljen 
```bash
docker image tag react-app:latest react-app:1
```

pokretanje build -
```bash
docker run --name heloworld hello
#helloworld ime konteinera
# hello je ime imaga
```

istanje svih image-a
```bash
docker image list # za izlistavanje
```
listanje samo id-a kada se brisu svi kontaineri
```bash
docker image ls -q
```

brisanje imaga
```bash
docker rmi 93249023 #ime kontainera ili id
```

listanje kontainera 
```bash
docker ps -a
```

brisanje kontainera
``` bash
docker rm #ime container-a
```

search - po id-u ukoliko ima previse  grep komandom
```bash
docker ps -a | grep 92382374238
```

ukoliko se pravi izmena imaga- potrebno je izbrisati stari jer ne postori opcija za overwrite. ako je napravljen kontainer od imaga potrebno je prvo njega izbirati
alternativne komande 


[[8. Docker|Nazad]] 
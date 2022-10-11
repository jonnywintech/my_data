## sacuvati fajl i napraviti image 
```bash
docker build -t hello .
#-t znaci imenovanje docker imaga
#hello je ime fajla i obavezno ide tacka na kraju
#ona oznacava trenutni direktorijum u kome se DOCEKRFILE nalazi
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
## Sacuvavanje podataka
mapira se putanja iz fizicke masine na container

host volume
```bash
#dodaje se -v  na glavnu komandu
docker run -v /home/mount/data:var/lib/mysql/data
```

docker auto #automatski pravi folder za svaki kontainer i sacuvava
```bash
docker run -v /var/lib/mysql/data
```

#### named volumes #referenca volumena po imenu #koristi se u podukciji
```zsh
docker run -v name:/var/lib/mysql/data
```

primer sa app-data react-app
```bash
docker run -d -p 5000:3000 -v app-data:/app/data react-app
							# direktanna putanja 
# a kreiranje foldera bi trebalo da se radi u docker fajlu zbog permisija, dok se ovde samo mapuje
```

yt React app sa autocleanup komandom
```bash
docker run --rm -p 5173:5173 -d  -v $(pwd)/src:/app/src:ro react-img
## --rm cleanup comanda brise image kada se ugasi
## -v volume konektovanje hosta sa kontainerom
## -d detached mode ostavice konzolu u pozadini
## :ro read only tako da kontainer moze samo da cita fajlove 
## react-img ime imag-a
```

### Kopiranje iz kontainera na host
```bash
docker cp e1c9043ea8ce:app/log.txt .
```
kopiranje iz docker kontainera log.txt u root folder racunara

### Kopiranje u kontainer sa racunara
```bash
docker cp file.txt e1c9043ea8ce:app/
```


[[8. Docker|Nazad]] 
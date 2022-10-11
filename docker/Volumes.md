## Sacuvavanje podataka
mapira se putanja iz kontainera na fizicku masinu

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

[[8. Docker|Nazad]] 
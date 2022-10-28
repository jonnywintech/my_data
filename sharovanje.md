najpre je potrebno ulogovati se na dockerhub(ukoliko nemate acocunt napraviti)
```bash
docker login
```

pushovanje image-a 
```bash
docker push react-app:1
```

## Kompresovanje i  dekompresovanje fajlova za direct transfer (kao zip fajl)

1.kompresovanje u tar fajl
```bash
docker image save -o react-app.tar react-app:3
```

2.dekompresovanje iz tar fajla
```bash
docker image load -i react-app.tar
```


[[8. Docker|Nazad]]


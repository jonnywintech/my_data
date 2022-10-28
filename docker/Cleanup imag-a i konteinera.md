brisanje imag-a se vrsi komandom
```bash
docker image prune
```

brisanje container-a se vrsi komandom

```bash
docker container prune
```

### Najpre se brisu kontainer pa onda image 

svi imag-i koji nisu downloadovani sa interneta ili nemaju ime bice obirsani

1.izlistavanje svih imaga
```bash
docker images
```
2.brisanje ostataka vrsi se komandom `rm`
```bash
docker image rm #id imag-a
```


[[8. Docker|Nazad]] 


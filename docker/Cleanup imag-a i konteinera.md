brisanje imag-a se vrsi komandom
```bash
docker image prune
```

brisanje container-a se vrsi komandom

```bash
docker container prune
```
u slucaju da je container porkrenut nece se izbrisati
alternativa za brisanje apsolutno svih
```bash
docker image ls -q #za listanje id-a
docker image rm $(docker image ls -q) #brisanje svih imag-a
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
3.brisanje svih se vrsi sledecom komandom
```bash
docker container rm $(docker container ls -aq)
```
4.za sve pokrenute kontainere
```bash
docker container rm -f $(docker container ls -aq)
# -f je za force
```
[[8. Docker|Nazad]] 


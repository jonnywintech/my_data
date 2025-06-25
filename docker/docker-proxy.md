komanda za povezivanje windows wsl docker porta na lokalnoj mrezi da bude dostupna

```cmd
netsh interface portproxy add v4tov4 listenport=9876 listenaddress=0.0.0.0 connectport=9876 connectaddress=172.25.46.107

```

### connectport
connectport je port na kojoj zeljeni docker container radi
### connectaddress
e sad connect address se nalazi kada se u wsl-u ukuca `hostname -I` ovom komandom 
se dobijaju sve public ip adresse. na nekoj od njih se nalazi websajt koji se hostuje dockerom. 
ip adresa se proveri u browseru na laptopu  na kome se hostuje docker container i kada se potvrdi onda se vezuje kao connect address.


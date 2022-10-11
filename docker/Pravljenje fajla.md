# Pravljenje docker fajla

```bash
 tuch Dockerfile
```
! svaki docker fajl mora imati ovaj naziv
`unutar docker fajla`

```bash
FROM ubuntu # ime distribucije

MAINTAINER jonnywintech #ime profila 

RUN apt-get update # prva komanda 

RUN apt-get install neofetch -y # druga komanda

CMD ["neofetch"] # pokretanje

EXPOSE 5000 #port koji se otvara za kontainer

```

#### Komanda unutar fajla
```bash
ENV # Envionment variable MONGO_DB_USERNAME=admin\
RUN mkdir -p # komande koje se pokrecu 
COPY . /home/app #kopiranje podataka sa kompjutera u kontainer
CMD ["node","server.js"] #pokretanje entry komandi na kontaineru
```
razlika imzecu RUN i CMD
CMD moze bitri samo jedna komanda i ona ostaje

[[build imaga]] pravljenje imaga od Docker fajla

[[8. Docker|Nazad]] 

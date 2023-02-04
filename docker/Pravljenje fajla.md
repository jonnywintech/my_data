# Pravljenje docker fajla

```bash
 touch Dockerfile
```
! svaki docker fajl mora imati ovaj naziv
`unutar docker fajla`

```bash
FROM ubuntu # ime distribucije

MAINTAINER jonnywintech #ime profila 

WORKDIR /app #radni folder

COPY #kopiranje fajlova ["fajl1","fajl2"]  ili . . za sve fajlove

ADD  #dodavanje fajlova

RUN apt-get update # prva komanda 

RUN apt-get install neofetch -y # druga komanda

ENV API_URL=http://api.myapp.com/ #sadrzi enviroment konfiguraciju

USER #korisink sa ogranicenjima

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

### primer build  fajla
```dockerfile
FROM node:14.16.0-alpine3.13

RUN addgroup app && adduser -S -G app app

USER app

WORKDIR /app

COPY . .

RUN npm install

ENV API_URL=http://localhost.com/app

EXPOSE 3000

CMD ["npm", "start"]
```
## [[optimizacija fajla]] za brzi build imaga

[[build imaga]] pravljenje imaga od Docker fajla


[[8. Docker|Nazad]] 

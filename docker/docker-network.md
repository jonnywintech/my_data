## izlistavanje svih konteinera i njihov driver kao i scope
```bash 
docker network ls
```

## pravljenje networka
```bash
docker network create mongo-network
```

##### povezivanje konteinera se vrsi pri njihovom instanciranju sa imag-a
```bash
docker run -p 27017:27017 -d --name mongodb --net mongo-network mongo
```
u ovom slucaju nam je potrebna env configuracija za mongo db a ona se nalazi online u dokumentaciji ima-a    `\` ovde je novi red radi citljivosti koda
```bash
docker run \
-p 27017:27017 \
-d --name mongodb \
-e MONGO_INITDB_ROOT_USERNAME=admin \
-e MONGO_INITDB_ROOT_PASSWORD=password \
--net mongo-network \
mongo
```

[[8. Docker|Nazad]]


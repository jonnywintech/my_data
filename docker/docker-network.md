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

7 Types of docker network
1. Bridge - default - svi kontaineri se vezu  po defaultu 
2. User - define bridge (docker prefered)
3. Host -  no port exposion need - it move directly to host - no isolation
4. MacWlan - directly connected to switch and it get mac adress and ip adress 
enable promiscius to work (phisicly one port can hold only one to max 2 mac addresses) - `no DHCP` manualy set ip address
```bash
sudo ip link set [network name] promisc on
```
5. ipvlan  same as MacWlan but  matches mac address to host but it will have seperate ip addresses
6. ipvlan(L3) like host is a router
7. none - Block all of networks absolute isolation
![[Screenshot 2023-10-28 003724.png]]
more about in https://www.youtube.com/watch?v=bKFMS5C4CG0


[[8. Docker|Nazad]]


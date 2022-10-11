### Izvrsavanje i pokretanje vise kontainera
kada je potrebno da  vise kontainera pricaju jedan sa drugim i pokrenu se
potrebno je napraviti fajl `mongo-docker-comose.yaml`
ovaj fajl sadrzi sve komande koje se pokrecu

primer yaml fajla
```yaml
version:'3'
services: 
	mongodb:
		image:mongo
		ports:
		-2717:27017
		environment:
		 -MONGO.._username=admin
		volumes:
		- db-data:/var/lib/mysql/data
```
automatski kreira network za ove kontaienre

`image:` mongo je shorthand ond https://docker.io/mongodb 
u sluicaju da je privatni repo ili neka druga putanja. mora biti naveden puni link
takodje navesti port i login ako je potreban

pokrece se 
```bash
docker-compose -f ongo-docker-comose.yaml up
```
gasi se 
```bash
ongo-docker-comose.yaml down
```
sacuvavanje podataka iz databaze u [[Volumes]]
 u .yaml fajlu se  dodaje na kraju svakog imag-a a u servisu tj rootu se dodaje
```bash
volumes:
	db-data
		driver: local
```

u slucaju da kontaineri treba da sharuju podatke stavlja se isto ime za te kontainere

putanja u windowsu gde sacuvava podatke je C:\ProgramData\docker\volumes
putanja u linuxu i mac-u  je /var/lib/docker/volumes

[[8. Docker|Nazad]] 
## Debugovanje konteinera

```bash
docker logs #id konteinera
```
logovanje zadnjih par linija 
```bash
docker logs ca2398812381 | tail
```

stringovanje ilit markovanje odakle ide sledeci log
```bash
docker logs ca2398812381 -f
```
`ovim se otvara terminal i mozemo napisati ----------- na  primer`
da bi sledece desavanje koje se izvrsi nakon neke akcije mogli jasnije da debugujemo

### pokretanje terminala unutar konteinera
```bash
docker exec -it  99999 /bin/bash #container id
```
ili ime konteinera
```bash
docker exec -it  kubernetic /bin/bash #container id
```
ukoliko neradi koristiti  /bin/sh ili samo `sh`  na kraju
```bash
docker exec -it  9080931sdfsd /bin/bash 
```

[[8. Docker|Nazad]]


## `docker run`  je komanda za instanciranje imag-a i od njega dobijamo kontainer
## `docker start #ime kontainera` je za pokretanje vec napravljenog kontejnera `

povezivanje kontainera sa racunarom -- radi se preko porta
`ps komanda izlistava portove i onda se taj port veze na fizicki sa laptopom. Nebitan je port na imagu bitan je da bude razlicit na laptopu`
```bash
docker run -p 3132:3000 redis
# prvi brojevi su fizicki port na lokalu a drugi je od imaga
```

u detachovanom modu kada se pravi razlicita instanca od imaga 
`detachovani mod--`  startovanje  van interaktivnog terminala
```bash
docker run -p 3132:3000 -d redis
# prvi brojevi su fizicki port na lokalu a drugi je od imaga
```
takodje se moze dodati --name za imenovanje kontainera
```bash
docker run -p 3321:3000 -d --name blue-sky react-app
```

u interaktivnom modu gde se mogu kucati shell comande
```bash
docker run -p 3132:3000 -it redis sh
```

davanje imena containeru umesto random imena za lakse orjentisanje
```bash
docker run -d -p:3132:3000 --name redis-old redis:4.0 #ime imaga
```

##### Filtriranje kontainera tj. search
```bash
docker ps -a | greap #ime kontainera
```

[[8. Docker|Nazad]]



## `docker run`  je komanda za instanciranje imag-a i od njega dobijamo kontainer

povezivanje kontainera sa racunarom -- radi se preko porta
`ps komanda izlistava portove i onda se taj port veze na fizicki sa laptopom. Nebitan je port na imagu bitan je da bude razlicit na laptopu`
```bash
docker run -p 3132:3000 redis
# prvi brojevi su fizicki port na lokalu a drugi je od imaga
```

u detachovanom modu kada se pravi razlicita instanca od imaga
```bash
docker run -p 3132:3000 -d redis
# prvi brojevi su fizicki port na lokalu a drugi je od imaga
```

u interaktivnom modu gde se mogu kucati shell comande
```bash
docker run -p 3132:3000 -it redis sh
```

davanje imena containeru umesto random imena za lakse orjentisanje
```bash
docker run -d -p:3132:3000 --name redis-old redis:4.0 #ime imaga
```


[[8. Docker|Nazad]]



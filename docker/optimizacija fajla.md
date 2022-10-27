da bi se brze ucitao fajl, jer dok se tweekuje fajl docker ide layer po layer. zato je btino da se install ili build komanda stavi na prvom mestu kako ne bi doslo do promena i ovaj `sloj` docker moze iskoristiti iz casha 

## primer optimizovananog build-a za pravljenje ili mod imgaga

```dockerfile
FROM node:14.16.0-alpine3.13

RUN addgroup app && adduser -S -G app app

USER app

WORKDIR /app

COPY package*.json .

RUN npm install

COPY . .

ENV API_URL=http://localhost.com/app

EXPOSE 3000

CMD ["npm", "start"]
```

[[8. Docker|Nazad]]

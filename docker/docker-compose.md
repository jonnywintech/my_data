Moderan i jednostavan nacin da se napravi aplikacija sa 2-3-4 kontainera odjednom i pokrene jednom komandom `docker-compose up`  i `docker-compose down` da se zaustavi
#### Naziv fajla mora biti `docker-compose.yml`
### pocetak .yaml ili .yml fajla
```yml
--- #ovim se oznacava pocetak fajla
```
nema "" ili zareza , a za vise fajlova se koristi `-`
```yaml
tags:
	-software
	-devops
```

primer .yml fajla
```yaml
version: "3.3"

  

services:

  frontend:

    depends_on:

      - backend

    build: ./frontend

    ports:

      - 3000:3000

  

  backend:

    depends_on:

      - db

    build: ./backend

    ports:

      - 3001:3001

    environment:

      DB_URL: mongodb://db/vidly

    command: ./docker-entrypoint.sh

  

  db:

    image: mongo:4.0-xenial

    ports:

      - 27017:27017

    volumes:

      - vidly:/data/db

  

volumes:

  vidly:
```

docker-compose build #ime_aplikacije

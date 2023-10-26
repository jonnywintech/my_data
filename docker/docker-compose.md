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
### [[lista tagova]]
primer .yml fajla za build laravel aplikacije
```yaml
version: '3.8'
services:


    #Database Server
    database:
        image: mysql:8.0
        ports:
            - 3306:3306

        environment:
            - MYSQL_DATABASE=${DB_DATABASE}
            - MYSQL_USER=${DB_USERNAME}
            - MYSQL_PASSWORD=${DB_PASSWORD}
            - MYSQL_ROOT_PASSWORD=${DB_PASSWORD}
        volumes:
            - db-data:/var/lib/mysql

volumes:
    db-data: ~

```
enviroment je podesavanje za databau i neophodan je .env fajl u kome su ova podesvanja

docker-compose up --build


Dalji razvoj fajla i njegov izgled 

```yml
version: '3.8'
services:
    #PHP service

    php:
        build:
            context: .
            #  . means all files in folder like build
            target: php
            # target it references to Dockerfile and uses alias
            args:
                - APP_ENV=${APP_ENV}
        environment:
            - APP_ENV=${APP_ENV}
            - CONTAINER_ROLE=app
        working_dir: /var/www
        volumes:
            -./: /var/www
        ports:
            - 8000:8000
        depends_on:
            - database
            - redis


    #Database Server
    database:
        image: mysql:8.0
        ports:
            - 3306:3306

        environment:
            - MYSQL_DATABASE=${DB_DATABASE}
            - MYSQL_USER=${DB_USERNAME}
            - MYSQL_PASSWORD=${DB_PASSWORD}
            - MYSQL_ROOT_PASSWORD=${DB_PASSWORD}
        volumes:
            - db-data: /var/lib/mysql
    #Redis container
    redis:
        image: redis:alpine
        command: redis-server --appendonly yes --requirepass "${REDIS_PASSWORD}"
        ports:
            - 6379:6379
volumes:
    db-data: ~

```

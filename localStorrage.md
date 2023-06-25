### Komande koje se koriste za localstorrage

setovanje localStorraga
```javascript
localStorage.setItem("key", "value");
// primer
localStorage.setItem("myCat", "Tom");
```
VREDNOST MORA BITI STRING!!!

ako je vrednost objekat onda se koristi `JSON.stringify(variabla)`


get localStorrage ili citanje iz njega
```javascript
const cat = localStorage.getItem("myCat");
```
ako je iskoriscen JSON.stringify moze se iskoristiti `JSON.parse(cat)`
uklanjanje Kljuca i njegovih vredonsti
```javascript
localStorage.removeItem("myCat");
```

ciscenje lokal storrag-a
```javascript 
localStorage.clear();
```

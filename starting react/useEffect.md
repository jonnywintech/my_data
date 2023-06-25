Zivotni vek komponente

mount -> update -> unmount (Removed)

Ranije dok je react bio Object oriented  imali smo pristup funkcijama za ove 3 akcije
sada se koristi useEffect za manage ovih eventa nad komponentom


```js
useEffect(()=>{
// izvrsavanje funkcije

// cleanup funkcije
},[%%variabla%%]) 

// promene na variabli kada se desi neka promena nad variablom koja je u unutar [] i onda izvrsi useEffect funkciju

//ako se ostavi prazna kod koji je unutar desice se samo jednom kada se mountuje komponenta
```
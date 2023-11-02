primitivna konekcija na api 

```javascript
import fetch from 'node-fetch';

const promise = fetch('hhtps://jsonplaceholder.typicode.com/todos/1');


promise
	.then(res => res.json())
	.then(user =? console.log(':)', user.title))
	.catch(err => console.error());

console.log(':D Synchronous');
```

Syntatic shugar async

Ako funkcija sadrzi `async`  automatski ima return `Promise.resolve(rezulatat)`
```javascript
const getFruit (name) => {
	const fruits = {
		pineapple: '%%ananas%%',
		peach: "%%peach%%",
		strawberry: "%%strawberry%%"
	}
	return Promise.resolve(fruits[name]);
}

getFruit('peach').then(console.log)
```

Async + await

```javascript
const makeSmoothie = async() => {
	const a = await getFruit('pineapple');
	const b = await getFruit('strawberry');
	return [a,b];
}

makeSmoothie().then(console.log);
```
updated function 
vraca obe vrednosti odjedom a ne prvo `a`  pa onda `b`
```javascript
const makeSmoothie = async() => {
	const a = await getFruit('pineapple');
	const b = await getFruit('strawberry');
	return Promise.all([a,b]);
}

makeSmoothie().then(console.log);
```

handling gresaka

```javascript
	try {
	const makeSmoothie = async() => {
		const a = await getFruit('pineapple');
		const b = await getFruit('strawberry');
		return Promise.all([a,b]);
	}catch(err){
	console.log(err)
	}
}

makeSmoothie().then(console.log);
```
.map .filter nece vratiti odmah jedan za drugim rezultat. Za vracanje jednog po jednog rezultata nam je potreban obican `for` loop i `await` rec u njemu

#### Moze se koristiti i u if statementu gde ce se cekati na dobijenu vrednost pa onda uporediti

```js
const fruitInspection = async () => {
	if (await getFruit('peach') === '%%peach%%'){
		console.log('looks peachy!');
	}
}

fruitInspection();
```

[[5. JavaScript|Nazad]] 
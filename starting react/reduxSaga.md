## Redux Saga 
### instalira se sledecom komandom
```bash
npm install redux-saga
```

posle sage najslicnije paket koji se koristi jeste redux thinker koji je jako slican sagi
`bitno je da ako sadrzi vise saga middleware svi oni importuju u jedan i nakace na reducer`

`Yield` je jednak async await

`call` kada se poziva kao prvi parameta je funckija koju zelimo a drugi je prametar nase funkcije

`put` je jednak dispatchu akcija a pre njega je `yield `

`takeLatest` koristi ime slic-a / handlera

## Dodavanje u projekat
`store.js` gde se storuju glavni reduceri  tu se dodaje sledece
```jsx
import createSagaMiddleware from 'redux-saga';

const sagaMiddleware = createSagaMiddleware();
```
#### u reduceru dodajemo sledece
```jsx
middleware : [
     ...getDefaultMiddleware(
      { thunk: false }
     ),
     sagaMiddleware
  ]
```

### i zadnji deo
```jsx
const sagas =[];

for (let saga in sagas) {

  sagaMiddleware.run(sagas[saga]);

}
```

pravi se `rootSaga.js` fajl i u njega smesta
```jsx
const sagas = {};
 

export default sagas;
```

u slic-u pravimo middleware objekat sa akcijom koji se kaci na reducer spreadovan
```jsx
//van slice-a kao initial state
const middlewareActions = {

  getMovies: () => { },

};
//unutar slice-a
...middlewareActions,

```

pise se ovog tipa radi razlikovanja da li je reducer akcija ili saga

i na kraju se ekposrtuje akcija u niz
```jsx
export const { setMovies, setSearchValue, `getMovies`} = movieSlice.actions
```

[[2. React|Nazad]] 
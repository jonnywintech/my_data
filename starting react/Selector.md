## Selector nam sluzi da pokupimo trenutno stanje i mozemo da ga modifikujemo

`Primeri`
```jsx
export const SelectGenres = (state) => state.genre.genres;

export const selectGenre = (state) => state.genre.selectedGenres;
```
`primer 2 sa filterom`
```jsx
export const SelectGenres = (state, filter) => state.genre.genres;
```


Koristi se u Delovima Aplikacije sa Destructorovanim kodom

```jsx
import { SelectGenres, selectGenre } from '../../features/genres/selectors';
```

Nad ovim kodom se koristi 
```jsx
import { useSelector } from 'react-redux/es/exports';
// i onda se smesta u variablu 

const genre = useSelector(SelectedGenre);
```


`primer 2 u delu aplikacije `
```jsx
const list = useSelector( ( state ) => selectedGenres( state, 'filter' ));
```

[[2. React|Nazad]]

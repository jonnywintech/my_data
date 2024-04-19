# `<Switch>`
### switch renderuje rute jednu po jednu 
najpre redneruje `<Route>` komponentu
## Jako bitna stavka je specificnost ruta.  Najpre se na  vrhu stavlja specificna ruta  a onda nadole sto manje specificna  jer React renderuje po redolsedu i necemo moci otvoriti specificnu rutu posle nespecificne
importuje se najpre sa sledecom sintaxom
```jsx
import { Switch } from 'react-router-dom';
```
# ne koristi ovo , depricated je
# koristiti 6.6 [[starting react/Routes|Routes]]
`primeri specificne rute`
```jsx
//<Switch>
//	<Route path='/articles/:title'>
//		<Article>
//	</Route>
// </Switch>
```

`primer nexpecificne rute`
```jsx
//<Switch>
//	<Route path='/articles'>
//		<Article>
//	</Route>
//</Switch>
```



[[2. React|Nazad]]


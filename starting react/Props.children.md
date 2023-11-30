
```jsx
export default function TabButtons(props){
	return <li> <button>{props.children}</button></li>
}
```

i onda u jsx

```jsx
import TabButtons from './components/TabButtons';
// some code

<TabButtons>Children PROP</TabButtons>

```

ovde imamo children prop koji se prosledjuje izmedju otvarajuceg i zatvarajuceg taga i rezervisana je rec u reactu te se nemoze proslediti kao atribut komponente
```jsx
<TabButtons children="childrenPROP" />
// ovo neradi jer je children rezervisana rec
```

ovo je drugi nacin da se prosledi informacija u komponentu
prvi nacin je naveden kao [[props]] . u zavisnosti on nacina primene ili stila kodiranje koriste se oba nacina pisanja.

### Moze se proslediti ceo jsx niz elemenata samo je bitno pravilo da sav kod mora biti wrapovan u jednu komponentu `<></>`

[[2. React|Nazad]] 
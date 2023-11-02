ovo se koristi da bi svaka komponetnta dobili hashovane klase i bila unique , tako da bezbrizno mozemo koristiti komponente svude bez straha da ce jedna klasa uticati na otstale komponente u aplikaciji

Napravi se css fajl sa `.module` reci u nazivu na primer

`Header.modlue.css`

onda se importuje u js fajlu gde se koristi 
```jsx
import classes from "./Header.module.css"


//a onda se targetuje klasa unutar Header.module.css

<header className={classes['header-image']}>
</header>

// alternativno moze se korstiti 'dot' sintaksa kada je samo jedna rec u pitanju

<header className={classes.header}>
</header>
```
# izgled dispatcha

importuje se  iz reduxa
```jsx
import { useDispatch } from 'react-redux';
```

u nazivu funkcije se menja naziv u `dispatch` radi lakseg koriscenja

```jsx
const dispatch = useDispatch();
```

u html se primenjuje uglavnom na buttonu ili input polju
prosledjuje se dispatch kao rezultat callback funkcije

```jsx
 <button className="remove-btn" onClick={()=> dispatch(removeItem(id))}>remove</button>
```

u ovom slucaju ima parametar id koji se prosledjuje [[Reducer|Reducer-u]]


[[2. React|Nazad]]


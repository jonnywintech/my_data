Use ref se moze koristiti za input element kada zelimo da react ne re-renderuje element

```jsx
import React, { useRef } from 'react';

function MojaKomponenta() { 
	// Kreiranje reference sa početnom vrednošću 
	const mojaReferenca = useRef(pocetnaVrednost); 
	// ... Ostala logika komponente ... 
}
```

useRef vraca promenljive objekat reference i taj objekat opstaje izmedju re-renderovanja

```jsx
import React, { useRef, useEffect } from 'react';

function MojaKomponenta() {
  const mojInputRef = useRef();

  useEffect(() => {
    // Ovo će fokusirati input element kada se komponenta montira
    mojInputRef.current.focus();
  }, []);

  return <input ref={mojInputRef} type="text" />;
}
```

u slucaju da imamo custom komponentu ona se mora wrapovati sa `React.forwardRef`

```jsx
import React from 'react';
import classes from './Input.module.css';

const Input = React.forwardRef((props, ref) => {
  return (
    <div className={classes.input}>
      <label htmlFor={props.input.id}>{props.label}
      </label>
        <input ref={ref} {...props.input}/>
    </div>
  );
});

export default Input;
```

[[2. React|Nazad]]
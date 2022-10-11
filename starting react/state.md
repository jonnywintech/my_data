# State iliti stanje variable koje se renderuje pri izmeni vrednosti

#### importuje se na vrhu elementa sa 
```jsx
import { useState } from 'react';
```

### Postavljanje vrednosti za  state
```jsx
const [state, setState] = useState(initialSate);
```

primer
```jsx
function Counter({initialCount}) {
  const [count, setCount] = useState(initialCount);
  return (
    <>
      Count: {count}
      <button onClick={() => setCount(initialCount)}>Reset</button>
      <button onClick={() => setCount(prevCount => prevCount - 1)}>-</button>
      <button onClick={() => setCount(prevCount => prevCount + 1)}>+</button>
    </>
  );
}
```

set state se ne menja direktno nikako nego preko callback funkcije 








[[2. React|Nazad]]

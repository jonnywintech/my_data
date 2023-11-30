primer App.js
```jsx
import Input from './Input';

function App() {
  return (
    <div id="app">
      <Input type="text" placeholder="Your name" />
      <Input richText placeholder="Your message" />
    </div>
  );
}

export default App;
```

Input.js
```jsx
export default function Input({...props}) {
return <>
    <input {...props} />
</>
}
```

ovako dinamicno mozemo napraviti input polje da bude bilo koje vrednosti

[[2. React|Nazad]]
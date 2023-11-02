# Komponente se Pišu u Pascal case varijanti
### što zanči da je prvo početno slovo komponente veliko
## Primeri kako izgleda prosta react aplikacija
`obavezno se importuje na vrhu  index.js`
```jsx
import React from "react"

import ReactDOM from "react-dom"
```

`komponenta`
```jsx 
function Page() {

return (

<h1>It's working!</h1>

		)
	}
```
### `Napomena `
#### u return delu funckije moze biti samo jedan element
taj jedan element moze sadrzati vise drugih ali bitno je da je samo jedan `<div>`
na primer koji ce sadrzati druge komponente


`renderovanje komponenti kroz react`
```jsx
ReactDOM.render(<Page />, document.getElementById("root"))
```


`izgled index.js u reactu`
```jsx
import React from 'react';

import ReactDOM from 'react-dom/client';

import './index.css';

import App from './App';  

const root = ReactDOM.createRoot(document.getElementById('root'));

root.render(

  <React.StrictMode>

    <App />

  </React.StrictMode>

);
```


```jsx
ReactDOM.render(<App />, document.getElementById('root'));
```

[[Parrent Child]]  parrent child relationship izmedju komponenti

[[2. React|Nazad]]
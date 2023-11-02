# Router in react

 u komponenti koja se renderuje se dodaje sledeći import 
```jsx
import { BrowserRouter as Router, Route } from "react-router-dom"
```

a umesto `<div>  </div>` koji wrapuje(obavija elemente) dodaje se `<Router></Router>`
primeri

`<Router>` se postavlja u aplikaciji u kojoj se redneruju iliti smenjuju rute kao osnova za  sve
```jsx
	function App() {

  return (

    <Router>

      <Header />

      <main>

        {/* Add Routes here! */}

      </main>

      <Footer />

    </Router>

  );

}
```

ONDA PROMENLJIVI DEO OBAVIJAMO SA  `<Switch> i <Route>`
Switch  Obavija vise elemenata koji se smenjuju a Ruta obavija element koji ce se renderovati na datoj ruti 
putanja na koju vodi stranice se renderuje sa `<Route path="/"> </Route>` 

```jsx
	  <Switch>

		
        <Route path="/">

	          <Home />   {/* Komponenta Koja se Renderuje u ruteru */}

        </Route>

			 {/*  druga ruta u switchu koja se renderuje*/}
		<Route path="/about">

	          <About />   {/* Komponenta Koja se Renderuje u ruteru */}

        </Route>
        
       </Switch>
       
```
Ovo rendereovanje se izvrsava kada se na navigaciji klikne na `<Link>` element (moze biti navbar ili  ili neki drugi deo teksta obicno `<a href=''>` dok je u reactu `<Link>`)

[[Linkovanje Ruta]]


[[2. React|Nazad]]

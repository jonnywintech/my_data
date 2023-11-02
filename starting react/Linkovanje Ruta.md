
komanda koja nam omogućava koriscenje router linkova

```jsx
import { Link } from "react-router-dom";
```
puna putanja
```jsx
import { BrowserRouter as Router, Route, Link, NavLink } from 'react-router-dom';
```

primer `<a> taga pre i posle </a>`
```jsx
	 <a href={`/articles/${article.slug}`}>
	
	                  {article.title}
	
	 </a>
```

izmene kada se dodaje Link
```jsx
	<Link to="/about">About</Link>  
	<NavLink to="/about">About</NavLink>
```
### Razlika izmedju NavLinka i Link-a je to sto NavLink ima status Active kada se klikne na njega i pogodan je za navigaciju

# Da bi radila komponenta mora se obaviti `<Router>` tagom a to se radi u app Komponenti ako je ona krainja i obavija i navbar i Komponente Sa Routama i Stranicama koje se renderuju
primer navbara
```jsx
const Navbar = () => {

  return (


    <nav class="navbar navbar-expand-lg bg-dark navbar-dark">

    <div class="container-fluid">

      <a class="navbar-brand" href="#">Movies</a>

      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">

        <span class="navbar-toggler-icon"></span>

      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">

        <ul class="navbar-nav me-auto mb-2 mb-lg-0">

          <li class="nav-item">

            <Link class="nav-link active" aria-current="page" to="/">Home</Link>

          </li>

          <li class="nav-item">

            <Link class="nav-link" to="/movies">Movies</Link>

          </li>

          <li class="nav-item dropdown">

            <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">

              Dropdown

            </a>

            <ul class="dropdown-menu">

              <li><a class="dropdown-item" href="#">Action</a></li>

              <li><a class="dropdown-item" href="#">Another action</a></li>

              <li><a class="dropdown-item" href="#">Something else here</a></li>

            </ul>

          </li>

          <li class="nav-item">

            <a class="nav-link disabled">Disabled</a>

          </li>

        </ul>

      </div>

    </div>

  </nav>

  )

}
```

[[2. React|Nazad]]

## Primer gde se vidi parrent child komponente

## 2 child komponente
```jsx
function Header() {

return (

<header>

<nav>

<img src="./react-logo.png" width="40px" />

</nav>

</header>

)

}

  

function Footer() {

return (

<footer>

<small>© 2021 Ziroll development. All rights reserved.</small>

</footer>

)

}
```

# parrent komponenta koja renderuje 2 childa


```jsx
function Page() {

return (

		<div>
		
		<Header />
		
		<MainContent />
		
		<Footer />
		
		</div>

		)

	}
```

[[2. React|Nazad]]


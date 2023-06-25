## Props je objekat kome prosledjujemo vrednost iz druge komponente

### Props Komponenta
```jsx
export default function Contact(props) {


return (

	<div className="contact-card">

		<img src={props.img}/>
		
		<h3>{props.name}</h3>
		
		<div className="info-group">
		
		<img src="./images/phone-icon.png" />
		
		<p>{props.phone}</p>
		
		</div>
		
		<div className="info-group">
		
		<img src="./images/mail-icon.png" />
		
		<p>{props.email}</p>
		
		</div>

	</div>

)

}
```

## komponenta koja se renderuju u aplikaciji
```jsx
<Contact

img="./images/mr-whiskerson.png"

name="Mr. Whiskerson"

phone="(212) 555-1234"

email="mr.whiskaz@catnap.meow"

/>
```

bitno je da se naziv objekta poklapa sa komponentom u kojoj proseldjujemo stavke

Prosledjivanje podataka se vrsi preko props u jednom pravcu Parent -> child 

[[2. React|Nazad]]

Tabs.jsx
```jsx
export default function Tabs({ children, buttons}){
	return <>
		<menu>
		 {buttons}
		</menu>
		{children}
	</>
}
```

Examples.jsx
```jsx
export default function Examples(){
	<Section title="Examples" id="Examples">
		<Tabs
			componentWrapper="menu"
			// ovde unosimo vrednost menu kao string gde 
			//reakt prosledjuje i pravi dinamicnu komponentu u zavisnosti koji parametar prosledimo
			buttons={
				<TabButton
					isSelected={selectedTopic === 'components'}
					onClick={()=> handleSelect('components')}
					>
					Components
				</TabButton>
				<TabButton
					isSelected={selectedTopic === 'jsx'}
					onClick={()=> handleSelect('jsx')}
					>
					Components
				</TabButton>
			}
		> Children
		</Tabs>
	</Section>
}

```

napredna verzija Tabs.jsx gde imamo dinamican wrapper umesto `<menu>`
```jsx
export default function Tabs({ children, buttons, componentWrapper }){
	const ComponentWrapper = componentWrapper;
	return <>
		<ComponentWrapper>
		 {buttons}
		</ComponentWrapper>
		{children}
	</>
}
```
nemozemo direktno proslediti componentWrapper nego prosledjujemo vrednost konstanti i onda je koristimo kao wrapper

[[2. React|Nazad]]


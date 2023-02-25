There is 2 ways to lazy load component
### 1. Import { lazy } from React
primer
```jsx
import React, { lazy } from 'React';
```

### 2. Import Suspense element wrappera

```jsx
import React, { lazy, Suspense } from 'React';

// dalje u kodu 
<Suspense falback={<h2> Loading</h2>}>
	<Routes>
		<Route path="/" element ={<Element />} />
	</Routes>
</Suspense>
```
Suspense ima Fallback element koji se prikazuje dok se u pozadini sajt ucitava
Mora biti wrappovan oko Routa
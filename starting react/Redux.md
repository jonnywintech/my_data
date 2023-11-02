#### `React-redux je globalni state manager` koji dozvoljva da se sve komponente menjaju i smeste na jedno mesto

# instaliranje redux toolkita
```bash
npx create-react-app my-app --template redux
```

## STORE  mesto gde se cuvaju sve  vrednosti komponenata
#### u src folderu se pravi  /app/store.js
primer store.js
```jsx
import { configureStore } from "@reduxjs/toolkit";

import counterReducer from  '../features/counter'

  

export const store = configureStore({

    reducer: {

            counter: counterReducer,

    }

});
```
## `Importuje se  `[[Reducer]] `i onda napise njegovo ime`


### Slice je deo koda koji koristi odredjena komponenta i izdeljen je na delove po potrebi
### nalazi se u src/features/counter.js
primer za counter
```jsx
import { createSlice } from "@reduxjs/toolkit/dist/createSlice";

  

const initialState = {

    count: 0

}

  

export const counterSlice = createSlice({

    name: "counter",

    initialState,

    reducers: {

        increment: (state)=> {

            state.count +=1;

        },

        decrement: (state)=> {

            state.count -=1;

        },

    }

});

  

export const { increment, decrement } = counterSlice.actions;

  

export default counterSlice.reducer;
```


## Da bi store funkcionisao potrebno je  dodati `<Provider>`  u index.js
 
 ```jsx
 import { store } from './app/store';
 import { Provider } from './react-redux';

	ReactDOM.render(
	<React.StrictMode>
	<Provider store={store}>
	<App />
	</Provider>
	</React.StrictMode>,
	document.getElemetById('root')
	);

```


[[2. React|Nazad]]

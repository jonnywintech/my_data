# Kratko objasnjene Hookova 
-   **Create a Redux store with `configureStore`**
    -   `configureStore` accepts a `reducer` function as a named argument
    -   `configureStore` automatically sets up the store with good default settings
-   **Provide the Redux store to the React application components**
    -   Put a React Redux `<Provider>` component around your `<App />`
    -   Pass the Redux store as `<Provider store={store}>`
-   **Create a Redux "slice" reducer with `createSlice`**
    -   Call `createSlice` with a string name, an initial state, and named reducer functions
    -   Reducer functions may "mutate" the state using Immer
    -   Export the generated slice reducer and action creators
-   **Use the React Redux `useSelector/useDispatch` hooks in React components**
    -   Read data from the store with the `useSelector` hook
    -   Get the `dispatch` function with the `useDispatch` hook, and dispatch actions as needed

# Redux komponente i njihov izgled
izgled counter komponente
```jsx
import { createSlice } from '@reduxjs/toolkit';

// pocetna vrednost
  
const initialState = {

    count: 0

}


export const counterSlice = createSlice({
	// ime reducera
    name: "counter",

    initialState,

    reducers: {
		//akcija  reducera 
        increment: (state)=> {

            state.count +=1;

        },

        decrement: (state)=> {

            state.count -=1;

        },

        reset: (state)=> {

            state.count = 0;

        },
		// akcija koja prima parametar kao vrednost
        incrementByAmount: (state, amount) => {

            state.count += amount.payload;

        },
	// akcija koja prima parametar kao vrednost
        decrementByAmount: (state, amount) => {

            state.count -= amount.payload;

        },

    }

});

  
 // izvoz akcija reducera
export const { increment, decrement,reset,incrementByAmount,decrementByAmount } = counterSlice.actions;

  
// izvoz reducera
export default counterSlice.reducer;
```


[[2. React|Nazad]]

# izgled slice sa reducerom

reducer sa dve akcije

```jsx
 reducers:{

        clearCart: (state)=> {

            state.cartItems = [];

        },

        removeItem: (state, action)=> {

            const itemId = action.payload;

            state.cartItems = state.cartItems.filter((item)=>

            item.id !== itemId);  

        },

    },
```

izgled  celog slice dela gde se primenjuje `reducer`
```jsx
const cartSlice = createSlice({

    name: "cart",

    initialState,

    reducers:{

        clearCart: (state)=> {

            state.cartItems = [];

        },

// reducer akcija koja ima 2 parametra. 
// prvi je state a drugi je akcija koja ima item ID kao parametar
        removeItem: (state, action)=> {

// payload se dobija sa frontenda i prosledjuje se kao parametar
            const itemId = action.payload;

            state.cartItems = state.cartItems.filter((item)=>

            item.id !== itemId);  

        },

    },

});
```

[[Dispatch]] -- Kako se aktivira Reducer (tipa kada se klikne)

[[2. React|Nazad]]

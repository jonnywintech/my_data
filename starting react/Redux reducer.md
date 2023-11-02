# Akcije koje se mogu primeniti nad globalnim/inicijalnim stejtom

### cartItems array sa podacima o proizvodu

```jsx
const cartItems = [

  {

    id: 'rec1JZlfCIBOPdcT2',

    title: 'Samsung Galaxy S8',

    price: '399.99',

    img: 'https://dl.airtable.com/.attachments/64b266ad865098befbda3c3577a773c9/24497852/yedjpkwxljtb75t3tezl.png',

    amount: 1,

  },
```


### initialState iliti pocetno stanje Slice-a

```jsx
const initialState = {

    cartItems: cartItems,

    amount: 3,

    total: 0,

    isLoading: true,

};
```

### slice sa Reducerom

```jsx
const cartSlice = createSlice({

    name: "cart",

    initialState,

// akcija koja menja state nad globalnim stanjem
    reducers:{

        clearCart: (state)=> {

            state.cartItems = [];

        },

    }
```


## Celokupni izgled slic-a
```jsx

// proizvod i njegovi podaci (ovaj deo se nalazi u sopstvenom .js falu ako se ne koristi API)
/* const cartItems = [

  {

    id: 'rec1JZlfCIBOPdcT2',

    title: 'Samsung Galaxy S8',

    price: '399.99',

    img: 'https://dl.airtable.com/.attachments/64b266ad865098befbda3c3577a773c9/24497852/yedjpkwxljtb75t3tezl.png',

    amount: 1,

  },
 */

// pocetno stanje globalnog stejta
const initialState = {

    cartItems: cartItems,

    amount: 3,

    total: 0,

    isLoading: true,

};
// slice 
const cartSlice = createSlice({

    name: "cart",

    initialState,

// akcija koja menja state nad globalnim stanjem
    reducers:{

        clearCart: (state)=> {

            state.cartItems = [];

        },

    }

});
```

[[Reducer]] -- menjanje trenutong stejta



[[2. React|Nazad]]
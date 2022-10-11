## Slice je deo aplikacije i koristi se radi lakse organizacije koda

# Koraci
### 1. Import
```jsx
import { createSlice } from '@reduxjs/toolkit'
```

### 2. Postavljanje pocetnog stanje ili stejta
```jsx
const initialState = {
// objekat koji sadrzi pocetno stanje
    genres: [],
// on je destructovan unutar slic-a
}
```

### 3. inicijalna vrednost slic-a
```jsx
const genreSlice = createSlice({

  name: 'genre',

  initialState,

  selectedGenres,

  reducers: {}
  );

```

### 4. [[Reducer|Reduceri]]
```jsx
reducers: {

    //actions

    addGenre: (state, action) => {
	// akcija kupi iz input forme vrednost i sacuvava je u storu
        state.genres.push(action.payload);

    },

    removeGenre: (state, action) => {

      state.genres = state.genres.filter((item)=> item !== action.payload);

    },

    selectGenre: (state, action) => {

      state.selectedGenres = action.payload;

    },

    editGenre: (state, action) => {

     state.genres = state.genres.map((item)=> item === state.selectedGenres ? action.payload : item)

     //setovanje selectovanog zanra na prazan niz

     state.selectedGenres = '';

    }

  }
```

### 5. Dodati Slice u [[Redux|store]]
### ceo primer slice-a

```jsx
import { createSlice } from '@reduxjs/toolkit'

  

const initialState = {

    genres: [],

}

const selectedGenres = "";

  

const genreSlice = createSlice({

  name: 'genre',

  initialState,

  selectedGenres,

  reducers: {

    //actions

    addGenre: (state, action) => {

        state.genres.push(action.payload);

    },

    removeGenre: (state, action) => {

      state.genres = state.genres.filter((item)=> item !== action.payload);

    },

    selectGenre: (state, action) => {

      state.selectedGenres = action.payload;

    },

    editGenre: (state, action) => {

     state.genres = state.genres.map((item)=> item === state.selectedGenres ? action.payload : item)

     //setovanje selectovanog zanra na prazan niz

     state.selectedGenres = '';

    }

  }

});

  

export const {addGenre, removeGenre, selectGenre, editGenre } = genreSlice.actions

  

export default genreSlice.reducer
```
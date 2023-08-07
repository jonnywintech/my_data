
u globalnom stejtu se dodaje pageNumber sa pocetnom vrednoscu

```jsx
const initialState = {
  movies: [],
  sortBy: "",
  pageNumber: 1,
};
```

takodje se pravi i setter za pageNumber
```jsx
setPageNumber: (state, action) => {
      state.pageNumber += action.payload;
}

export const { setPageNumber } = movieSlice.actions;
```

```jsx
export const moviesSelector = (state) => {
    const filter = state.movie.searchValue;
    const sortBy = state.movie.sortBy;
    let movies = state.movie.movies;
    movies = movies.filter((movie) => movie.title.toLowerCase().includes(filter.toLowerCase()));
    
    switch (sortBy) {
      case 'nameAsc':
       movies = movies.sort((a,b) => a.title.toLowerCase() > b.title.toLowerCase() ? 1 : -1)
       break;
      case 'nameDesc':
       movies = movies.sort((a,b) => a.title.toLowerCase() > b.title.toLowerCase() ? -1 : 1)
       break;
      case 'durationAsc':
         movies = movies.sort((a,b) => a.duration > b.duration ? 1 : -1)
        break;
      case 'durationDesc':
         movies = movies.sort((a,b) => a.duration > b.duration ? -1 : 1)
         break;
    }
    return movies.slice((state.movie.pageNo -1)*5, state.movie.pageNo * 5);
}
```
## paginacija se vrsi ovom komandom u selektoru

```jsx
return  movies = movies.slice((state.movie.pageNo -1) *5, state.movie.pageNo *5)
```
`broj stranice je inicijalno 1 u slice.js  sa -1 postavljamo ga na 0tu vrednost a broj 5 odredjuje koliko elemenata imamo na stranici, onda deo posle zareza odredjuje za sledecu stranicu koliko imamo elemenata i tako u krug`

imamo 2 selectora da bi mogli da disablujemo dugme i  znamo trenutnu stranicu
```js
export const selectMoviePage = (state) => state.movie.pageNumber;
export const hasNextPage = (state) =>
  state.movie.pageNumber * 5 < state.movie.movies.length;

```

onda imamo dispatch akcije koji menja trenutnu vrednost pageNo s cime se menja sadrzaj
```jsx
<button
disabled={!haveNext}
onClick={() => dispatch(setPageNumber(+1))}> Next
</button>
```

[[2. React|Nazad]] 
## sortiranje u nizu ili objektu

```jsx
export const moviesSelector = (state) => {

    const filter = state.movie.searchValue;

    let movies = state.movie.movies;

    const sortBy = state.movie.sortBy;

    movies = movies.filter((movie) => movie.title.includes(filter));

   switch (sortBy) {

    case "nameASC":

        return movies = movies.sort((a,b) => a.title.toLowerCase() > b.title.toLowerCase() ? 1 : -1);

    case "nameDESC":

        return movies = movies.sort((a,b) => a.title.toLowerCase() < b.title.toLowerCase() ? 1 : -1);

    case "durationASC":

        return movies = movies.sort((a,b) => a.title.toLowerCase() - b.title.toLowerCase() ? 1 : -1);

    case "durationDESC":

        return movies = movies.sort((a,b) => b.title.toLowerCase() - a.title.toLowerCase()  ? 1 : -1);

    default:

    return  movies = movies.slice((state.movie.pageNo -1) *5, state.movie.pageNo *5)

   }

}
```


[[2. React|Nazad]]

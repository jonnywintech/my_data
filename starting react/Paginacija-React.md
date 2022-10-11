## paginacija se vrsi sledecom komandom u selektoru

```jsx
	return  movies = movies.slice((state.movie.pageNo -1) *5, state.movie.pageNo *5)
```
`broj stranice je inicijalno 1 u slice.js  sa -1 postavljamo ga na 0tu vrednost a broj 5 odredjuje koliko elemenata imamo na stranici, onda deo posle zareza odredjuje za sledecu stranicu koliko imamo elemenata i tako u krug`


[[2. React|Nazad]] 
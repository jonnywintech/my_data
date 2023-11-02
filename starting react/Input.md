Input koje je tipa tekst ima sledece vrednosti

```jsx
	<input

          className='form-control'

          type="search" placeholder='Search' value={value} onChange={(e)=>dispatch(setSearchValue(e.target.value))}

        />
```


checkbox

```jsx
 <div class="form-check">

        <input class="form-check-input" name="movieSelector" type="checkbox" checked={isChecked}
        // u ovom slucaju value se koristi da bi se primenio Select all ili Deselect all DUGME

         onChange={()=>dispatch(toggleSelectMovie(movie.id))} id="movieSelector"/>

        <label class="form-check-label" for="movieSelector">

          Selected

        </label>

      </div>
```

[[2. React|Nazad]]  
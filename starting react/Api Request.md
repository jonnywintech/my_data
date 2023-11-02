# Za konektovanje Prema apiju se koristi sledece

### Pravi se service folder i u njemu smesta http request;
### za ovo se koristi axios biblioteka koja olaksava stvari
`primeri HttpService.js`

```jsx
import axios from "axios";

export default class HttpService {
  constructor() {
    this.client = axios.create({
      baseURL: "http://localhost:3000/api/",
    });
  }
}
```

`korak dva pravljenje servisa koji kupi ove podatke MovieService.js`

```jsx
import HttpService from "./HttpService";

class MovieService extends HttpService {
  getAll = async () => {
    const { data } = await this.client.get("movies");

    return data;
  };
}

const movieService = new MovieService();

export default movieService;
```


[[2. React|Nazad]] 
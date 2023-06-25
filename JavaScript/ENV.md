Kao sto postoji .env fajl u laravelu tako isto postoji konfiguracija za JS


primer .env.example
```.env
REACT_APP_API_KEY=

REACT_APP_API_URL=

REACT_APP_BASE_URL=
```

onda imamo global folder u kome se pozivaju ove variable
/src/globals/constants.js

```javascript
export const API_KEY = process.env.REACT_APP_API_KEY;

export const API_URL = process.env.REACT_APP_API_URL;

export const BASE_URL = process.env.REACT_APP_BASE_URL;
```

i onda imamo import deo gde se pozivaju ove konstante

```javascript
import { API_URL } from 'global/constants';

// u ovom primeru se koristi axios
  

axios.defaults.baseURL = API_URL;

axios.defaults.headers.post['Accept'] = 'application/json';

axios.defaults.headers.post['Content-Type'] = 'application/json';
```
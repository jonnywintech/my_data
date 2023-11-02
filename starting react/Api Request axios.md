Za postavljanje apija su potrebna dva fajla global.js i interceptors.js
i opcinalno treci koji ne racunam u ova dva jer je globalni config constants file
constants.js sve konstante koje se koriste u aplikaciji , konfig fajl
global.js je glavna ruta pasovana u axios
glavna ruta cita BASE_URL koji cita iz  .env fajla

constants.js
```jsx
export const BASE_URL = process.env.REACT_APP_BASE_URL;
```


global.js
``` jsx
import axios from 'axios';

import { BASE_URL } from '../globals/constants';

  

axios.defaults.baseURL = BASE_URL;

```


interceptors se koristi za hendlovanje gresaka koje mogu doci preko api rute

interceptors.js
```jsx
import axios from "axios";

  

axios.interceptors.response.use((response) => {

return response;

}, (error) => {

if (error.code !== 'ERR_CANCELED') return Promise.reject(error);

});
```
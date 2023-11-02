installaciaj
```bash
 npm create vite@latest 
```

name project and choose react

cd u my-app
```bash
npm i @reduxjs/toolkit react-redux redux-saga axios 
```

```bash
npm install react-router-dom localforage match-sorter sort-by
```

go to app and cleanup App.test.js, reportWebVitals.js, setupTests

```bash
npm run dev
```

create store folder

add store.js
in that file add 

```jsx
import { configureStore } from '@reduxjs/toolkit'

export const store = configureStore({
  reducer: {},
})
```

main.js | index.js

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App.jsx';
import { store } from './store/store';
import { Provider } from "react-redux";

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <Provider store={store}>
      <App />
    </Provider>
    ,
  </React.StrictMode>,
);

```

with react router

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App.jsx';
import { store } from './store/store';
import { Provider } from "react-redux";
import { BrowserRouter } from 'react-router-dom';

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <Provider store={store}>
	    <BrowserRouter>
		      <App />
	    </BrowserRouter>
    </Provider>
    ,
  </React.StrictMode>,
);

```
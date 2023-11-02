## Primer Ruta v6 routera
importuje se najpre sa sledecom sintaxom
```jsx
import { Routes } from 'react-router-dom';
```

Primer nestovane rute
```jsx
function App() {
  return (
    <Routes>
      <Route path="invoices" element={<Invoices />}>
        <Route path=":invoiceId" element={<Invoice />} />
        <Route path="sent" element={<SentInvoices />} />
      </Route>
    </Routes>
  );
}
```

Drugi primer
```jsx
<Routes>
  <Route path="/" element={<Dashboard />}>
    <Route
      path="messages"
      element={<DashboardMessages />}
    />
    <Route path="tasks" element={<DashboardTasks />} />
  </Route>
  <Route path="about" element={<AboutPage />} />
</Routes>
```


[[2. React|Nazad]]

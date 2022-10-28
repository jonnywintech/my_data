kada se izradjuje aplikacija vezuje se lokalni dev sa onim koji je u konteineru tako da svaka izmena u lokalu se primanjuje u kontaineru
`primer`
```bash
docker run -d -p 5001:3000 -v $(pwd):app react-app
```

[[8. Docker|Nazad]] 
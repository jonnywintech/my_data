Za email recorde u dns podesavanja pored mx recorda potrebni su jos par.

- DKIM
- DMARC

### DKIM se generiše i onda dodaje u dns recordima na serveru kao txt record
primer
___
| Type | Name | Priority | Content | TTL |
| --- | --- | --- | --- | --- |
| TXT  | titan1_domainkey | 0 | "v=DKIM1; k=rsa; p=eaadab0ba3b96fc66d646a0f8e831c2c | 360 |

---
TTL  - je vreme koliko se ovaj record cuva na drugim serverima. za radi testiranja stavlja se sto manji oko 360. kasnije kada se sve utvrdi da sve funkcionise moze se povecati.


### DMARC - on se dodaje u  dns kao txt record takodje samo da odredjenim parametrima na osnovu domena

| Type | Name   | Priority | Content                                                | TTL |
| ---- | ------ | -------- | ------------------------------------------------------ | --- |
| TXT  | _dmarc | 0        | "v=DMARC1; p=none; rua=mailto:office@evolvadigital.com | 360 |



# BTC Rate Check Service

## Implements the following API:

### `GET` /rate

The request returns the current BTC course to UAH using Binance API service.

#### Parameters

``No parameters``

#### Response Codes

```
200: Returns actual exchange rate BTC to UAH
400: Invalid status value
```

---

### `POST` /subscribe

The request checks if there is no e-mail address in the current file database and, if it is not present, adds it.
Additionally, sends a letter notifying that user will be receiving messages about exchange rates.

#### Parameters

``email`` ***string***: email address that is going to be added to file database

#### Response Codes

```
200: E-mail address is added
409: Such an e-mail address already exists
```

---

### `POST` /sendEmails

The request sends current exchange rate (BTC to UAH) to subscribed e-mail addresses using goroutines. Additionally,
returns an e-mail addresses array if during sending a letter to them any error occurred.

#### Parameters

``No parameters``

#### Response Codes

```
200: E-mails are sent
```

## Usage:

- Locally

```
git clone https://github.com/nazarsavorona/btc-rate-check-service.git
cd .\btc-rate-check-service\
docker build -t btc-rate-check-service .
docker run -p 8081:8081 btc-rate-check-service
```

Now you can reach an API using [`http://localhost:8081/api`](http://localhost:8081/api)
or [`http://127.0.0.1:8081/api`](http://127.0.0.1:8081/api) and its web
version [`http://localhost:8081`](http://localhost:8081).

- Deployed version `temporarily unavailable`
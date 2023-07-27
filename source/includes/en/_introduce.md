# Interface Description

## Feedback Email

Email: <a href="mailto:api@bg.exchange" id="api-support">api@bg.exchange</a>

## request address
**HTTP request address**<br>

<a id="HTTP-HOST"></a>
HOST: `https:api.bg.exchange/hk`

**WEBSOCKET request address**

- ~~WebSocket private channel (DEPRECATED): `wss://ws.bg.exchange`~~
- ~~WebSocket public channel (DEPRECATED): `wss://ws.bg.exchange/ws`~~
- WebSocket public channel V2: `wss://ws.bg.exchange/v2/ws`
- WebSocket private channel V2: `wss://ws.bg.exchange/v2/ws`

[^1^]: [Link](#WS_HOST_PRIVATE)
[^2^]: [Link](#WS_HOST_PUBLIC)
[^3^]: [Link](#WS_HOST_PUBLIC_V2)
[^4^]: [Link](#WS_HOST_PRIVATE_V2)


##Response Status

> <a name="ResonpseExample">[HTTP/1.1 400](#ERR1)</a>


```json
{
  "code":1087,
  "message": "No data found"
}
```


> <a name="ResonpseExample">[HTTP/1.1 401](#ERR2)</a>


```json
{
  "code":40001,
  "message": "ACCESS_KEY cannot be empty"
}
```

> <a name="ResonpseExample">[HTTP/1.1 500](#ERR1)</a>


```json
{
  "code":500,
  "message": "Internal Server Error"
}
```




Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request |
400 | Bad Request -- The client should not repeat this request without modification. | <code>message</code> string
401 | Unauthorized -- Your API key is wrong, See [Authentication Description](#auth) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string


# Glossary
|noun|suggestion|
|---|---|
|currency| currency, such as BTC, USDT,HKD, USD|
|product|trading product, such as BTC_HKD|

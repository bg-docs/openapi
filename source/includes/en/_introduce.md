# interface

**Feedback email**

Email: <a href="mailto:api@bg.exchange">api@bg.exchange</a>

**Request URL**

HOST: `https:api.bg.exchange/hk/`

**RESPONSE STATUS**

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request |
400 | Bad Request  -- The client should not repeat this request without modification. | <code>message</code> string
401 | Unauthorized -- Your API key is wrong, See [鉴权说明](#auth) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string


# Glossary
|Term|Meaning|
|---|---|
|currency|the currency, e.g. BTC, USDT, HKD, USD|
|product|the trading product, e.g. BTC_HKD|

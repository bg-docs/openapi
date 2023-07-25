# 接口說明

**反饋郵箱**

Email: <a href="mailto:api@bg.exchange">api@bg.exchange</a>

**請求地址**

HOST: `https:api.bg.exchange/hk/`

**RESPONSE STATUS**

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request |
400 | Bad Request  -- The client should not repeat this request without modification. | <code>message</code> string
401 | Unauthorized -- Your API key is wrong, See [鉴权说明](#auth) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string


# 名詞解釋
|名詞|示意|
|---|---|
|currency|幣種, 例如 BTC, USDT,HKD, USD|
|product|交易產品,例如 BTC_HKD|

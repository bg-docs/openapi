# 接口说明

**反馈邮箱**

Email: <a href="mailto:api@bg.exchange">api@bg.exchange</a>

**请求地址**

HOST: `https:api.bg.exchange/hk/`

**RESPONSE STATUS**

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request |
400 | Bad Request  -- The client should not repeat this request without modification. | <code>message</code> string
401 | Unauthorized -- Your API key is wrong, See [鉴权说明](#auth) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string


# 名词解释
|名词|示意|
|---|---|
|currency|币种, 例如 BTC, USDT,HKD, USD|
|product|交易产品,例如 BTC_HKD|



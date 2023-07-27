# 接口說明

##反饋郵箱

Email: <a href="mailto:api@bg.exchange" id="api-support">api@bg.exchange</a>

##請求地址
**HTTP請求地址**<br>

<a id="HTTP-HOST"></a>
HOST: `https:api.bg.exchange/hk`

**WEBSOCKET請求地址**

- ~~WebSocket私有頻道(DEPRECATED): `wss://ws.bg.exchange`~~
- ~~WebSocket公共頻道(DEPRECATED): `wss://ws.bg.exchange/ws`~~
- WebSocket公共頻道V2: `wss://ws.bg.exchange/v2/ws`
- WebSocket私有頻道V2: `wss://ws.bg.exchange/v2/ws`

[^1^]: [鏈接](#WS_HOST_PRIVATE)
[^2^]: [鏈接](#WS_HOST_PUBLIC)
[^3^]: [鏈接](#WS_HOST_PUBLIC_V2)
[^4^]: [鏈接](#WS_HOST_PRIVATE_V2)


##Response Status

> <a name="ResonpseExample">[HTTP/1.1 400](#ERR1)</a>


```json
{
  "code":1087,
  "message":"查找不到數據"
}
```


> <a name="ResonpseExample">[HTTP/1.1 401](#ERR2)</a>


```json
{
  "code":40001,
  "message":"ACCESS_KEY不能為空"
}
```

> <a name="ResonpseExample">[HTTP/1.1 500](#ERR1)</a>


```json
{
  "code":500,
  "message":"Internal Server Error"
}
```




Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request |
400 | Bad Request  -- The client should not repeat this request without modification. | <code>message</code> string
401 | Unauthorized -- Your API key is wrong, See [鑑權說明](#auth) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string


# 名詞解釋
|名詞|示意|
|---|---|
|currency|幣種, 例如 BTC, USDT,HKD, USD|
|product|交易產品,例如 BTC_HKD|

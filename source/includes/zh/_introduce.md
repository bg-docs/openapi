
# 接口说明

##反馈邮箱

Email: <a href="mailto:api@bg.exchange" id="api-support">api@bg.exchange</a>

##请求地址
**HTTP请求地址**<br>

<a id="HTTP-HOST"></a>
HOST: `https://api.bg.exchange/hk`

**WEBSOCKET请求地址**

- WebSocket公共频道V2<a id="WS_HOST_PUBLIC_V2"></a>: `wss://ws.bg.exchange/v2/ws`
- WebSocket私有频道V2<a id="WS_HOST_PRIVATE_V2"></a>: `wss://ws.bg.exchange/v2/ws`


##Response Status

> <a name="ResonpseExample">[HTTP/1.1 400](#ERR1)</a>


```json
{
  "code":1087,
  "message":"查找不到数据"
}
```


> <a name="ResonpseExample">[HTTP/1.1 401](#ERR2)</a>


```json
{
  "code":40001,
  "message":"ACCESS_KEY不能为空"
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
401 | Unauthorized -- Your API key is wrong, See [鉴权说明](#auth) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string


# 名词解释
|名词|示意|
|---|---|
|currency|币种, 例如 BTC, USDT,HKD, USD|
|product|交易产品,例如 BTC_HKD|



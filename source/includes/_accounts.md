# 账户信息

## 获取所有账户余额信息

<font class="httpget">GET</font> */v1/accounts*


获取用户所有的交易账户信息

**冻结账户**

当用户下单完成，自己会被划拨到冻结账户。被划拨到冻结账户的资金不能被用于其他交易，以及提现操作。当订单成交或被取消，冻结账户的资金会被释放。

> 鉴权信息

> 私有信息的鉴权信息，请参考 [鉴权说明](#auth)

> REQUEST EXAMPLE

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("${host}/v1/accounts")
  .method("GET", null)
  .addHeader("ACCESS-KEY", "HKBGE-0d7f7a3ba656a73c38295ad879779e16")
  .addHeader("ACCESS-SIGN", "a3ef844e35289b3af63bd8e113990a9394ea495c5e5e3be2ebbd26ea63dacc0e")
  .addHeader("ACCESS-TIMESTAMP", "2022-01-08T07:19:56.339Z")
  .build();
Response response = client.newCall(request).execute();
```

```javascript
var settings = {
  "url": "${host}/v1/accounts",
  "method": "GET",
  "timeout": 0,
  "headers": {
    "ACCESS-KEY": "HKBGE-0d7f7a3ba656a73c38295ad879779e16",
    "ACCESS-SIGN": "a3ef844e35289b3af63bd8e113990a9394ea495c5e5e3be2ebbd26ea63dacc0e",
    "ACCESS-TIMESTAMP": "2022-01-08T07:19:56.339Z"
  },
};

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

```python
import http.client

conn = http.client.HTTPSConnection("${host}")
payload = ''
headers = {
  'ACCESS-KEY': 'HKBGE-0d7f7a3ba656a73c38295ad879779e16',
  'ACCESS-SIGN': 'a3ef844e35289b3af63bd8e113990a9394ea495c5e5e3be2ebbd26ea63dacc0e',
  'ACCESS-TIMESTAMP': '2022-01-08T07:19:56.339Z'
}
conn.request("GET", "/v1/accounts", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => '${host}/v1/accounts',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
  CURLOPT_HTTPHEADER => array(
    'ACCESS-KEY: HKBGE-0d7f7a3ba656a73c38295ad879779e16',
    'ACCESS-SIGN: a3ef844e35289b3af63bd8e113990a9394ea495c5e5e3be2ebbd26ea63dacc0e',
    'ACCESS-TIMESTAMP: 2022-01-08T07:19:56.339Z'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

```

```go
package main

import (
  "fmt"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "${host}/v1/accounts"
  method := "GET"

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("ACCESS-KEY", "HKBGE-0d7f7a3ba656a73c38295ad879779e16")
  req.Header.Add("ACCESS-SIGN", "a3ef844e35289b3af63bd8e113990a9394ea495c5e5e3be2ebbd26ea63dacc0e")
  req.Header.Add("ACCESS-TIMESTAMP", "2022-01-08T07:19:56.339Z")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

<aside>
RESPONSE STATUS
</aside>

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request | [参考示例](#ResonpseExample1)
401 | Unauthorized -- Your API key is wrong, See [鉴权说明](#auth) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

| 参数名称 | 参数说明 | 类型 | schema |
| -------- | -------- | ----- |----- | 
|available|可用额度|string||
|hold|冻结额度|string||
|balance|余额,包含 可用额度为冻结额度之和|string||
|currency|资产名称|string||

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
[
  {
    "available": "10.0001",
    "balance": "11.0001",
    "currency": "BTC",
    "hold": "1.0"
  }
]
```


## 获取单个账户余额信息


<font class="httpget">GET</font> */v1/accounts/{currency}*


获取用户指定的交易账户信息

**冻结账户**

当用户下单完成，自己会被划拨到冻结账户。被划拨到冻结账户的资金不能被用于其他交易，以及提现操作。当订单成交或被取消，冻结账户的资金会被释放。


<aside>
REQUEST PARAMETERS
</aside>

| 参数名称 | 参数说明 | 是否必须 | 数据类型 | schema |
| -------- | -------- | -------- | -------- | ------ |
|currency|资产名称，例:BTC||true|string||


> 鉴权信息

> 私有信息的鉴权信息，请参考 [鉴权说明](#auth)

<aside>
RESPONSE STATUS
</aside>

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request | [参考示例](#ResonpseExample1)
401 | Unauthorized -- Your API key is wrong, See [鉴权说明](#auth) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

| 参数名称 | 参数说明 | 类型 | schema |
| -------- | -------- | ----- |----- | 
|available|可用额度|string||
|hold|冻结额度|string||
|balance|余额,包含 可用额度为冻结额度之和|string||
|currency|资产名称|string||

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
{
  "available": "10.0001",
  "balance": "11.0001",
  "currency": "BTC",
  "hold": "1.0"
}
```

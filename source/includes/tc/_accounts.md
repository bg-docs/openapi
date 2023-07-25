# 賬戶信息

## 獲取所有賬戶餘額信息

<font class="httpget">GET</font> */v1/accounts*


獲取用戶所有的交易賬戶信息

**凍結賬戶**

當用戶下單完成，自己會被劃撥到凍結賬戶。被劃撥到凍結賬戶的資金不能被用於其他交易，以及提現操作。當訂單成交或被取消，凍結賬戶的資金會被釋放。

> 鑑權信息

> 私有信息的鑑權信息，請參考 [鑑權說明](#auth)

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
RESPONSE PARAMETERS
</aside>

| 參數名稱 | 參數說明 | 類型 | schema |
| -------- | -------- | ----- |----- | 
|available|可用額度|string||
|hold|凍結額度|string||
|balance|餘額,包含 可用額度為凍結額度之和|string||
|currency|資產名稱|string||

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


## 獲取單個賬戶餘額信息


<font class="httpget">GET</font> */v1/accounts/{currency}*


獲取用戶指定的交易賬戶信息

**凍結賬戶**

當用戶下單完成，自己會被劃撥到凍結賬戶。被劃撥到凍結賬戶的資金不能被用於其他交易，以及提現操作。當訂單成交或被取消，凍結賬戶的資金會被釋放。


<aside>
REQUEST PARAMETERS
</aside>

| 參數名稱 | 參數說明 | 是否必須 | 數據類型 | schema |
| -------- | -------- | -------- | -------- | ------ |
|currency|資產名稱，例:BTC||true|string||


> 鑑權信息

> 私有信息的鑑權信息，請參考 [鑑權說明](#auth)

 
<aside>
RESPONSE PARAMETERS
</aside>

| 參數名稱 | 參數說明 | 類型 | schema |
| -------- | -------- | ----- |----- | 
|available|可用額度|string||
|hold|凍結額度|string||
|balance|餘額,包含 可用額度為凍結額度之和|string||
|currency|資產名稱|string||

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
{
  "available": "10.0001",
  "balance": "11.0001",
  "currency": "BTC",
  "hold": "1.0"
}
```

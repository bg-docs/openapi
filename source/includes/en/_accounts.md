# Account information

## Obtaining all account balance information

<font class="httpget">GET</font> */v1/accounts*


Obtaining all transaction account information of the user

**Unavailable balance**

After the user finishes placing an order, it will be assigned to the unavailable balance. Funds assigned to the unavailable balance cannot be used in other transactions or withdrawal operations. When the order is closed or cancelled, the funds assigned to the unavailable balance will be released.

> Authentication information

> For the authentication information of private information, please refer to [Authentication Specifications](#Authentication Specifications)

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
200 | Success Request | [Examples](#ResonpseExample1)
401 | Unauthorized -- Your API key is wrong, See [Authentication Specifications](#Authentication Specifications) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

| Parameter Name | Parameter Description | Type | schema |
| -------- | -------- | ----- |----- | 
|available|Available balance|string||
|hold|Unavailable balance|string||
|balance|Balance, including the sum of available and on-hold credits|string||
|currency|Asset name|string||

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


## Obtaining all account balance information


<font class="httpget">GET</font> */v1/accounts/{currency}*


Obtaining transaction account information specified by the user

**On-hold Account**

After the user finishes placing an order, it will be assigned to the On-hold Account. Funds assigned to the On-hold Account cannot be used in other transactions or withdrawal operations. When the order is closed or cancelled, the funds in the On-hold Account will be released.


<aside>
REQUEST PARAMETERS
</aside>

| Parameter Name | Parameter Description | Mandatory  | Data Type | schema |
| -------- | -------- | -------- | -------- | ------ |
|currency|Asset name, e.g. BTC||true|string||


> Authentication information

> For the authentication information of private information, please refer to [Authentication Specifications](#Authentication Specifications)

<aside>
RESPONSE STATUS
</aside>

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request | [Examples](#ResonpseExample1)
401 | Unauthorized -- Your API key is wrong, See [Authentication Specifications](#Authentication Specifications) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

| Parameter Name | Parameter Description | Type | schema |
| -------- | -------- | ----- |----- | 
|available|Available balance|string||
|hold|Unavailable balance|string||
|balance|Balance, including the sum of available and on-hold credits|string||
|currency|Asset name|string||

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
{
  "available": "10.0001",
  "balance": "11.0001",
  "currency": "BTC",
  "hold": "1.0"
}
```

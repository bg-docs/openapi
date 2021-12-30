# Products

##  Candles

```python
python -m pip install requests

import requests

url = "{host}/products/BTC_USDT/candles"

headers = {"Accept": "application/json"}

response = requests.request("GET", url, headers=headers)

print(response.text)

```

```javascript
// npm install node-fetch
const fetch = require("node-fetch")
fetch("{host}/products/BTC_USDT/candles")
    .then(res => console.log(res.json()))
    .catch(err => console.log(err))
```

```php
// composer require guzzlehttp/guzzle
<?php

require_once('vendor/autoload.php');

$client = new \GuzzleHttp\Client();

$response = $client->request('GET', '{host}/products/BTC_USDT/candles', [
  'headers' => [
    'Accept' => 'application/json',
  ],
]);

echo $response->getBody();
```


```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("{host}/products/BTC_USDT/candles")
  .get()
  .addHeader("Accept", "application/json")
  .build();

Response response = client.newCall(request).execute();
```

```golang
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "{host}/products/BTC_USDT/candles"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Accept", "application/json")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```
<font style="background-color: #0e9b71;text-shadow:1px 1px 0px #0d8d67, 0 1px 0 #0d8d67, 1px 0 0 #0d8d67;border-radius:5px;padding:5px">GET</font> */product/{product_id}/candles*

历史产品的k 线图， 数据以数组形式返回，每个对象保函[`close`，`count`，`high`，`low`，`open`，`turnOver`，`vol`]

#### 请求参数

|参数名| 必选  |类型|                                                                                                                                                              说明                                                                                                                                                               |
|:----    |:----|:----- |:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| product_id | 是   |string |                                                                                                                                                              交易对                                                                                                                                                              |
| interval | 是   |string | *指标周期*  <br/> [ <font color="red">"1min"</font>, <font color="red">"5min"</font>, <font color="red">"15min"</font>, <font color="red">"30min"</font>, <font color="red">"60min"</font>, <font color="red">"4hour"</font>, <font color="red">"1day"</font>, <font color="red">"1week"</font>, <font color="red">"1mon"</font>] |
|start     | 是   |string |                                                                                                                                                           开始  (毫秒)                                                                                                                                                            |
|end     | 是   |string |                                                                                                                                                           结束   (毫秒)                                                                                                                                                           |
|size     | 是   |string |                                                                                                                                                        数据长度  [1,2000]                                                                                                                                                         |


##### 返回参数
| Status | Meaning                                                 | Description |Schema|
|--------|---------------------------------------------------------|-------------|---|
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | OK          |Inline|
| 500      | [SERVER_ERROR](https://tools.ietf.org/html/rfc7235#section-3.1)    | Server Error            |None|


> response

```json 
  {
    "code": 200,
    "data": [
        {
            "close": 11.9,
            "count": 2,
            "high": 11.9,
            "id": 1639584000,
            "low": 11,
            "open": 11,
            "turnOver": 22.9,
            "vol": 2
        }
    ],
    "interval": "1day",
    "msg": "success",
    "productId": "ETH_USDT",
    "ts": 1639650753079
}

```


## OrderBook


```python
python -m pip install requests

import requests

url = "{host}/products/BTC_USDT/orderbook"

headers = {"Accept": "application/json"}

response = requests.request("GET", url, headers=headers)

print(response.text)

```


```javascript
// npm install node-fetch
const fetch = require("node-fetch")
fetch("{host}/products/BTC_USDT/orderbook")
    .then(res => console.log(res.json()))
    .catch(err => console.log(err))
``` 

```php
// composer require guzzlehttp/guzzle
<?php

require_once('vendor/autoload.php');

$client = new \GuzzleHttp\Client();

$response = $client->request('GET', '{host}/products/BTC_USDT/orderbook', [
  'headers' => [
    'Accept' => 'application/json',
  ],
]);

echo $response->getBody();
```

 
```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("{host}/products/BTC_USDT/orderbook")
  .get()
  .addHeader("Accept", "application/json")
  .build();

Response response = client.newCall(request).execute();
```



```golang
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "{host}/products/BTC_USDT/orderbook"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Accept", "application/json")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

<font style="background-color: #0e9b71;text-shadow:1px 1px 0px #0d8d67, 0 1px 0 #0d8d67, 1px 0 0 #0d8d67;border-radius:5px;padding:5px">GET</font> */product/{product_id}/orderbook*

Get a list of open orders for a product. The amount of detail shown can be customized with the level parameter.

#### 请求参数


|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| product_id |是  |string |    |
| interval | 是   |string | *指标周期*  <br/> [ <font color="red">"1min"</font>, <font color="red">"5min"</font>, <font color="red">"15min"</font>, <font color="red">"30min"</font>, <font color="red">"60min"</font>, <font color="red">"4hour"</font>, <font color="red">"1day"</font>, <font color="red">"1week"</font>, <font color="red">"1mon"</font>] |


##### 返回参数
| Status | Meaning                                                 | Description |Schema|
|--------|---------------------------------------------------------|-------------|---|
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | OK          |Inline|
| 500      | [SERVER_ERROR](https://tools.ietf.org/html/rfc7235#section-3.1)    | Server Error            |None|

> response

```json 
{
    "interval": "1min",
    "status": "ok",
    "ts": 1639651867084,
    "type": "orderBook",
    "tick":
}

```

## Overview


```python
python -m pip install requests

import requests

url = "{host}/products/BTC_USDT/tickers"

headers = {"Accept": "application/json"}

response = requests.request("GET", url, headers=headers)

print(response.text)

```


```javascript
// npm install node-fetch
const fetch = require("node-fetch")
fetch("{host}/products/BTC_USDT/tickers")
    .then(res => console.log(res.json()))
    .catch(err => console.log(err))
``` 

```php
// composer require guzzlehttp/guzzle
<?php

require_once('vendor/autoload.php');

$client = new \GuzzleHttp\Client();

$response = $client->request('GET', '{host}/products/BTC_USDT/tickers', [
  'headers' => [
    'Accept' => 'application/json',
  ],
]);

echo $response->getBody();
```


```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("{host}/products/BTC_USDT/tickers")
  .get()
  .addHeader("Accept", "application/json")
  .build();

Response response = client.newCall(request).execute();
```



```golang
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "{host}/products/BTC_USDT/tickers"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Accept", "application/json")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

<font style="background-color: #0e9b71;text-shadow:1px 1px 0px #0d8d67, 0 1px 0 #0d8d67, 1px 0 0 #0d8d67;border-radius:5px;padding:5px">GET</font> */products/{product_id}/tickers*

Gets snapshot information about the trade (tick), best bid/ask and 24h volume.


##### 参数

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| product_id |是  |string | 交易对   |

##### 返回参数说明

|参数名|类型|说明|
|:------:|:----:|:------------------------------:|
| close | int  | 收盘  |
| count | int  | |
| high | int  | 最高  |
| id |  int  |  |
| low | int  | 最低  |
| open | int  | 开盘价  |
| turnOver | string  | 交易量  |
| vol | string  | 交易额  |

>response

```json
 {
    "type": "overview",
    "code": 200,
    "ts": 1639655064896,
    "msg": "success",
    "data": [
        {
            "open": "11",
            "close": "11.9",
            "low": "11",
            "high": "11.9",
            "turnOver": "22.9",
            "count": 0,
            "vol": "2",
            "pairCode": "ETH_USDT",
            "change": "0.9",
            "changePercent": "0.0818181818181818"
        },
        {
            "open": "180",
            "close": "206",
            "low": "100",
            "high": "1018",
            "turnOver": "109265.599912",
            "count": 0,
            "vol": "862.052512",
            "pairCode": "BTC_USDT",
            "change": "26",
            "changePercent": "0.1444444444444444"
        }
    ]
}
```

## Ticker


```python
python -m pip install requests

import requests

url = "{host}/products/BTC_USDT/ticker"

headers = {"Accept": "application/json"}

response = requests.request("GET", url, headers=headers)

print(response.text)

```


```javascript
// npm install node-fetch
const fetch = require("node-fetch")
fetch("{host}/products/BTC_USDT/ticker")
    .then(res => console.log(res.json()))
    .catch(err => console.log(err))
``` 

```php
// composer require guzzlehttp/guzzle
<?php

require_once('vendor/autoload.php');

$client = new \GuzzleHttp\Client();

$response = $client->request('GET', '{host}/products/BTC_USDT/ticker', [
  'headers' => [
    'Accept' => 'application/json',
  ],
]);

echo $response->getBody();
```


```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("{host}/products/BTC_USDT/ticker")
  .get()
  .addHeader("Accept", "application/json")
  .build();

Response response = client.newCall(request).execute();
```



```golang
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "{host}/products/BTC_USDT/ticker"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Accept", "application/json")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

<font style="background-color: #0e9b71;text-shadow:1px 1px 0px #0d8d67, 0 1px 0 #0d8d67, 1px 0 0 #0d8d67;border-radius:5px;padding:5px">GET</font> */products/{product_id}/ticker*

Gets snapshot information about the last trade (tick), best bid/ask and 24h volume.

##### 参数

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| product_id |是  |string | 交易对   |

> response

```json
{
    "ch": "market.BTC_USDT.detail",
    "status": "ok",
    "tick": {
        "open": "180",
        "close": "206",
        "low": "100",
        "high": "1018",
        "turnOver": "109265.599912",
        "count": 0,
        "vol": "862.052512",
        "pairCode": "BTC_USDT",
        "change": "26",
        "changePercent": "0.1444444444444444"
    },
    "ts": 1639654376827
}
```

##### 数据体参数说明

|参数名|类型|说明|
|:-----  |:-----|-----                           |
| close |int   | 收盘  |
| count |int   | |
| high |int   | 最高  |
| id | int   |  |
| low |int   | 最低  |
| open |int   | 开盘价  |
| turnOver |string   | 交易量  |
| vol |string   | 交易额  |



## Trade

```python
python -m pip install requests

import requests

url = "{host}/products/BTC_USDT/trade"

headers = {"Accept": "application/json"}

response = requests.request("GET", url, headers=headers)

print(response.text)

```


```javascript
// npm install node-fetch
const fetch = require("node-fetch")
fetch("{host}/products/BTC_USDT/trade")
    .then(res => console.log(res.json()))
    .catch(err => console.log(err))
``` 

```php
// composer require guzzlehttp/guzzle
<?php

require_once('vendor/autoload.php');

$client = new \GuzzleHttp\Client();

$response = $client->request('GET', '{host}/products/BTC_USDT/trade', [
  'headers' => [
    'Accept' => 'application/json',
  ],
]);

echo $response->getBody();
```


```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("{host}/products/BTC_USDT/trade")
  .get()
  .addHeader("Accept", "application/json")
  .build();

Response response = client.newCall(request).execute();
```



```golang
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "{host}/products/BTC_USDT/trade"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Accept", "application/json")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

<font style="background-color: #0e9b71;text-shadow:1px 1px 0px #0d8d67, 0 1px 0 #0d8d67, 1px 0 0 #0d8d67;border-radius:5px;padding:5px">GET</font> */products/{product_id}/trade*

Gets a list the latest trades for a product.

##### 参数

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| product_id |是  |string | 交易对   |


> response

```json 
{
    "status": "ok",
    "tick": {
        "data": [
            {
                "direction": "buy",
                "id": 45120000,
                "price": "100",
                "ts": 1639648687668,
                "vol": "2"
            }
        ],
        "id": 1639652116290,
        "ts": 1639652116290
    },
    "ts": 1639652116290
}
```

##### 返回参数说明

|参数名|类型|说明|
|:-----  |:-----|-----                           |
| direction |string   |  |
| price |string   |  价格 |
| vol |string   |  成交量 |

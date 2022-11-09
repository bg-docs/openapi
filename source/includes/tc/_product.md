##  Candles

```python
python -m pip install requests

import requests

url = "{host}/public/v1/products/BTC_USDT/candles?period=1day&size=50&start=1539651867084&end=1639651867084"

headers = {"Accept": "application/json"}

response = requests.request("GET", url, headers=headers)

print(response.text)

```

```javascript
// npm install node-fetch
const fetch = require("node-fetch")
fetch("{host}/public/v1/products/BTC_USDT/candles?period=1day&size=50&start=1539651867084&end=1639651867084")
    .then(res => console.log(res.json()))
    .catch(err => console.log(err))
```

```php
// composer require guzzlehttp/guzzle
<?php

require_once('vendor/autoload.php');

$client = new \GuzzleHttp\Client();

$response = $client->request('GET', '{host}/public/v1/products/BTC_USDT/candles?period=1day&size=50&start=1539651867084&end=1639651867084', [
  'headers' => [
    'Accept' => 'application/json',
  ],
]);

echo $response->getBody();
```


```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("{host}/public/v1/products/BTC_USDT/candles?period=1day&size=50&start=1539651867084&end=1639651867084")
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

	url := "{host}/public/v1/products/BTC_USDT/candles?period=1day&size=50&start=1539651867084&end=1639651867084"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Accept", "application/json")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```
<font class="httpget">GET</font> */public/v1/products/{product}/candles*

歷史產品的k 線圖， 數據以數組形式返回，每個對象保函[`close`，`count`，`high`，`low`，`open`，`turnOver`，`vol`]

#### 請求參數

|參數名| 必選  |類型|                                                                                                                                                                說明                                                                                                                                                                |
|:----    |:----|:----- |:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| product | 是   |string |                                                                                          幣對                                                                                                                                         交易對                                                                                          |
| period | 是   |string | *指標週期*  <br/> [ <font color="red">"step0"</font>, <font color="red">"step5"</font>, <font color="red">"step10"</font>, <font color="red">"30min"</font>, <font color="red">"60min"</font>, <font color="red">"4hour"</font>, <font color="red">"1day"</font>, <font color="red">"1week"</font>, <font color="red">"1mon"</font>] |
|start     | 是   |string |                                                                               timestamp 毫秒                                                                                                                                                開始  (毫秒)                                                                               |
|end     | 是   |string |                                                                                                                                                            結束   (毫秒)                                                                                                                                                             |
|size     | 是   |string |                                                                          [1,2000]                                                                                                                                                       數據長度  [1,2000]                                                                           |


##### 返回參數
|參數名|類型|   說明 |
|:------:|:----:|:--:|
| close | int  |   收盤價格 |
| high | int  |   最高價格 |
| low | int  |   最低價格 |
| open | int  |  開盤價格 |
| turnOver | string  |  交易量 |
| vol | string  |  交易額 |
| pairCode | string  |  幣對  |


| Status | Meaning                                                 | Description |Schema|
|--------|---------------------------------------------------------|-------------|---|
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | OK          |Inline|
| 500      | [SERVER_ERROR](https://tools.ietf.org/html/rfc7235#section-3.1)    | Server Error            |None|


> response

```json 
  {
    "code": 200,
    "data": [
        {"close": 11.9,
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

url = "{host}/public/v1/products/BTC_USDT/orderbook?interval=step5"

headers = {"Accept": "application/json"}

response = requests.request("GET", url, headers=headers)

print(response.text)

```


```javascript
// npm install node-fetch
const fetch = require("node-fetch")
fetch("{host}/public/v1/products/BTC_USDT/orderbook?interval=step5")
    .then(res => console.log(res.json()))
    .catch(err => console.log(err))
``` 

```php
// composer require guzzlehttp/guzzle
<?php

require_once('vendor/autoload.php');

$client = new \GuzzleHttp\Client();

$response = $client->request('GET', '{host}/public/v1/products/BTC_USDT/orderbook?interval=step5', [
  'headers' => [
    'Accept' => 'application/json',
  ],
]);

echo $response->getBody();
```


```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("{host}/public/v1/products/BTC_USDT/orderbook?interval=step5")
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

	url := "{host}/public/v1/products/BTC_USDT/orderbook?interval=step5"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Accept", "application/json")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

<font class="httpget">GET</font> */public/v1/products/{product}/orderbook*

Get a list of open orders for a product. The amount of detail shown can be customized with the level parameter.

#### 請求參數


|參數名|必選|類型| 說明                                                                                |
|:----    |:---|:----- |-----------------------------------------------------------------------------------|
| product |是  |string |                                                                                   |
| interval | 是   |string | *指標週期*  <br/> step [ <font color="red">"1"</font>, <font color="red">"11"</font>] |


##### 返回參數
| Status | Meaning                                                 | Description |Schema|
|--------|---------------------------------------------------------|-------------|---|
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | OK          |Inline|
| 500      | [SERVER_ERROR](https://tools.ietf.org/html/rfc7235#section-3.1)    | Server Error            |None|

> response

```json 
{
	"interval": "step1",
	"status": "ok",
	"ts": 1641378313942,
	"type": "orderBook",
	"tick": {
		"seqId": 9996,
		"id": 1641378313,
		"bids": [
			[1, 65]
		],
		"asks": [
			[48349.99, 5.3795],
			[48562.27, 94.1076],
			[48998.82, 49.924],
			[49322.83, 15.03636],
			[49324.72, 8.1281],
			[49334.76, 82.7552],
			[49342.59, 44.9204],
			[49364.66, 28.5769],
			[49365.2, 6.2237],
			[49390.8, 44.7102],
			[49414.67, 92.3859],
			[49428.24, 46.7245],
			[49430.6, 66.2994],
			[49435.96, 68.4281],
			[49437.07, 20.5226],
			[49443.47, 51.3443],
			[49444.4, 73.2709],
			[49448.78, 41.5535],
			[49454.19, 77.954],
			[49458.74, 29.2196],
			[49477.83, 50.3074],
			[49492.03, 93.2679],
			[49500.02, 11.1431],
			[49506.89, 74.3294],
			[49519.14, 45.8255],
			[49525.62, 19.6835],
			[49538.88, 97.1741],
			[49544.83, 70.238],
			[49551.81, 38.3689],
			[49557.84, 69.0679],
			[49565.77, 55.5486],
			[49571.15, 55.1521],
			[49589.14, 83.2236],
			[49590.11, 1.5069],
			[49593.9, 45.1853],
			[49601.42, 21.826],
			[49602.74, 2.7914],
			[49609.3, 79.3817],
			[49615.55, 81.7304],
			[49653.07, 12.2331],
			[49662.5, 68.8741],
			[49675.13, 31.3474],
			[49686.03, 6.1158],
			[49690.92, 79.5905],
			[49699.37, 91.9541],
			[49719.33, 80.5142],
			[49724.29, 61.7956],
			[49726.37, 96.1342],
			[49752.36, 71.4982],
			[49769.78, 49.3641],
			[49785.77, 43.4184],
			[49815.95, 91.9892],
			[49820.16, 74.1338],
			[49847.76, 20.297],
			[49888.07, 76.3738],
			[49888.44, 8.6581],
			[49907.97, 12.634],
			[49932.43, 63.1484],
			[49951.37, 5.0352],
			[49952.08, 81.9681],
			[49958.58, 99.3703],
			[49977.74, 62.3056],
			[49986.53, 34.2252],
			[49998.03, 47.7642],
			[49998.3, 88.6624]
		],
		"ts": 1641378313486,
		"version": 1641378313,
		"type": "orderBook",
		"pairCode": "BTC_USDT",
		"interval": "1"
	}
}

```

## Tickers

行情總覽

```python
python -m pip install requests

import requests

url = "{host}/public/v1/products/BTC_ETH/tickers"

headers = {"Accept": "application/json"}

response = requests.request("GET", url, headers=headers)

print(response.text)

```


```javascript
// npm install node-fetch
const fetch = require("node-fetch")
fetch("{host}/public/v1/products/BTC_ETH/tickers")
    .then(res => console.log(res.json()))
    .catch(err => console.log(err))
``` 

```php
// composer require guzzlehttp/guzzle
<?php

require_once('vendor/autoload.php');

$client = new \GuzzleHttp\Client();

$response = $client->request('GET', '{host}/public/v1/products/BTC_ETH/tickers', [
  'headers' => [
    'Accept' => 'application/json',
  ],
]);

echo $response->getBody();
```


```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("{host}/public/v1/products/BTC_ETH/tickers")
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

	url := "{host}/public/v1/products/BTC_ETH/tickers"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Accept", "application/json")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

<font class="httpget">GET</font> */public/v1/products/{product}/tickers*

Gets snapshot information about the trade (tick), best bid/ask and 24h volume.


##### 參數

| 參數名     |必選|類型|說明|
|:--------|:---|:----- |-----   |
| product |是  |string | 交易對   |

##### 返回參數說明

|參數名|類型|   說明 |
|:------:|:----:|:--:|
| close | int  |   收盤價格 |
| high | int  |   最高價格 |
| low | int  |   最低價格 |
| open | int  |  開盤價格 |
| turnOver | string  |  交易量 |
| vol | string  |  交易額 |
| pairCode | string  |  幣對  |

>response

```json
 {
  "type": "overview",
  "code": 200,
  "ts": 1641378730830,
  "msg": "success",
  "data": [{
    "open": "19.56",
    "close": "48174.19",
    "low": "1",
    "high": "54969.49",
    "turnOver": "2397481368.57161866",
    "count": 0,
    "vol": "49659.154689",
    "pairCode": "BTC_USDT",
    "change": "48154.63",
    "changePercent": "2461.8931492842535787"
  }, {
    "open": "11.9",
    "close": "11.9",
    "low": "11.9",
    "high": "11.9",
    "turnOver": "0",
    "count": 0,
    "vol": "0",
    "pairCode": "ETH_USDT",
    "change": "0",
    "changePercent": "0"
  }]
}
```

## Ticker


```python
python -m pip install requests

import requests

url = "{host}/public/v1/products/ETH_USDT/ticker"

headers = {"Accept": "application/json"}

response = requests.request("GET", url, headers=headers)

print(response.text)

```


```javascript
// npm install node-fetch
const fetch = require("node-fetch")
fetch("{host}/public/v1/products/ETH_USDT/ticker")
    .then(res => console.log(res.json()))
    .catch(err => console.log(err))
``` 

```php
// composer require guzzlehttp/guzzle
<?php

require_once('vendor/autoload.php');

$client = new \GuzzleHttp\Client();

$response = $client->request('GET', '{host}/public/v1/products/ETH_USDT/ticker', [
  'headers' => [
    'Accept' => 'application/json',
  ],
]);

echo $response->getBody();
```


```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("{host}/public/v1/products/ETH_USDT/ticker")
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

	url := "{host}/public/v1/products/ETH_USDT/ticker"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Accept", "application/json")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

<font class="httpget">GET</font> */public/v1/products/{product}/ticker*

Gets snapshot information about the last trade (tick), best bid/ask and 24h volume.

##### 參數

| 參數名     |必選|類型| 說明  |
|:--------|:---|:----- |-----|
| product |是  |string | 幣對  |

> response

```json
{
  "ch": "market.ETH_USDT.detail",
  "status": "ok",
  "tick": {
    "open": "11.9",
    "close": "11.9",
    "low": "11.9",
    "high": "11.9",
    "turnOver": "0",
    "count": 0,
    "vol": "0",
    "pairCode": "ETH_USDT",
    "change": "0",
    "changePercent": "0"
  },
  "ts": 1641378912756
}
```

##### 數據體參數說明

|參數名|類型| 說明   |
|:-----  |:-----|------|
| close |int   | 收盤價格 |
| high |int   | 最高價格   |
| low |int   | 最低價格   |
| open |int   | 開盤價格  |
| turnOver |string   | 交易量  |
| vol |string   | 交易額  |



## Trade

```python
python -m pip install requests

import requests

url = "{host}/public/v1/products/ETH_USDT/trade"

headers = {"Accept": "application/json"}

response = requests.request("GET", url, headers=headers)

print(response.text)

```


```javascript
// npm install node-fetch
const fetch = require("node-fetch")
fetch("{host}/public/v1/products/ETH_USDT/trade")
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
  .url("{host}/public/v1/products/ETH_USDT/trade")
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

	url := "{host}/public/v1/products/ETH_USDT/trade"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Accept", "application/json")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

<font class="httpget">GET</font> */public/v1/products/{product}/trade*

Gets a list the latest trades for a product.

##### 參數

| 參數名     |必選|類型|說明|
|:--------|:---|:----- |-----   |
| product |是  |string | 交易對   |


> response

```json 
{
	"status": "ok",
	"tick": {
		"data": [{
			"direction": "sell",
			"id": 28730000,
			"price": "11.9",
			"ts": 1639585820376,
			"vol": "1"
		}],
		"id": 1641379110358,
		"ts": 1641379110358
	},
	"ts": 1641379110358
}
```

##### 返回參數說明

|參數名|類型| 說明         |
|:-----  |:-----|------------|
| direction |string   | buy / sell |
| price |string   | 價格         |
| vol |string   | 成交量        |

----


## Trades

```python
python -m pip install requests

import requests

url = "{host}/public/v1/products/ETH_USDT/trades?size=10"

headers = {"Accept": "application/json"}

response = requests.request("GET", url, headers=headers)

print(response.text)

```


```javascript
// npm install node-fetch
const fetch = require("node-fetch")
fetch("{host}/public/v1/products/ETH_USDT/trades?size=10")
    .then(res => console.log(res.json()))
    .catch(err => console.log(err))
``` 

```php
// composer require guzzlehttp/guzzle
<?php

require_once('vendor/autoload.php');

$client = new \GuzzleHttp\Client();

$response = $client->request('GET', '{host}/public/v1/products/ETH_USDT/trades?size=10', [
  'headers' => [
    'Accept' => 'application/json',
  ],
]);

echo $response->getBody();
```


```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("{host}/public/v1/products/ETH_USDT/trades?size=10")
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

	url := "{host}/public/v1/products/ETH_USDT/trades?size=10"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("Accept", "application/json")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

<font class="httpget">GET</font> */public/v1/products/{product}/trades*

Gets a list the latest trades for a product.

##### 參數

| 參數名     |必選| 類型     | 說明   |
|:--------|:---|:-------|------|
| product |是  | string | 交易對  |
| size       |是  | int      | 數據長度 |

> response

```json 
{
	"data": [{
		"data": [{
			"direction": "buy",
			"id": 28470000,
			"price": "11",
			"ts": 1639585820373,
			"vol": "1"
		}],
		"id": 2847,
		"ts": 1639585820373,
		"type": "fills"
	}, {
		"data": null,
		"id": 2871,
		"ts": 1639585820376,
		"type": "fills"
	}, {
		"data": [{
			"direction": "sell",
			"id": 28730000,
			"price": "11.9",
			"ts": 1639585820376,
			"vol": "1"
		}],
		"id": 2873,
		"ts": 1639585820376,
		"type": "fills"
	}],
	"status": "ok",
	"ts": 1641379702364
}
```

##### 返回參數說明

|參數名|類型| 說明         |
|:-----  |:-----|------------|
| direction |string   | buy / sell |
| price |string   | 價格         |
| vol |string   | 成交量        |

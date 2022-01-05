# WEBSOCKET FEED

- ` {host}/ws`

## Candles Subscribe/UnSubscribe 

#### Subscribe

> request

```json
	{
		"event": "sub",
		"params": {
			"biz": "market",
			"type": "candles",
			"pairCode": "ETH_BNB",
			"interval": "1day"
		},
		"zip":false
	}	
```

#### 请求参数

|参数名|必选|类型| 说明   |
|:----    |:---|:----- |------|
| params .biz | 是  |string |      |
| params .type     |是  |string | 订阅类型类型 |
| params .pairCode     |是  |string | 币对   |
| params .interval     |是  |string | 周期   |
| event     |是  |string | 事件 Subscribe  |
| zip     |是  |bool | 是否启用gzip |


> response

```json
{
	"id": "",
	"channel": "subscribe",
	"biz": "market",
	"type": "candles",
	"pairCode": "ETH_BNB",
	"interval": "1day",
	"ts": 1639655425910,
	"status": "ok"
}
```

#### 返回参数
|参数名|类型|说明|
|:----    |:----- |-----   |
| type | string |  订阅类型 |
| interval     |string | 间隔  |
| pairCode    |string | 币对|
| data .open     |string | 开盘 |
| data .close    |string | 收盘 |
| data .low     |string | 低 |
| data .high     |string | 高 |
| data .vol     |string | 成交 |
| data .turnOver     |string | 成交量 |
| data .count     |string |  |


#### UnSubscribe

> request

```json
	{
		"event": "unsub",
		"params": {
			"biz": "market",
			"type": "candles",
			"pairCode": "ETH_BNB",
			"interval": "1day"
		},
		"zip":true
	}	
```

#### 请求参数

|参数名|必选|类型| 说明            |
|:----    |:---|:----- |---------------|
| params .biz | 是  |string |               |
| params .type     |是  |string | 订阅类型类型        |
| params .pairCode     |是  |string | 币对            |
| params .interval     |是  |string | 周期            |
| event     |是  |string | 事件 UnSubscribe |
| zip     |是  |bool | 是否启用gzip      |


> response

```json
{
	"id": "",
	"channel":"unsubscribe",
	"biz": "market",
	"type": "candles",
	"pairCode": "ETH_BNB",
	"interval": "1day",
	"ts": 1639655425910,
	"status": "ok"
}
```

#### 返回参数
|参数名|类型|说明|
|:----    |:----- |-----   |
| type | string |  订阅类型 |
| interval     |string | 间隔  |
| pairCode    |string | 币对|
| data .open     |string | 开盘 |
| data .close    |string | 收盘 |
| data .low     |string | 低 |
| data .high     |string | 高 |
| data .vol     |string | 成交 |
| data .turnOver     |string | 成交量 |
| data .count     |string |  |



#### FEED 


```json

{
	"id": "his",
	"type": "candles",
	"pairCode": "ETH_USDT",
	"interval": "1day",
	"data": [{
		"id": 1639584000,
		"open": 11,
		"close": 11.9,
		"low": 11,
		"high": 11.9,
		"vol": 2,
		"turnOver": 22.9,
		"count": 2
	}, {
		"id": 1639670400,
		"open": 11.9,
		"close": 11.9,
		"low": 11.9,
		"high": 11.9,
		"vol": 0,
		"turnOver": 0,
		"count": 0
	}]
}

```
----

##  Fills Subscribe/UnSubscribe

#### Subscribe


```json
{
  "event": "sub",
  "params": {
    "biz": "market",
    "type": "fills",
    "pairCode": "ETH_USDT"
  },
  "zip": false
}
```


|参数名|必选|类型| 说明       |
|:----    |:---|:----- |----------|
| params .biz | 是  |string |          |
| params .type     |是  |string | 订阅类型类型   |
| params .pairCode     |是  |string | 币对       |
| params .interval     |是  |string | 周期       |
| event     |是  |string | 事件 Subscribe      |
| zip     |是  |bool | 是否启用gzip |



```json
{
  "id": "",
  "channel": "subscribe",
  "biz": "market",
  "type": "fills",
  "pairCode": "ETH_USDT",
  "interval": "",
  "ts": 1641384262679,
  "status": "ok"
}
```

#### UnSubscribe

|参数名|必选|类型| 说明       |
|:----    |:---|:----- |----------|
| params .biz | 是  |string |          |
| params .type     |是  |string | 订阅类型类型   |
| params .pairCode     |是  |string | 币对       |
| params .interval     |是  |string | 周期       |
| event     |是  |string | 事件 Subscribe      |
| zip     |是  |bool | 是否启用gzip |

```json

{
	"event": "unsub",
	"params": {
		"biz": "market",
		"type": "fills",
		"pairCode": "ETH_USDT"
	},
	"zip": false
}

```


```json
{
	"id": "",
	"unsubbed": "market.ETH_USDT.trade.detail",
	"ts": 1641384470335,
	"status": "ok"
}
```
#### FEED 

|参数名|类型|说明|
|:----    |:---|:----- |-----   |
| type | string |  订阅类型 |
| interval     |string | 间隔  |
| pairCode    |string | 币对|
| data .price     |string | 价格 |
| data .vol     |string | 成交 |
| data .ts     |int  | 时间戳 |
| data .direction     |string |  方向|

```json

{
	"biz": "market",
	"data": [{
		"vol": "1",
		"ts": 1639585820373,
		"id": 28470000,
		"price": "11",
		"direction": "buy"
	}, {
		"vol": "1",
		"ts": 1639585820376,
		"id": 28730000,
		"price": "11.9",
		"direction": "sell"
	}],
	"id": "his",
	"pairCode": "ETH_USDT",
	"ts": 1640919016188,
	"type": "fills"
}

``` 

-----

## OrderBook Subscribe/UnSubscribe

> request

```json
{
  "event": "sub",
  "params": {
    "biz": "market",
    "type": "orderBook",
    "pairCode": "ETH_USDT",
    "interval": "1"
  },
  "zip": false
}
```

#### Subscribe

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| params .biz | 是  |string |   |
| params .type     |是  |string | 订阅类型类型  |
| params .pairCode     |是  |string | 币对|
| params .interval     |是  |string | _周期_ |
| event     |是  |string | 事件 |
| zip     |是  |bool | 是否启用gzip |


> response

```json
{
  "id": "",
  "channel": "subscribe",
  "biz": "market",
  "type": "orderBook",
  "pairCode": "ETH_USDT",
  "interval": "step1",
  "ts": 1641384620237,
  "status": "ok"
}
```

#### UnSubscribe 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| params .biz | 是  |string |   |
| params .type     |是  |string | 订阅类型类型  |
| params .pairCode     |是  |string | 币对|
| params .interval     |是  |string | _周期_ |
| event     |是  |string | 事件 |
| zip     |是  |bool | 是否启用gzip |

```json
{
  "event": "unsub",
  "params": {
    "biz": "market",
    "type": "orderBook",
    "pairCode": "ETH_USDT",
    "interval": "1"
  },
  "zip": false
}

```

```json
{
  "id": "",
  "unsubbed": "market.ETH_USDT.depth.step1",
  "ts": 1641384766983,
  "status": "ok"
}

```

#### FEED 



```json

{
	"seqId": 8414921,
	"id": 1641385128,
	"bids": [
		[3781.85, 0.30656],
		[3781.78, 0.0219],
		[360, 4.59207],
		[10, 11]
	],
	"asks": [
		[3835, 0.19948],
		[3836.98, 0.00026],
		[3837.33, 0.4445],
		[3839, 0.2]
	],
	"ts": 1641385128493,
	"version": 1641385128,
	"type": "orderBook",
	"pairCode": "ETH_USDT",
	"interval": "1"
}
```
----

## Percent10 Subscribe\Unsubscribe

#### Subscribe

> request

```json
	{
		"event": "sub",
		"params": {
			"type": "percent10",
			"pairCode": "ETH_USDT"
		},
		"zip":false
	}	
```

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| params .biz | 是  |string |   |
| params .type     |是  |string | 订阅类型类型  |
| params .pairCode     |是  |string | 币对|
| event     |是  |string | 事件 |
| zip     |是  |bool | 是否启用gzip |
```json
{
  "id": "",
  "channel": "subscribe",
  "biz": "market",
  "type": "percent10",
  "pairCode": "ETH_USDT",
  "interval": "",
  "ts": 1641387412252,
  "status": "ok"
}
```
#### UnSubscribe

> request

```json
	{
		"event": "unsub",
		"params": {
			"type": "percent10",
			"pairCode": "ETH_USDT"
		},
		"zip":false
	}	
```

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| params .biz | 是  |string |   |
| params .type     |是  |string | 订阅类型类型  |
| params .pairCode     |是  |string | 币对|
| event     |是  |string | 事件 |
| zip     |是  |bool | 是否启用gzip |

```json
{
  "id": "",
  "unsubbed": "market.ETH_USDT.depth.percent10",
  "ts": 1641387599816,
  "status": "ok"
}
```


#### FEED

```json
{
	"seqId": 2875,
	"id": 1640683777,
	"bids": [
		[11.994, 0.10124],
		[11.988, 0],
		[11.982, 0],
		[11.976, 0],
		[11.97, 0],
		[11.964, 0],
		[11.958, 0],
		[11.952, 0],
		[11.946, 0],
		[11.94, 0],
		[11.934, 0],
		[11.928, 0],
		[11.922, 0],
		[11.916, 0],
		[11.91, 0],
		[11.904, 0],
		[11.898, 0],
		[11.892, 0],
		[11.886, 0],
		[11.88, 0],
		[11.874, 0],
		[11.868, 0],
		[11.862, 0],
		[11.856, 0],
		[11.85, 0],
		[11.844, 0],
		[11.838, 0],
		[11.832, 0],
		[11.826, 0],
		[11.82, 0],
		[11.814, 0],
		[11.808, 0],
		[11.802, 0],
		[11.796, 0],
		[11.79, 0],
		[11.784, 0],
		[11.778, 0],
		[11.772, 0],
		[11.766, 0],
		[11.76, 0],
		[11.754, 0],
		[11.748, 0],
		[11.742, 0],
		[11.736, 0],
		[11.73, 0],
		[11.724, 0],
		[11.718, 0],
		[11.712, 0],
		[11.706, 0],
		[11.7, 0],
		[11.694, 0],
		[11.688, 0],
		[11.682, 0],
		[11.676, 0],
		[11.67, 0],
		[11.664, 0],
		[11.658, 0],
		[11.652, 0],
		[11.646, 0],
		[11.64, 0],
		[11.634, 0],
		[11.628, 0],
		[11.622, 0],
		[11.616, 0],
		[11.61, 0],
		[11.604, 0],
		[11.598, 0],
		[11.592, 0],
		[11.586, 0],
		[11.58, 0],
		[11.574, 0],
		[11.568, 0],
		[11.562, 0],
		[11.556, 0],
		[11.55, 0],
		[11.544, 0],
		[11.538, 0],
		[11.532, 0],
		[11.526, 0],
		[11.52, 0],
		[11.514, 0],
		[11.508, 0],
		[11.502, 0],
		[11.496, 0],
		[11.49, 0],
		[11.484, 0],
		[11.478, 0],
		[11.472, 0],
		[11.466, 0],
		[11.46, 0],
		[11.454, 0],
		[11.448, 0],
		[11.442, 0],
		[11.436, 0],
		[11.43, 0],
		[11.424, 0],
		[11.418, 0],
		[11.412, 0],
		[11.406, 0],
		[11.4, 0],
		[11.394, 0],
		[11.388, 0],
		[11.382, 0],
		[11.376, 0],
		[11.37, 0],
		[11.364, 0],
		[11.358, 0],
		[11.352, 0],
		[11.346, 0],
		[11.34, 0],
		[11.334, 0],
		[11.328, 0],
		[11.322, 0],
		[11.316, 0],
		[11.31, 0],
		[11.304, 0],
		[11.298, 0],
		[11.292, 0],
		[11.286, 0],
		[11.28, 0],
		[11.274, 0],
		[11.268, 0],
		[11.262, 0],
		[11.256, 0],
		[11.25, 0],
		[11.244, 0],
		[11.238, 0],
		[11.232, 0],
		[11.226, 0],
		[11.22, 0],
		[11.214, 0],
		[11.208, 0],
		[11.202, 0],
		[11.196, 0],
		[11.19, 0],
		[11.184, 0],
		[11.178, 0],
		[11.172, 0],
		[11.166, 0],
		[11.16, 0],
		[11.154, 0],
		[11.148, 0],
		[11.142, 0],
		[11.136, 0],
		[11.13, 0],
		[11.124, 0],
		[11.118, 0],
		[11.112, 0],
		[11.106, 0],
		[11.1, 0],
		[11.094, 0],
		[11.088, 0],
		[11.082, 0],
		[11.076, 0],
		[11.07, 0],
		[11.064, 0],
		[11.058, 0],
		[11.052, 0],
		[11.046, 0],
		[11.04, 0],
		[11.034, 0],
		[11.028, 0],
		[11.022, 0],
		[11.016, 0],
		[11.01, 0],
		[11.004, 0],
		[10.998, 0],
		[10.992, 0],
		[10.986, 0],
		[10.98, 0],
		[10.974, 0],
		[10.968, 0],
		[10.962, 0],
		[10.956, 0],
		[10.95, 0],
		[10.944, 0],
		[10.938, 0],
		[10.932, 0],
		[10.926, 0],
		[10.92, 0],
		[10.914, 0],
		[10.908, 0],
		[10.902, 0],
		[10.896, 0],
		[10.89, 0],
		[10.884, 0],
		[10.878, 0],
		[10.872, 0],
		[10.866, 0],
		[10.86, 0],
		[10.854, 0],
		[10.848, 0],
		[10.842, 0],
		[10.836, 0],
		[10.83, 0],
		[10.824, 0],
		[10.818, 0],
		[10.812, 0],
		[10.806, 0],
		[10.8, 0]
	],
	"asks": [
		[12.006, 0],
		[12.012, 0],
		[12.018, 0],
		[12.024, 0],
		[12.03, 0],
		[12.036, 0],
		[12.042, 0],
		[12.048, 0],
		[12.054, 0],
		[12.06, 0],
		[12.066, 0],
		[12.072, 0],
		[12.078, 0],
		[12.084, 0],
		[12.09, 0],
		[12.096, 0],
		[12.102, 0],
		[12.108, 0],
		[12.114, 0],
		[12.12, 0],
		[12.126, 0],
		[12.132, 0],
		[12.138, 0],
		[12.144, 0],
		[12.15, 0],
		[12.156, 0],
		[12.162, 0],
		[12.168, 0],
		[12.174, 0],
		[12.18, 0],
		[12.186, 0],
		[12.192, 0],
		[12.198, 0],
		[12.204, 0],
		[12.21, 0],
		[12.216, 0],
		[12.222, 0],
		[12.228, 0],
		[12.234, 0],
		[12.24, 0],
		[12.246, 0],
		[12.252, 0],
		[12.258, 0],
		[12.264, 0],
		[12.27, 0],
		[12.276, 0],
		[12.282, 0],
		[12.288, 0],
		[12.294, 0],
		[12.3, 0],
		[12.306, 0],
		[12.312, 0],
		[12.318, 0],
		[12.324, 0],
		[12.33, 0],
		[12.336, 0],
		[12.342, 0],
		[12.348, 0],
		[12.354, 0],
		[12.36, 0],
		[12.366, 0],
		[12.372, 0],
		[12.378, 0],
		[12.384, 0],
		[12.39, 0],
		[12.396, 0],
		[12.402, 0],
		[12.408, 0],
		[12.414, 0],
		[12.42, 0],
		[12.426, 0],
		[12.432, 0],
		[12.438, 0],
		[12.444, 0],
		[12.45, 0],
		[12.456, 0],
		[12.462, 0],
		[12.468, 0],
		[12.474, 0],
		[12.48, 0],
		[12.486, 0],
		[12.492, 0],
		[12.498, 0],
		[12.504, 0],
		[12.51, 0],
		[12.516, 0],
		[12.522, 0],
		[12.528, 0],
		[12.534, 0],
		[12.54, 0],
		[12.546, 0],
		[12.552, 0],
		[12.558, 0],
		[12.564, 0],
		[12.57, 0],
		[12.576, 0],
		[12.582, 0],
		[12.588, 0],
		[12.594, 0],
		[12.6, 0],
		[12.606, 0],
		[12.612, 0],
		[12.618, 0],
		[12.624, 0],
		[12.63, 0],
		[12.636, 0],
		[12.642, 0],
		[12.648, 0],
		[12.654, 0],
		[12.66, 0],
		[12.666, 0],
		[12.672, 0],
		[12.678, 0],
		[12.684, 0],
		[12.69, 0],
		[12.696, 0],
		[12.702, 0],
		[12.708, 0],
		[12.714, 0],
		[12.72, 0],
		[12.726, 0],
		[12.732, 0],
		[12.738, 0],
		[12.744, 0],
		[12.75, 0],
		[12.756, 0],
		[12.762, 0],
		[12.768, 0],
		[12.774, 0],
		[12.78, 0],
		[12.786, 0],
		[12.792, 0],
		[12.798, 0],
		[12.804, 0],
		[12.81, 0],
		[12.816, 0],
		[12.822, 0],
		[12.828, 0],
		[12.834, 0],
		[12.84, 0],
		[12.846, 0],
		[12.852, 0],
		[12.858, 0],
		[12.864, 0],
		[12.87, 0],
		[12.876, 0],
		[12.882, 0],
		[12.888, 0],
		[12.894, 0],
		[12.9, 0],
		[12.906, 0],
		[12.912, 0],
		[12.918, 0],
		[12.924, 0],
		[12.93, 0],
		[12.936, 0],
		[12.942, 0],
		[12.948, 0],
		[12.954, 0],
		[12.96, 0],
		[12.966, 0],
		[12.972, 0],
		[12.978, 0],
		[12.984, 0],
		[12.99, 0],
		[12.996, 0],
		[13.002, 0],
		[13.008, 0],
		[13.014, 0],
		[13.02, 0],
		[13.026, 0],
		[13.032, 0],
		[13.038, 0],
		[13.044, 0],
		[13.05, 0],
		[13.056, 0],
		[13.062, 0],
		[13.068, 0],
		[13.074, 0],
		[13.08, 0],
		[13.086, 0],
		[13.092, 0],
		[13.098, 0],
		[13.104, 0],
		[13.11, 0],
		[13.116, 0],
		[13.122, 0],
		[13.128, 0],
		[13.134, 0],
		[13.14, 0],
		[13.146, 0],
		[13.152, 0],
		[13.158, 0],
		[13.164, 0],
		[13.17, 0],
		[13.176, 0],
		[13.182, 0],
		[13.188, 0],
		[13.194, 0],
		[13.2, 0]
	],
	"ts": 1640683777520,
	"version": 1640683777,
	"type": "percent10",
	"pairCode": "ETH_USDT"
}
```

----


##  Ticker Subscribe\UnSubscribe



#### Subscribe

> request

```json
	{
		"event": "sub",
		"params": {
			"biz": "market",
			"type": "ticker",
			"pairCode": "ETH_USDT"
		},
		"zip":false
	}	
```


|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| params .biz | 是  |string |   |
| params .type     |是  |string | 订阅类型类型  |
| params .pairCode     |是  |string | 币对|
| params .interval     |是  |string | 周期 |
| event     |是  |string | 事件 |
| zip     |是  |bool | 是否启用gzip |


> response

```json
{
  "id": "",
  "channel": "subscribe",
  "biz": "market",
  "type": "ticker",
  "pairCode": "ETH_USDT",
  "interval": "",
  "ts": 1641387679813,
  "status": "ok"
}
```

#### Subscribe

> request

```json
	{
		"event": "unsub",
		"params": {
			"biz": "market",
			"type": "ticker",
			"pairCode": "ETH_USDT"
		},
		"zip":false
	}	
```


|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| params .biz | 是  |string |   |
| params .type     |是  |string | 订阅类型类型  |
| params .pairCode     |是  |string | 币对|
| params .interval     |是  |string | 周期 |
| event     |是  |string | 事件 |
| zip     |是  |bool | 是否启用gzip |


> response

```json
{
  "id": "",
  "unsubbed": "market.ETH_USDT.ticker",
  "ts": 1641387799984,
  "status": "ok"
}
```
#### FEED 

|参数名|类型|说明|
|:----    |:----- |-----   |
| type | string |  订阅类型 |
| interval     |string | 间隔  |
| pairCode    |string | 币对|
| data .open     |string | 开盘 |
| data .close    |string | 收盘 |
| data .low     |string | 低 |
| data .high     |string | 高 |
| data .vol     |string | 成交 |
| data .turnOver     |string | 成交量 |
| data .count     |string |  |

> push 

```json

{
	"biz": "market",
	"data": {
		"open": "18",
		"close": "19.56",
		"low": "18",
		"high": "19.56",
		"turnOver": "68.46",
		"count": 0,
		"vol": "3.5",
		"pairCode": "BTC_USDT",
		"change": "1.56",
		"changePercent": "0.0866666666666667"
	},
	"id": "",
	"pairCode": "BTC_USDT",
	"ts": 1640251563497,
	"type": "ticker"
}
```
----

# WEBSOCKET REQUEST

## Request Candles

> request 

```json
{
	"event": "req",
	"params": {
		"biz": "market",
		"type": "candles",
		"pairCode": "ETH_USDT",
		"interval": "1day",
		"size": 301,
		"from": 1613692800,
		"to": 1639699200,
		"id": "his"
	},
	"zip":false
}
```
| 参数名             | 必选  |类型| 说明       |
|:----------------|:----|:----- |----------|
| params.biz      | 是   |string |          |
| params.type     | 是   |string | 类型       |
| params.pairCode | 是   |string | 币对       |
| params.interval | 是   |string | 周期       |
| params.from     | 是   |string | 开始时间     |
| params.to       | 是   |string | 结束时间     |
| event           | 是   |string | 事件       |
| zip             | 是   |bool | 是否启用gzip |


###### 返回结构

|参数名|类型|   说明 |
|:------:|:----:|:--:|
| close | int  |   收盘价格 |
| high | int  |   最高价格 |
| low | int  |   最低价格 |
| open | int  |  开盘价格 |
| turnOver | string  |  交易量 |
| vol | string  |  交易额 |
| pairCode | string  |  币对  |


```json
{
	"id": "his",
	"type": "candles",
	"pairCode": "ETH_USDT",
	"interval": "1day",
	"data": [{
		"id": 1639584000,
		"open": 11,
		"close": 11.9,
		"low": 11,
		"high": 11.9,
		"vol": 2,
		"turnOver": 22.9,
		"count": 2
	}, {
		"id": 1639670400,
		"open": 11.9,
		"close": 11.9,
		"low": 11.9,
		"high": 11.9,
		"vol": 0,
		"turnOver": 0,
		"count": 0
	}]
}


```

## Request Ticker

#### 请求结构

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| params.biz | 是  |string |   |
| params.type     |否  |string | 类型 |
| params.pairCode     |否  |string | 币对|
| event     |是  |string | 事件 |
| zip     |是  |bool | 是否启用gzip |

```json
	{
	"event": "req",
	"params": {
		"biz": "market",
		"type": "ticker",
		"pairCode": "ETH_USDT",
		"id": "his"
	},
	"zip":false
}
```

#### 返回参数

|参数名|类型|   说明 |
|:------:|:----:|:--:|
| close | int  |   收盘价格 |
| high | int  |   最高价格 |
| low | int  |   最低价格 |
| open | int  |  开盘价格 |
| turnOver | string  |  交易量 |
| vol | string  |  交易额 |
| pairCode | string  |  币对  |

```json
{
	"biz": "market",
	"data": {
		"open": "18",
		"close": "19.56",
		"low": "18",
		"high": "19.56",
		"turnOver": "68.46",
		"count": 0,
		"vol": "3.5",
		"pairCode": "BTC_USDT",
		"change": "1.56",
		"changePercent": "0.0866666666666667"
	},
	"id": "",
	"pairCode": "BTC_USDT",
	"ts": 1640251563497,
	"type": "ticker"
}
```


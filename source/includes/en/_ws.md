# WEBSOCKET FEED PUBLIC

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
			"product":"ETH_BNB",
			"interval": "1day"
		},
		"zip":false
	}	
```

#### Request parameters

|Parameter Name|Mandatory|Type| Description   |
|:----    |:---|:----- |------|
| params .biz | Y  |string |      |
| params .type     |Y  |string | Subscription type |
| params .product     |Y  |string | Currency pair   |
| params .interval     |Y  |string | Interval   |
| event     |Y  |string | Event Subscribe  |
| zip     |Y  |bool | Enable GZIP or not |


> response

```json
{
	"id": "",
	"channel": "subscribe",
	"biz": "market",
	"type": "candles",
	"product": "ETH_BNB",
	"interval": "1day",
	"ts": 1639655425910,
	"status": "ok"
}
```

#### Response parameters
|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| type | string |  Subscription type |
| interval     |string | Interval |
| product    |string | Currency pair|
| data .open     |string | Opening |
| data .close    |string | Closing |
| data .low     |string | Lowest |
| data .high     |string | Highest |
| data .vol     |string | Volume |
| data .turnOver     |string | Trading volume |
| data .count     |string |  |


#### UnSubscribe

> request

```json
	{
		"event": "unsub",
		"params": {
			"biz": "market",
			"type": "candles",
			"product": "ETH_BNB",
			"interval": "1day"
		},
		"zip":true
	}	
```

#### Request parameters

|Parameter Name|Mandatory|Type|Description      |
|:----    |:---|:----- |---------------|
| params .biz | Y  |string |               |
| params .type     |Y  |string | Subscription type        |
| params .product     |Y  |string | Currency pair            |
| params .interval     |Y  |string | Interval            |
| event     |Y  |string | Event Unsubscribe |
| zip     |Y  |bool | Enable GZIP or not      |


> response

```json
{
	"id": "",
	"channel":"unsubscribe",
	"biz": "market",
	"type": "candles",
	"product": "ETH_BNB",
	"interval": "1day",
	"ts": 1639655425910,
	"status": "ok"
}
```

#### Response parameters
|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| type | string |  Subscription type
| interval     |string | Interval |
| product    |string | Currency pair|
| data .open     |string | Opening |
| data .close    |string | Closing |
| data .low     |string | Lowest |
| data .high     |string | Highest |
| data .vol     |string | Volume |
| data .turnOver     |string | Trading volume |
| data .count     |string |  |



#### FEED 


```json

{
	"id": "his",
	"type": "candles",
	"product": "ETH_USDT",
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
    "product": "ETH_USDT"
  },
  "zip": false
}
```


|Parameter Name|Mandatory|Type|Description |
|:----    |:---|:----- |----------|
| params .biz | Y  |string |          |
| params .type     |Y  |string | Subscription type   |
| params .product     |Y  |string | Currency pair       |
| params .interval     |Y  |string | Interval       |
| event     |Y  |string | Event Subscribe      |
| zip     |Y  |bool | Enable GZIP or not |



```json
{
  "id": "",
  "channel": "subscribe",
  "biz": "market",
  "type": "fills",
  "product": "ETH_USDT",
  "interval": "",
  "ts": 1641384262679,
  "status": "ok"
}
```

#### UnSubscribe

|Parameter Name|Mandatory|Type|Description |
|:----    |:---|:----- |----------|
| params .biz | Y  |string |          |
| params .type     |Y  |string | Subscription type   |
| params .product     |Y  |string | Currency pair       |
| params .interval     |Y  |string | Interval       |
| event     |Y  |string | Event Subscribe      |
| zip     |Y  |bool | Enable GZIP or not |

```json

{
	"event": "unsub",
	"params": {
		"biz": "market",
		"type": "fills",
		"product": "ETH_USDT"
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

|Parameter Name|Type|Description|
|:----    |:---|:----- |-----   |
| type | string |  Subscription type
| interval     |string | Interval |
| product    |string | Currency pair|
| data .price     |string | Price |
| data .vol     |string | Volume |
| data .ts     |int  | Timestamp |
| data .direction     |string |  Direction |

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
	"product": "ETH_USDT",
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
    "product": "ETH_USDT",
    "interval": "1"
  },
  "zip": false
}
```

#### Subscribe

|Parameter Name|Mandatory|Type|Description|
|:----    |:---|:----- |-----   |
| params .biz | Y  |string |   |
| params .type     |Y  |string | Subscription type  |
| params .product     |Y  |string | Currency pair|
| params .interval     |Y  |string | Interval |
| event     |Y  |string | Event |
| zip     |Y  |bool | Enable GZIP or not |


> response

```json
{
  "id": "",
  "channel": "subscribe",
  "biz": "market",
  "type": "orderBook",
  "product": "ETH_USDT",
  "interval": "step1",
  "ts": 1641384620237,
  "status": "ok"
}
```

#### UnSubscribe 

|Parameter Name|Mandatory|Type|Description|
|:----    |:---|:----- |-----   |
| params .biz | Y  |string |   |
| params .type     |Y  |string | Subscription type  |
| params .product     |Y  |string | Currency pair|
| params .interval     |Y  |string | Interval |
| event     |Y  |string | Event |
| zip     |Y  |bool | Enable GZIP or not |

```json
{
  "event": "unsub",
  "params": {
    "biz": "market",
    "type": "orderBook",
    "product": "ETH_USDT",
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
	"product": "ETH_USDT",
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
			"product": "ETH_USDT"
		},
		"zip":false
	}	
```

|Parameter Name|Mandatory|Type|Description|
|:----    |:---|:----- |-----   |
| params .biz | Y  |string |   |
| params .type     |Y  |string | Subscription type  |
| params .product     |Y  |string | Currency pair|
| event     |Y  |string | Event |
| zip     |Y  |bool | Enable GZIP or not |
```json
{
  "id": "",
  "channel": "subscribe",
  "biz": "market",
  "type": "percent10",
  "product": "ETH_USDT",
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
			"product": "ETH_USDT"
		},
		"zip":false
	}	
```

|Parameter Name|Mandatory|Type|Description|
|:----    |:---|:----- |-----   |
| params .biz | Y  |string |   |
| params .type     |Y  |string | Subscription type  |
| params .product     |Y  |string | Currency pair|
| event     |Y  |string | Event |
| zip     |Y  |bool | Enable GZIP or not |

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
		[11.994, 0.10124]
	],
	"asks": [
		[12.006, 0]
	],
	"ts": 1640683777520,
	"version": 1640683777,
	"type": "percent10",
	"product": "ETH_USDT"
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
			"product": "ETH_USDT"
		},
		"zip":false
	}	
```


|Parameter Name|Mandatory|Type|Description|
|:----    |:---|:----- |-----   |
| params .biz | Y  |string |   |
| params .type     |Y  |string | Subscription type  |
| params .product     |Y  |string | Currency pair|
| params .interval     |Y  |string | Interval |
| event     |Y  |string | Event |
| zip     |Y  |bool | Enable GZIP or not |


> response

```json
{
  "id": "",
  "channel": "subscribe",
  "biz": "market",
  "type": "ticker",
  "product": "ETH_USDT",
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
			"product": "ETH_USDT"
		},
		"zip":false
	}	
```


|Parameter Name|Mandatory|Type|Description|
|:----    |:---|:----- |-----   |
| params .biz | Y  |string |   |
| params .type     |Y  |string | Subscription type  |
| params .product     |Y  |string | Currency pair|
| params .interval     |Y  |string | Interval |
| event     |Y  |string | Event |
| zip     |Y  |bool | Enable GZIP or not |


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

|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| type | string |  Subscription type
| interval     |string | Interval |
| product    |string | Currency pair|
| data .open     |string | Opening |
| data .close    |string | Closing |
| data .low     |string | Lowest |
| data .high     |string | Highest |
| data .vol     |string | Volume |
| data .turnOver     |string | Trading volume |
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
		"product": "BTC_USDT",
		"change": "1.56",
		"changePercent": "0.0866666666666667"
	},
	"id": "",
	"product": "BTC_USDT",
	"ts": 1640251563497,
	"type": "ticker"
}
```
----


## Request Candles

> request 

```json
{
	"event": "req",
	"params": {
		"biz": "market",
		"type": "candles",
		"product": "ETH_USDT",
		"interval": "1day",
		"size": 301,
		"from": 1613692800,
		"to": 1639699200,
		"id": "his"
	},
	"zip":false
}
```
|Parameter Name            |Mandatory|Type|Description |
|:----------------|:----|:----- |----------|
| params.biz      | Y   |string |          |
| params.type     | Y   |string | Type       |
| params.product | Y   |string | Currency pair       |
| params.interval | Y   |string | Interval       |
| params.from     | Y   |string  | Start time     |
| params.to       | Y   |string  | End time     |
| event           | Y   |string  | Event       |
| zip             | Y   |bool | Enable GZIP or not |


###### 返回结构

|Parameter Name|Type|   Description|
|:------:|:----:|:--:|
| close | int  |   Closing price |
| high | int  |   Highest price |
| low | int  |   Lowest price |
| open | int  |  Opening price |
| turnOver | string  |  Trading volume |
| vol | string  |  Turnover |
| product | string  |  Currency pair |


```json
{
	"id": "his",
	"type": "candles",
	"product": "ETH_USDT",
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

|Parameter Name|Mandatory|Type|Description|
|:----    |:---|:----- |-----   |
| params.biz | Y  |string |   |
| params.type      | N  |string | Type |
| params.product      | N  |string | Currency pair|
| event     |Y  |string | Event |
| zip     |Y  |bool | Enable GZIP or not |

```json
	{
	"event": "req",
	"params": {
		"biz": "market",
		"type": "ticker",
		"product": "ETH_USDT",
		"id": "his"
	},
	"zip":false
}
```

#### Response parameters

|Parameter Name|Type|   Description|
|:------:|:----:|:--:|
| close | int  |   Closing price |
| high | int  |   Highest price |
| low | int  |   Lowest price |
| open | int  |  Opening price |
| turnOver | string  |  Trading volume |
| vol | string  |  Turnover |
| product | string  |  Currency pair |

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
	"product": "BTC_USDT",
	"ts": 1640251563497,
	"type": "ticker"
}
```


# WEBSOCKET FEED PUBLIC (DEPRECATED)

- ` wss://ws.bg.exchange/ws`

## Candles Subscribe/UnSubscribe 

#### Subscribe

> sub request

```json
{
    "event": "sub",
    "params":{
        "biz": "market",
        "type": "candles",
        "product": "ETH_BNB",
        "interval": "30min"
    },
    "zip": true
}
```

#### Request Parameters

|Parameter Name|Required|Type| Description   |
|:----    |:---|:----- |------|
| params .biz | Yes  |string |      |
| params .type     |Yes  |string | Subscription type |
| params .product     |Yes  |string | Currency pair   |
| params .interval     |Yes  |string | Interval   |
| event     |Yes  |string | event Subscribe  |
| zip     |Yes  |bool | Enable gzip |


> sub response

```json
{
	"channel": "subscribe",
	"biz": "market",
	"type": "candles",
	"product": "ETH_BNB",
	"interval": "30min",
	"ts": 1639655425910,
	"status": "ok"
}
```

#### Response Parameters
|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| type | string |  Subscription type |
| interval     |string | Interval  |
| product    |string | Currency pair|
| data .open     |string | The first traded price in this candle |
| data .close    |string | The last traded price in this candle  |
| data .low     |string | The lowest traded price in this candle |
| data .high     |string | The highest traded price in this candle |
| data .vol     |string | Total trading volume in this candle |
| data .turnOver     |string | Total turnover in this candle |
| data .id     | int | Unique and sequential ID  |
| data .count     | int | Total number of trades in this candle |


#### UnSubscribe

> unsub request

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

#### Request Parameters

|Parameter Name|Required|Type| Description            |
|:----    |:---|:----- |---------------|
| params .biz | Yes  |string |               |
| params .type     |Yes  |string | Subscription type        |
| params .product     |Yes  |string | Currency pair            |
| params .interval     |Yes  |string | Interval            |
| event     |Yes  |string | Event UnSubscribe |
| zip     |Yes  |bool | Enable gzip      |


> unsub response

```json
{
	"channel":"unsubscribe",
	"biz": "market",
	"type": "candles",
	"product": "ETH_BNB",
	"interval": "1day",
	"ts": 1639655425910,
	"status": "ok"
}
```

#### Response Parameters
|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| type | string |  Subscription type |
| interval     |string | Interval  |
| product    |string | currency pair|
| data .open     |string | The first traded price in this candle |
| data .close    |string | The last traded price in this candle  |
| data .low     |string | The lowest traded price in this candle |
| data .high     |string | The highest traded price in this candle |
| data .vol     |string | Total trading volume in this candle |
| data .turnOver     |string | Total turnover in this candle |
| data .id     | int |   | Unique ID |
| data .count     | int | Total number of trades in this candle |
| data .seqId     |int | Unique and sequential ID |



#### Feed Stream 

> feed stream

```json



{
    "id": 1688954400,
    "type": "candles",
    "pairCode": "BTC_USDT",
    "product": "BTC_USDT",
    "data":
    {
        "open": 3.1406,
        "close": 3.0466,
        "high": 4.0007,
        "low": 3.0051,
        "turnOver": 51642.553798,
        "vol": 14765.94,
        "count": 52144,
        "seqId": 111322735,
        "id": 1688954400
    },
    "interval": "30min",
    "SeqId": 111322735
}

```
----

##  Fills Subscribe/UnSubscribe

#### Subscribe

> sub request

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


|Parameter Name|Required|Type| Description       |
|:----    |:---|:----- |----------|
| params .biz | Yes  |string |          |
| params .type     |Yes  |string | Subscription typeType   |
| params .product     |Yes  |string | Currency pair       |
| event     |Yes  |string | event Subscribe      |
| zip     |Yes  |bool | Enable gzip |

> sub response

```json
{
  "channel": "subscribe",
  "biz": "market",
  "type": "fills",
  "product": "ETH_USDT",
  "ts": 1641384262679,
  "status": "ok"
}
```

#### UnSubscribe

|Parameter Name|Required|Type| Description       |
|:----    |:---|:----- |----------|
| params .biz | Yes  |string |   |
| params .type     |Yes  |string | Subscription typeType   |
| params .product     |Yes  |string | Currency pair       |
| params .interval     |Yes  |string | Interval       |
| event     |Yes  |string | event Subscribe      |
| zip     |Yes  |bool | Enable gzip |


> sub request

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

> unsub response

```json
{
    "biz": "market",
    "channel": "unsubscribe",
    "product": "ETH_USDT",
    "type": "fills",
    "status": "ok",
    "ts": 1689041894440
}

```
#### Feed Stream 

|Parameter Name|Type|Description|
|:----    |:---|:----- |-----   |
| id | int | number | Unique ID |
| type | string |  Subscription type |
| interval     |string | Interval  |
| product    |string | Currency pair|
| pairCode    |string | ignore|
| data .price     |string | Price |
| data .vol     |string | Trading volume |
| data .ts     |int  | Timestamp |
| data .direction     |string |  Direction|
| data .id     |int |  Trade ID |


> feed stream


```json
{
    "id": 323241,
    "type": "fills",
    "pairCode": "BTC_USDT",
    "data":
    [
        {
            "ts": 1689152406185,
            "id": 323241000,
            "vol": "0.04",
            "price": "3.6733",
            "direction": "buy"
        }
    ],
    "product": "BTC_USDT",
    "ts": 1689152412845
}


``` 

-----

## OrderBook Subscribe/UnSubscribe

> sub request

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

|Parameter Name|Required|Type|Description|
|:----    |:---|:----- |-----   |
| params .biz | Yes  |string |  |
| params .type     |Yes  |string | Subscription type  |
| params .product     |Yes  |string | Currency pair|
| params .interval     |Yes  |string | _Interval_ |
| event     |Yes  |string | Event |
| zip     |Yes  |bool | Enable gzip |


> sub response

```json
{
    "biz": "market",
    "channel": "subscribe",
    "interval": "1",
    "product": "ETH_USDT",
    "type": "orderBook",
    "status": "ok",
    "ts": 1689934070509
}
```

#### UnSubscribe 

|Parameter Name|Required|Type|Description|
|:----    |:---|:----- |-----   |
| params .biz | Yes  |string |  |
| params .type     |Yes  |string | Subscription type  |
| params .product     |Yes  |string | Currency pair|
| params .interval     |Yes  |string | _Interval_ |
| event     |Yes  |string | Event |
| zip     |Yes  |bool | Enable gzip |



> unsub request

```json
{
  "event": "unsub",
  "params": {
    "biz": "market",
    "type": "orderBook",
    "product": "ETH_USDT",
    "interval": "1min"
  },
  "zip": false
}

```


> unsub response

```json
{
    "biz": "market",
    "channel": "unsubscribe",
    "interval": "1min",
    "product": "ETH_USDT",
    "type": "orderBook",
    "status": "ok",
    "ts": 1689934273388
}
```

#### Feed Stream 

> feed stream

```json

{
    "id": 1689934071,
    "type": "orderBook",
    "pairCode": "ETH_USDT",
    "product": "ETH_USDT",
    "ts": 1689934071000,
    "version": 1689934071,
    "seqId": 0,
    "interval": "1min",
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
	]
}

```
----

## Percent10 Subscribe\Unsubscribe

#### Subscribe

> sub request

```json
{
    "event": "sub",
    "params":
    {
        "biz": "market",
        "type": "percent10",
        "product": "ETH_USDT"
    },
    "zip": false
}	
```

|Parameter Name|Required|Type|Description|
|:----    |:---|:----- |-----   |
| params .biz | Yes  |string |  |
| params .type     |Yes  |string | Subscription type  |
| params .product     |Yes  |string | Currency pair|
| event     |Yes  |string | Event |
| zip     |Yes  |bool | Enable gzip |

> sub response

```json
{
    "biz": "market",
    "channel": "subscribe",
    "product": "ETH_USDT",
    "type": "percent10",
    "status": "ok",
    "ts": 1689934871904
}
```
#### UnSubscribe

> unsub request

```json
{
    "event": "unsub",
    "params":
    {
        "biz": "market",
        "type": "percent10",
        "product": "ETH_USDT"
    },
    "zip": false
}
```

|Parameter Name|Required|Type|Description|
|:----    |:---|:----- |-----   |
| params .biz | Yes  |string | |
| params .type     |Yes  |string | Subscription type  |
| params .product     |Yes  |string | Currency pair|
| params .pairCode     |Yes  |string | Currency pair|
| event     |Yes  |string | Event |
| zip     |Yes  |bool | Enable gzip |

> unsub response

```json
{
    "biz": "market",
    "channel": "unsubscribe",
    "product": "ETH_USDT",
    "type": "percent10",
    "status": "ok",
    "ts": 1689934879610
}
```


#### Feed Stream 

> feed stream

```json

{
    "id": 1689934879,
    "type": "percent10",
    "pairCode": "ETH_USDT",
    "product": "ETH_USDT",
    "ts": 1689934879000,
    "version": 1689934879,
    "seqId": 0,
    "bids": [
		[11.994, 0.10124]
	],
    "asks": [
		[12.006, 0]
	]
}
```

----


##  Ticker Subscribe\UnSubscribe



#### Subscribe

> sub request

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


|Parameter Name|Required|Type|Description|
|:----    |:---|:----- |-----   |
| params .biz | Yes  |string |  |
| params .type     |Yes  |string | Subscription type  |
| params .product     |Yes  |string | Currency pair|
| event     |Yes  |string | Event |
| zip     |Yes  |bool | Enable gzip |


> sub response

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

#### UnSubscribe

> unsub request

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


|Parameter Name|Required|Type|Description|
|:----    |:---|:----- |-----   |
| params .biz | Yes  |string |  |
| params .type     |Yes  |string | Subscription type  |
| params .product     |Yes  |string | Currency pair|
| event     |Yes  |string | Event |
| zip     |Yes  |bool | Enable gzip |


> unsub response

```json
{
    "biz": "market",
    "channel": "unsubscribe",
    "product": "BTC_USDT",
    "type": "ticker",
    "status": "ok",
    "ts": 1689935550687
}
```
#### Feed Stream 

|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| type | string |  Subscription type |
| ts     | int | Timestamp  |
| product    |string | Currency pair|
| msg    | string | ignore|
| code    | int | ignore|
| data .open     |string | The first traded price 24 hours ago |
| data .close    |string | The latest traded price in the last 24 hours |
| data .low     |string | The lowest traded price in the last 24 hours |
| data .high     |string | The highest traded price in the last 24 hours |
| data .vol     |string | Total trading volume in the last 24 hours |
| data .turnOver     |string | Total turnover in the last 24 hours |
| data .count     | int | Total number of trades in the last 24 hours |
| data .change     | int | Price change in the last 24 hours |
| data .changePercent     | int | Price change percentage in the last 24 hours |
| data .pairCode     |string | ignore |

> feed stream

```json

{
    "code": 200,
    "msg": "success",
    "ts": 1689935550508,
    "type": "ticker",
	"product": "BTC_USDT",
    "data":
    {
        "pairCode": "BTC_USDT",
        "open": "3.2934",
        "close": "3.01",
        "high": "4.003",
        "low": "2.9758",
        "turnOver": "25483.2032",
        "vol": "7355.4",
        "count": 0,
        "change": "-0.2834",
        "changePercent": "-0.0861"
    }
}
```
----


## Request Candles

> req request 

```json
{
	"event": "req",
	"params": {
		"biz": "market",
		"type": "candles",
		"product": "BTC_USDT",
		"interval": "1day",
		"size": 301,
		"from": 1613692800,
		"to": 1639699200
	},
	"zip":false
}
```
| Parameter Name             | Required  |Type| Description       |
|:----------------|:----|:----- |----------|
| params.biz      | Yes   |string |    |
| params.type     | Yes   |string | Type       |
| params.product | Yes   |string | Currency pair       |
| params.interval | Yes   |string | Interval       |
| params.from     | Yes   |string | K-line start time.   |
| params.to       | Yes   |string | K-line end time. |
| event           | Yes   |string | Event       |
| zip             | Yes   |bool | Enable gzip |


###### 返回结构

|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| biz | string |   |
| ts     | int | Timestamp  |
| product    |string | Currency pair|
| interval    | string | Interval 1day|
| event    | string | req |
| data .open     |string | The first traded price in this candle |
| data .close    |string | The last traded price in this candle  |
| data .low     |string | The lowest traded price in this candle |
| data .high     |string | The highest traded price in this candle |
| data .vol     |string | Total trading volume in this candle |
| data .turnOver     |string | Total turnover in this candle |
| data .id     | int | Unique and sequential ID  |
| data .count     | int | Total number of trades in this candle |

> req response 

```json
{
    "biz": "market",
    "product": "BTC_USDT",
    "ts": 1689936708184,
    "type": "candles",
    "interval": "1day",
    "event": "req",
    "data":
    [
        {
            "count": 2265,
            "turnOver": 2802.082564,
            "vol": 810.94,
            "id": 1689782400,
            "high": 4.003,
            "open": 3.2934,
            "low": 3.0103,
            "close": 3.2399
        },
        {
            "count": 25441,
            "turnOver": 29922.563131,
            "vol": 8627.47,
            "id": 1689868800,
            "high": 3.9711,
            "open": 3.2399,
            "low": 2.9758,
            "close": 3.8212
        }
    ]
}


```

## Request Ticker

#### 请求结构

|Parameter Name|Required|Type|Description|
|:----    |:---|:----- |-----   |
| params.biz | Yes  |string |   |
| params.type     |No  |string | Type |
| params.product     |No  |string | Currency pair|
| event     |Yes  |string | Event |
| zip     |Yes  |bool | Enable gzip |

> req request 

```json
	{
	"event": "req",
	"params": {
		"biz": "market",
		"type": "ticker",
		"product": "ETH_USDT"
	},
	"zip":false
}
```

#### Response Parameters

|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| biz | string |   |
| type     | string | ticker  |
| ts     | int | Timestamp  |
| product    |string | Currency pair|
| event    | string | req |
| data .open     |string | The first traded price 24 hours ago |
| data .close    |string | The latest traded price in the last 24 hours |
| data .low     |string | The lowest traded price in the last 24 hours |
| data .high     |string | The highest traded price in the last 24 hours |
| data .vol     |string | Total trading volume in the last 24 hours |
| data .turnOver     |string | Total turnover in the last 24 hours |
| data .count     | int | Total number of trades in the last 24 hours |
| data .change     | int | Price change in the last 24 hours |
| data .changePercent     | int | Price change percentage in the last 24 hours |


> req response 

```json
{
    "biz": "market",
    "product": "BTC_USDT",
    "ts": 1689937681602,
    "type": "ticker",
    "event": "req",
    "data":
    {
        "open": "3.2934",
        "close": "3.3483",
        "low": "2.9758",
        "high": "4.003",
        "turnOver": "39507.143672",
        "count": 0,
        "vol": "11384.41",
        "pairCode": "BTC_USDT",
        "change": "0.0549",
        "changePercent": "0.0167"
    }
}
```


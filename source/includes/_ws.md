# ~~WEBSOCKET PUBLIC(DEPRECATED)~~

- [公共频道地址(DEPRECATED)](#WS_HOST_PUBLIC)

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

#### 请求参数

|参数名|必选|类型| 说明   |
|:----    |:---|:----- |------|
| params .biz | 是  |string |      |
| params .type     |是  |string | 订阅类型 |
| params .product     |是  |string | 币对   |
| params .interval     |是  |string | 周期   |
| event     |是  |string | 事件 Subscribe  |
| zip     |是  |bool | 是否启用gzip |


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

#### 返回参数
|参数名|类型|说明|
|:----    |:----- |-----   |
| type | string |  订阅类型 |
| interval     |string | 间隔  |
| product    |string | 币对|
| data .open     |string | 这根K线期间第一笔成交价 |
| data .close    |string | 这根K线期间末一笔成交价 |
| data .low     |string | 这根K线期间最低成交价 |
| data .high     |string | 这根K线期间最高成交价 |
| data .vol     |string | 这根K线期间成交量 |
| data .turnOver     |string | 这根K线期间成交额 |
| data .id     | int | 唯一且有序id |
| data .count     | int | 这根K线期间成交笔数 |


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

#### 请求参数

|参数名|必选|类型| 说明            |
|:----    |:---|:----- |---------------|
| params .biz | 是  |string |               |
| params .type     |是  |string | 订阅类型        |
| params .product     |是  |string | 币对            |
| params .interval     |是  |string | 周期            |
| event     |是  |string | 事件 UnSubscribe |
| zip     |是  |bool | 是否启用gzip      |


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

#### 返回参数
|参数名|类型|说明|
|:----    |:----- |-----   |
| type | string |  订阅类型 |
| interval     |string | 间隔  |
| product    |string | 币对|
| data .open     |string | 这根K线期间第一笔成交价 |
| data .close    |string | 这根K线期间末一笔成交价 |
| data .low     |string | 这根K线期间最低成交价 |
| data .high     |string | 这根K线期间最高成交价 |
| data .vol     |string | 这根K线期间成交量 |
| data .turnOver     |string | 这根K线期间成交额 |
| data .id     | int | 唯一且有序id |
| data .count     | int | 这根K线期间成交笔数 |
| data .seqId     |int | 有序且唯一id |



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


|参数名|必选|类型| 说明       |
|:----    |:---|:----- |----------|
| params .biz | 是  |string |          |
| params .type     |是  |string | 订阅类型类型   |
| params .product     |是  |string | 币对       |
| event     |是  |string | 事件 Subscribe      |
| zip     |是  |bool | 是否启用gzip |

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

|参数名|必选|类型| 说明       |
|:----    |:---|:----- |----------|
| params .biz | 是  |string |          |
| params .type     |是  |string | 订阅类型类型   |
| params .product     |是  |string | 币对       |
| params .interval     |是  |string | 周期       |
| event     |是  |string | 事件 Subscribe      |
| zip     |是  |bool | 是否启用gzip |


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

|参数名|类型|说明|
|:----    |:---|:----- |-----   |
| id | int | 无符号整数 此消息唯一id |
| type | string |  订阅类型 |
| interval     |string | 间隔  |
| product    |string | 币对|
| pairCode    |string | 忽略|
| data .price     |string | 价格 |
| data .vol     |string | 成交量 |
| data .ts     |int  | 时间戳 |
| data .direction     |string |  方向|
| data .id     |int |  成交id|


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

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| params .biz | 是  |string |   |
| params .type     |是  |string | 订阅类型  |
| params .product     |是  |string | 币对|
| params .interval     |是  |string | _周期_ |
| event     |是  |string | 事件 |
| zip     |是  |bool | 是否启用gzip |


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

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| params .biz | 是  |string |   |
| params .type     |是  |string | 订阅类型  |
| params .product     |是  |string | 币对|
| params .interval     |是  |string | _周期_ |
| event     |是  |string | 事件 |
| zip     |是  |bool | 是否启用gzip |



> unsub request

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


> unsub response

```json
{
    "biz": "market",
    "channel": "unsubscribe",
    "interval": "1",
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
    "interval": "1",
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

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| params .biz | 是  |string |   |
| params .type     |是  |string | 订阅类型  |
| params .product     |是  |string | 币对|
| event     |是  |string | 事件 |
| zip     |是  |bool | 是否启用gzip |

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

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| params .biz | 是  |string |   |
| params .type     |是  |string | 订阅类型  |
| params .product     |是  |string | 币对|
| params .pairCode     |是  |string | 币对(忽略)|
| event     |是  |string | 事件 |
| zip     |是  |bool | 是否启用gzip |

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


|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| params .biz | 是  |string |   |
| params .type     |是  |string | 订阅类型  |
| params .product     |是  |string | 币对|
| event     |是  |string | 事件 |
| zip     |是  |bool | 是否启用gzip |


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


|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| params .biz | 是  |string |   |
| params .type     |是  |string | 订阅类型  |
| params .product     |是  |string | 币对|
| event     |是  |string | 事件 |
| zip     |是  |bool | 是否启用gzip |


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

|参数名|类型|说明|
|:----    |:----- |-----   |
| type | string |  订阅类型 |
| ts     | int | 时间戳  |
| product    |string | 币对|
| msg    | string | 忽略|
| code    | int | 忽略|
| data .open     |string | 24小时前开始第一笔成交价格 |
| data .close    |string | 24小时最新成交价格 |
| data .low     |string | 24小时内最低成交价 |
| data .high     |string | 24小时内最高成交价 |
| data .vol     |string | 24小时内成交量 |
| data .turnOver     |string | 24小时内成交额 |
| data .count     | int | 24小时成交笔数 |
| data .change     | int | 24小时价格变化 |
| data .changePercent     | int | 24小时价格变化(百分比) |
| data .pairCode     |string | 忽略 |

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
| 参数名             | 必选  |类型| 说明       |
|:----------------|:----|:----- |----------|
| params.biz      | 是   |string |          |
| params.type     | 是   |string | 类型       |
| params.product | 是   |string | 币对       |
| params.interval | 是   |string | 周期       |
| params.from     | 是   |string | 开始时间     |
| params.to       | 是   |string | 结束时间     |
| event           | 是   |string | 事件       |
| zip             | 是   |bool | 是否启用gzip |


###### 返回结构

|参数名|类型|说明|
|:----    |:----- |-----   |
| biz | string |  行情 |
| ts     | int | 时间戳  |
| product    |string | 币对|
| interval    | string | 间隔 1day|
| event    | string | req |
| data .open     |string | 这根K线期间第一笔成交价 |
| data .close    |string | 这根K线期间末一笔成交价 |
| data .low     |string | 这根K线期间最低成交价 |
| data .high     |string | 这根K线期间最高成交价 |
| data .vol     |string | 这根K线期间成交量 |
| data .turnOver     |string | 这根K线期间成交额 |
| data .id     | int | 唯一且有序id |
| data .count     | int | 这根K线期间成交笔数 |

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

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
| params.biz | 是  |string |   |
| params.type     |否  |string | 类型 |
| params.product     |否  |string | 币对|
| event     |是  |string | 事件 |
| zip     |是  |bool | 是否启用gzip |

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

#### 返回参数

|参数名|类型|说明|
|:----    |:----- |-----   |
| biz | string |  行情 |
| type     | string | ticker  |
| ts     | int | 时间戳  |
| product    |string | 币对|
| event    | string | req |
| data .open     |string | 24小时前开始第一笔成交价格 |
| data .close    |string | 24小时最新成交价格 |
| data .low     |string | 24小时内最低成交价 |
| data .high     |string | 24小时内最高成交价 |
| data .vol     |string | 24小时内成交量 |
| data .turnOver     |string | 24小时内成交额 |
| data .count     | int | 24小时成交笔数 |
| data .change     | int | 24小时价格变化 |
| data .changePercent     | int | 24小时价格变化(百分比) |


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


# WEBSOCKET FEED PUBLIC V2

- `wss://ws.bg.exchange/v2/ws/`

## Request 字段说明 

|参数名|类型|必选| 说明   |参考值|
|:---- |:---|:----- |------|------|
| event | string | 是|  请求事件 | [事件](#events) |
| biz     |string | 是| 业务线  | [业务线](#bizs) |
| type    |string | 是| 业务类型 | [类型](#types) |
| product  |string | 是| 交易对	 |BTC_USDT|
| interval |string | 否| 频率 | 1min |
| zip     |bool | 是| 是否开启压缩	 |true,false |
| params |json  | 否| 业务参数 | 可以为空 |

## Response 字段说明 

|参数名|类型|必选| 说明   |参考值|
|:---- |:---|:----- |------|------|
| event | string | 是|  请求事件 | [事件](#events) |
| biz     |string | 是| 业务线  | [业务线](#bizs) |
| type    |string | 是| 业务类型 | [类型](#types) |
| product  |string | 是| 交易对	 |BTC_USDT|
| interval |string | 否| 频率 | 1min |
| zip     |bool | 是| 是否开启压缩	 |true,false |
| id |string  | 否| 消息唯一id |
| code |number  | 是| 错误码 | |
| stauts |string  | 是| 错误码状态 ||
| data |json  | 否| 业务数据 | 参考具体业务数据说明 |

## Event 列表

<a name="events"></a>

|Event 名称|类型|说明|
|:----    |:----- |-----   |
| sub    |string | 订阅事件,由客户端主动发起|
| unsub    |string | 取消订阅事件，由客户端主动发起 |
| req    |string | 请求数据事件，由客户端主动发起 |


## Biz 列表

<a name="bizs"></a>

|Biz 名称|类型|说明|
|:----    |:----- |-----   |
| market    |string | 现货行情|

## Type 列表
<a name="types"></a>

|Type 名称|类型|说明|
|:----    |:----- |-----   |
| fills    |string | 成交数据|
| candles    |string | K线数据|
| orderbook    |string | 订单薄|
| ticker    |string | 24小时ticker|
| percent10    |string | 有限档位深度|



## Candles Subscribe/UnSubscribe and Req

通过订阅或者请求获取K线(最新一根K线)数据的更新

**K线图间隔参数:**

 min -> 分钟; hour -> 小时; day -> 天; week -> 周; mon -> 月

- 1min
- 5min
- 15min
- 30min
- 1hour
- 4hour
- 1day
- 1week
- 1mon


**字段说明:**

- `id` 消息唯一id
- `open` 这根K线期间第一笔成交价
- `close` 这根K线期间末一笔成交价
- `low` 这根K线期间最低成交价
- `high` 这根K线期间最高成交价
- `turnOver` 这根K线期间成交额
- `vol` 这根K线期间成交量
- `seqId` 唯一且有序id
- `count` 这根K线期间成交笔数
- `interval` K线间隔
- `product` 交易对


#### Subscribe

> Subscribe request

```json
{
    "event": "sub",
    "biz": "market",
    "type": "candles",
    "product": "BTC_USDT",
    "interval": "15min",
    "zip": false
}

```

> Subscribe response

```json
{
    "biz": "market",
    "type": "candles",
    "ts": 1666851880448,
    "code": 200,
    "status": "OK",
    "event": "sub",
    "product": "BTC_USDT",
    "interval": "15min"
}

```


#### UnSubscribe

> UnSubscribe request

```json
{
    "event": "unsub",
    "biz": "market",
    "type": "candles",
    "product": "BTC_USDT",
    "interval": "15min",
    "zip": false
}

```

> UnSubscribe response

```json
{
    "biz": "market",
    "type": "candles",
    "ts": 1666851880448,
    "code": 200,
    "status": "OK",
    "event": "unsub",
    "product": "BTC_USDT",
    "interval": "15min"
}

```

#### Feed Stream 

> Feed Stream

```json
{
    "id": "1689144300",
    "biz": "market",
    "type": "candles",
    "data":
    {
        "id": 1689144300,
        "open": "3.7366",
        "close": "3.7366",
        "high": "3.7366",
        "low": "3.7366",
        "turnOver": "0",
        "vol": "0",
        "count": 0,
        "seqId": 112588635
    },
    "product": "BTC_USDT",
    "interval": "15min"
}

```

#### Request Candles

> Req request 

**参数说明:**

- `id` 每个K线消息的唯一id
- `from` 开始时间的unix时间戳
- `to` 结束时间的unix时间戳
- `interval` K线间隔
- `product` 交易对


```json
{
    "event": "req",
    "biz": "market",
    "type": "candles",
    "product": "BTC_USDT",
    "interval": "15min",
    "zip": false,
    "from": 1687561511,
    "to": 1688641511
}
```

> Req response

```json
{
    "biz": "market",
    "type": "candles",
    "ts": 1689133139813,
    "code": 200,
    "status": "OK",
    "data":
    [
        {
            "count": 505866,
            "turnOver": 471315.660750,
            "vol": 132286.14,
            "id": 1688107500,
            "high": 4.0584,
            "open": 3.354,
            "low": 3.0616,
            "close": 3.4575
        },
        {
            "count": 492245,
            "turnOver": 458095.923364,
            "vol": 128555.52,
            "id": 1688108400,
            "high": 4.0584,
            "open": 3.4575,
            "low": 3.0637,
            "close": 3.3665
        }
    ],
    "event": "req",
    "product": "BTC_USDT",
    "interval": "15min"
} 


```

----

##  Fills Subscribe/UnSubscribe

**字段说明:**

- `id` 消息唯一id
- `ts` 成交时间戳
- `direction` 成交方向
- `price` 成交价格
- `vol` 成交量


#### Subscribe

> Subscribe request

```json
{
    "event": "sub",
    "biz": "market",
    "type": "fills",
    "product": "BTC_USDT",
    "zip": false
}
```

> Subscribe response

```json
{
    "biz": "market",
    "type": "fills",
    "product": "BTC_USDT",
    "ts": 1690165577416,
    "code": 200,
    "status": "OK",
    "event": "sub"
}
```

#### UnSubscribe

> UnSubscribe request

```json

{
    "event": "unsub",
    "biz": "market",
    "type": "fills",
    "product": "BTC_USDT",
    "zip": false
}

```

> UnSubscribe response  

```json
{
    "biz": "market",
    "type": "fills",
    "ts": 1666851880448,
    "code": 200,
    "status": "OK",
    "event": "unsub",
    "product": "BTC_USDT"
}

```
#### Feed Stream 

> Feed Stream

```json
{
    "id": "310529",
    "biz": "market",
    "type": "fills",
    "data":
    [
        {
            "vol": "0.79",
            "ts": 1689152279117,
            "price": "3.4134",
            "direction": "buy",
            "id": 310529000
        }
    ],
    "product": "BTC_USDT"
} 
```

-----

## OrderBook Subscribe/UnSubscribe

#### Subscribe

> Subscribe request

```json
{
    "event": "sub",
    "biz": "market",
    "type": "orderbook",
    "product": "BTC_USDT",
    "interval": "0",
    "zip": false
}
```

> Subscribe response

```json
{
    "biz": "market",
    "type": "orderbook",
    "ts": 1666851880448,
    "code": 200,
    "status": "OK",
    "event": "sub",
    "product": "BTC_USDT",
    "interval": 0
}
```

#### UnSubscribe 
> UnSubscribe request

```json
{
    "event": "unsub",
    "biz": "market",
    "type": "orderbook",
    "product": "BTC_USDT",
    "interval": "0",
    "zip": false
}

```
> UnSubscribe response

```json
{
    "biz": "market",
    "type": "orderbook",
    "ts": 1666851880448,
    "code": 200,
    "status": "OK",
    "event": "unsub",
    "product": "BTC_USDT",
    "interval": 0
}

```

#### Feed Stream 

> Feed Stream

```json

{
    "id": "1689143926",
    "biz": "market",
    "type": "orderBook",
    "data":
    {
        "seqId": 112588640,
        "bids":
        [
            [
                "3.7366",
                "0.66"
            ],
            [
                "3.6866",
                "0.98"
            ],
            [
                "3.4666",
                "0.33"
            ],
            [
                "3.3766",
                "0.76"
            ],
            [
                "3.3666",
                "0.7"
            ],
            [
                "3.1966",
                "0.75"
            ],
            [
                "3.1766",
                "0.06"
            ],
            [
                "3.0666",
                "0.91"
            ],
            [
                "3.0266",
                "0.73"
            ]
        ],
        "asks":
        [
            [
                "3.9966",
                "0.9"
            ]
        ]
    },
    "product": "BTC_USDT",
    "interval": "0"
}


```
----

## Percent10 Subscribe/Unsubscribe

有限档深度信息


#### Subscribe

> Subscribe request

```json
{
    "event": "sub",
    "biz": "market",
    "type": "percent10",
    "product": "BTC_USDT",
    "zip": false
}
```

> Subscribe response

```json
{
    "biz": "market",
    "type": "percent10",
    "ts": 1666851880448,
    "code": 200,
    "status": "OK",
    "event": "sub",
    "product": "BTC_USDT"
}
```
#### UnSubscribe

> UnSubscribe request

```json
{
    "event": "unsub",
    "biz": "market",
    "type": "percent10",
    "product": "BTC_USDT",
    "zip": false
}
```

> UnSubscribe response

```json
{
    "biz": "market",
    "type": "percent10",
    "product": "BTC_USDT",
    "ts": 1690193555943,
    "code": 200,
    "status": "OK",
    "event": "unsub"
}
```


#### Feed Stream 

> Feed Stream

```json

{
    "id": "1689143539",     //消息唯一id
    "biz": "market",
    "seqId": 112588640,     //唯一有序id
    "type": "percent10",    //业务类型
    "data":
    {
        "bids":             //买方
        [
            [
                "3.8646667",//价格
                "0"         //数量
            ]
        ],
        "asks":             //卖方
        [
            [
                "3.8685333",//价格
                "0"         //数量
            ],
            [
                "3.8704666",
                "0"
            ]
        ],
        "seqId": 112588640
    },
    "product": "BTC_USDT"
}
 
```

----


##  Ticker Subscribe/UnSubscribe and Req

**字段说明:**

- `id` 消息唯一id
- `open` 24小时前开始第一笔成交价格
- `close` 24小时最新成交价格
- `low` 24小时内最低成交价
- `high` 24小时内最高成交价
- `turnOver` 24小时内成交额
- `vol` 24小时内成交量
- `seqId` 唯一且有序id
- `count` 24小时成交笔数
- `change` 24小时价格变化
- `changePercent` 24小时价格变化(百分比)



#### Subscribe

> Subscribe request

```json
{
    "event": "sub",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "zip": false
}	
```


> Subscribe response

```json
{
    "biz": "market",
    "type": "ticker",
    "ts": 1666851880448,
    "code": 200,
    "status": "OK",
    "event": "sub",
    "product": "BTC_USDT"
}
```

#### UnSubscribe

> UnSubscribe request

```json
{
    "event": "unsub",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "zip": false
}
```


> UnSubscribe response

```json
{
    "biz": "market",
    "type": "ticker",
    "ts": 1689946788754,
    "code": 200,
    "status": "OK",
    "event": "unsub",
    "product": "BTC_USDT"
}
```
#### Feed Stream 

> Feed Stream

```json

{
    "id": "1689144487",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "data":
    [
        {
            "id": 1689144487,
            "seqId": 112588640,
            "open": "3.7366",
            "close": "3.7366",
            "high": "3.7366",
            "low": "3.7366",
            "turnOver": "0",
            "vol": "0",
            "count": 0,
            "change": "0",
            "changePercent": "0"
        }
    ]
}
```

#### Request Ticker

> Req request


```json
{
    "event": "req",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "zip": false
}

```

> Req response


```json
{
    "biz": "market",
    "type": "ticker",
    "ts": 1689133337870,
    "code": 200,
    "status": "OK",
    "data":
    {
        "id": 1689133336,
        "seqId": 112588640,
        "open": "3.7366",
        "close": "3.7366",
        "high": "3.7366",
        "low": "3.7366",
        "turnOver": "0",
        "vol": "0",
        "count": 0,
        "change": "0",
        "changePercent": "0"
    },
    "event": "req",
    "product": "BTC_USDT"
}

```

----






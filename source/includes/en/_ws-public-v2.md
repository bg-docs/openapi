# WEBSOCKET FEED PUBLIC V2

- `wss://ws.bg.exchange/v2/ws`

## Request Field Description

| Field Name | Type | Required | Description | Sample Value |
|:---------- |:---- |:------- |:----------- |:------------ |
| event | string | Yes | Request event | [Event](#events) |
| biz | string | Yes | Business line | [Business Line](#bizs) |
| type | string | Yes | Business type | [Type](#types) |
| product | string | Yes | Trading pair | BTC_USDT |
| interval | string | No | Frequency | 1min |
| zip | bool | Yes | Enable compression | true, false |
| params | json | No | Business parameters | Can be empty |

## Response Field Description

| Field Name | Type | Required | Description | Sample Value |
|:---------- |:---- |:------- |:----------- |:------------ |
| event | string | Yes | Request event | [Event](#events) |
| biz | string | Yes | Business line | [Business Line](#bizs) |
| type | string | Yes | Business type | [Type](#types) |
| product | string | Yes | Trading pair | BTC_USDT |
| interval | string | No | Frequency | 1min |
| zip | bool | Yes | Enable compression | true, false |
| id | string | No | Unique message ID |
| code | number | Yes | Error code | |
| status | string | Yes | Error code status | |
| data | json | No | Business data | See specific business data description for reference |

## Event List

<a name="events"></a>

|Event Name|Type|Description|
|:---------|:---|:----------|
| sub | string | Subscribe event, initiated by the client |
| unsub | string | Unsubscribe event, initiated by the client |
| req | string | Request data event, initiated by the client |

## Biz List

<a name="bizs"></a>

|Biz Name|Type|Description|
|:-------|:---|:----------|
| market | string | Spot market |

## Type List

<a name="types"></a>

|Type Name|Type|Description|
|:--------|:---|:----------|
| fills | string | Trade fills data |
| candles | string | K-line data |
| orderbook | string | Order book |
| ticker | string | 24-hour ticker |
| percent10 | string | Top 10 depth |




## Candles Subscribe/Unsubscribe and Req

Subscribe or request to get updates of K-line (latest candle) data.

**K-line interval parameters:**

min -> minutes; hour -> hours; day -> days; week -> weeks; mon -> months

- 1min
- 5min
- 15min
- 30min
- 1hour
- 4hour
- 1day
- 1week
- 1mon

**Field Description:**

- `id` Unique message ID
- `open` The first traded price during this candle period
- `close` The last traded price during this candle period
- `low` The lowest traded price during this candle period
- `high` The highest traded price during this candle period
- `turnOver` The total turnover during this candle period
- `vol` The total trading volume during this candle period
- `seqId` Unique and ordered ID
- `count` The number of trades during this candle period
- `interval` K-line interval
- `product` Trading pair


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

**Parameter Description:**

- `id` Unique ID for each K-line message
- `from` Unix timestamp of the start time
- `to` Unix timestamp of the end time
- `interval` K-line interval
- `product` Trading pair


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

**Field Description:**

- `id` Unique message ID
- `ts` Timestamp of the trade
- `direction` Trade direction
- `price` Trade price
- `vol` Trade volume


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

Depth information of the order book with a specific level of depth.


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
    "id": "1689143539",     //Unique message ID
    "biz": "market",
    "seqId": 112588640,     //Unique and sequential ID
    "type": "percent10",    //Business type
    "data":
    {
        "bids":             //Buyer
        [
            [
                "3.8646667",//Price
                "0"         //Amount
            ]
        ],
        "asks":             //Seller
        [
            [
                "3.8685333",//Price
                "0"         //Amount
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

- `id` Unique message ID
- `open` The first traded price 24 hours ago
- `close` The latest traded price in the last 24 hours
- `low` The lowest traded price in the last 24 hours
- `high` The highest traded price in the last 24 hours
- `turnOver` Total turnover in the last 24 hours
- `vol` Total trading volume in the last 24 hours
- `seqId` Unique and sequential ID
- `count` Total number of trades in the last 24 hours
- `change` Price change in the last 24 hours
- `changePercent` Price change percentage in the last 24 hours



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






<h1 id="v2-public-ws">WEBSOCKET public channel V2</h1>

- [Public channel V2 address](#WS_HOST_PUBLIC_V2)

**sequence number `seq_id` description**

1. `seq_id` is a serial number of the exchange market. When a user uses one or more WebSockets to connect to the same channel, in addition to the real-time transaction data, he will receive data pushes with the same serial number, and the user needs to handle the duplication by himself. data, a `seq_id` can be used to build a sequence of messages, which will allow the user to detect packet loss and ordering of messages.

2. `seq_id` is a monotonically increasing number with a minimum value of 0.


<h2 id="v2-public-candles">K-line channel</h2>


Subscribe or request to get K-line (the latest K-line) data push

**K-line chart interval parameters:**

min -> minute; hour -> hour; day -> day; week -> week; mon -> month

- 1min
- 5min
- 15min
- 30min
- 60min
- 4 hours
- 1 day
- 1week
- 1mon


**Field Description:**

- `id` message unique id
- `open` the first transaction price during this K-line period
- `close` the last transaction price during this K-line period
- `low` the lowest transaction price during this K-line period
- `high` is the highest transaction price during this K-line period
- `filled_size` the transaction volume during this K-line
- `vol` is the trading volume during this K-line
- `seq_id` unique and ordered id
- `count` is the number of transactions during this K-line period
- `interval` K-line interval
- `product` trading pair


**subscription**

> request example

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

> Response example

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


**unsubscribe**

> request example

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

> Response example

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

**Push data**

> Push data example

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
        "filled_size": "0",
        "vol": "0",
        "count": 0,
        "seq_id": 112588635
    },
    "product": "BTC_USDT",
    "interval": "15min"
}

```

**request data**

**Parameter Description:**

- `id` the unique id of each candlestick message
- ix timestamp of `from` start time
- ix timestamp of `to` end time
- `interval` K-line interval
- `product` trading pair

> Get the K-line data request example of the specified range

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

> Get the K-line data response example in the specified range

```json
{
    "biz": "market",
    "type": "candles",
    "product": "BTC_USDT",
    "ts": 1690252632272,
    "code": 200,
    "status": "OK",
    "data":
    [
        {
            "id": 1688398200,
            "open": "3.3706",
            "close": "3.3706",
            "high": "3.3706",
            "low": "3.3706",
            "filled_size": "0",
            "vol": "0",
            "count": 0
        },
        {
            "id": 1688399100,
            "open": "3.3706",
            "close": "3.3706",
            "high": "3.3706",
            "low": "3.3706",
            "filled_size": "0",
            "vol": "0",
            "count": 0
        }
    ],
    "event": "req",
    "interval": "15min"
}


```

----


<h2 id="v2-public-fills">Close channel</h2>


Subscribe to obtain real-time transaction incremental push data of products

Get the latest transaction data, and push the transaction data when there is transaction data. Each push may contain multiple transaction data.

**Field Description:**

- `id` message unique id
- `ts` transaction timestamp
- `direction` transaction direction
- `price` transaction price
- `vol` volume


**subscription**

> request example

```json
{
    "event": "sub",
    "biz": "market",
    "type": "fills",
    "product": "BTC_USDT",
    "zip": false
}
```

> Response example

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

**unsubscribe**

> request example

```json

{
    "event": "unsub",
    "biz": "market",
    "type": "fills",
    "product": "BTC_USDT",
    "zip": false
}

```

> Response example

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
**Push data**

> Push data example

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

<h2 id="v2-public-orderbook">Deep Channel</h2>


Subscribe to obtain product order book incremental push data

Push once every 500 milliseconds at the fastest, and also push when no event is triggered, bids and asks may be empty arrays if there is no data in the handicap

**OrderBook subscription interval parameters: [The current gear supports the maximum precision, the current gear supports the maximum depth]:**

- 0 : [0.0000000000000000001, 150]
- 1 : [0.00001, 150]
- 2 : [0.0001, 150]
- 3 : [0.001, 150]
- 4 : [0.01, 150]
- 5 : [0.1, 150]
- 6 : [0.0000000000000000001, 20]
- 7 : [0.00001, 20]
- 8 : [0.0001, 20]
- 9 : [0.001, 20]
- 10 : [0.01, 20]
- 11 : [0.1, 20]

Explanation: interval=5, the buyer's price in bids pushed can only be accurate to one decimal place, and the maximum array size of bids is 150


**Field Description:**

- `id` message unique id
- `biz` line of business
- `type` type
- `data.seq_id` is ignored
- `data.bids` buyers
- `data.bids[][0]` bid price
- `data.bids[][1]` number of buyers
- `data.asks` seller
- `data.asks[][0]` ask price
- `data.asks[][1]` number of sellers
- `data.product` trading pair
- `data.interval` slots



**subscription**

> request example

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

> Response example

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

**unsubscribe**
> request example

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
> Response example

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

**Push data**

> Push data example

```json

{
    "id": "1689143926",
    "biz": "market",
    "type": "orderbook",
    "data":
    {
        "seq_id": 112588640, //ordered and unique id
        "bids": //buyer
        [
            [
                "3.7366", //price
                "0.66" //quantity
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
        "asks": //Seller
        [
            [
                "3.9966", //price
                "0.9" //quantity
            ]
        ]
    },
    "product": "BTC_USDT",//trading pair
    "interval": "0"
}


```
----


<h2 id="v2-public-depth">Deep depth channel</h2>


Subscribe to obtain product depth map incremental push data

Explanation: Each buy and sell order takes up to 200 orders within 10% of the average price, sell 1 order within 10% of the upward price fluctuation, and buy 1 order within 10% downward fluctuation

Push once every 500 milliseconds at the fastest, and also push when no event is triggered, bids and asks may be empty arrays if there is no data in the handicap


**Field Description:**

- `id` message unique id
- `biz` line of business
- `seq_id` is ignored
- `type` type
- `data.bids` buyer depth
- `data.bids[][0]` Bid depth price
- `data.bids[][1]` the number of bids in depth
- `data.asks` depth of asks
- `data.asks[][0]` deep ask price
- `data.asks[][1]` depth number of asks
- `data.seq_id` ordered and unique id
- `data.product` trading pair


**subscription**

> request example

```json
{
    "event": "sub",
    "biz": "market",
    "type": "percent10",
    "product": "BTC_USDT",
    "zip": false
}
```

> Response example

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
**unsubscribe**

> request example

```json
{
    "event": "unsub",
    "biz": "market",
    "type": "percent10",
    "product": "BTC_USDT",
    "zip": false
}
```

> Response example

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


**Push data**

> Push data example

```json

{
    "id": "1689143539", //The unique id of the message
    "biz": "market",
    "seq_id": 112588640, //ordered and unique id
    "type": "percent10", //business type
    "data":
    {
        "bids": //buyer
        [
            [
                "3.8646667", //price
                "0" //quantity
            ]
        ],
        "asks": //Seller
        [
            [
                "3.8685333", //price
                "0" //quantity
            ],
            [
                "3.8704666",
                "0"
            ]
        ],
        "seq_id": 112588640
    },
    "product": "BTC_USDT"
}
 
```

----


<h2 id="v2-public-ticker">Quote channel</h2>


Obtain product 24-hour ticker incremental push data

**Field Description:**

- `id` message unique id
- `open` started the first transaction price 24 hours ago
- `close` 24 hours latest transaction price
- `low` The lowest transaction price within 24 hours
- `high` The highest transaction price within 24 hours
- `filled_size` turnover within 24 hours
- `vol` volume in 24 hours
- `seq_id` unique and ordered id
- `count` 24-hour transaction count
- `change` 24 hour price change
- `change_percent` 24h price change (percentage)



**subscription**

> request example

```json
{
    "event": "sub",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "zip": false
}
```


> Response example

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

**unsubscribe**

> request example

```json
{
    "event": "unsub",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "zip": false
}
```


> Response example

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
**Push data**

> Push data example

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
            "seq_id": 112588640,
            "open": "3.7366",
            "close": "3.7366",
            "high": "3.7366",
            "low": "3.7366",
            "filled_size": "0",
            "vol": "0",
            "count": 0,
            "change": "0",
            "change_percent": "0"
        }
    ]
}
```

**Request the latest market data for the specified trading pair**

> Get the latest market data request example for a specified trading pair


```json
{
    "event": "req",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "zip": false
}

```

> Example of getting the latest market data response for a specified trading pair


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
        "seq_id": 112588640,
        "open": "3.7366",
        "close": "3.7366",
        "high": "3.7366",
        "low": "3.7366",
        "filled_size": "0",
        "vol": "0",
        "count": 0,
        "change": "0",
        "change_percent": "0"
    },
    "event": "req",
    "product": "BTC_USDT"
}

```

<h2 id="v2-public-req-param">Public channel Request field description</h2>

| Parameter name | Type | Mandatory | Description | Reference value |
|:---------|:-------|:----|-----------|--------------|
| event | string | yes | request event | [event](#events) |
| biz | string | yes | line of business | [line of business](#bizs) |
| type | string | yes | business type | [type](#types) |
| product | string | yes | trading pair | BTC_USDT |
| interval | string | no | frequency | 1min |
| zip | bool | yes | whether to enable gzip | true, false |

<h2 id="v2-public-rep-param">Response field description of public channel</h2>


| Parameter name | Type | Mandatory | Description | Reference value |
|:---------|:-------|:----|---------|--------------|
| event | string | yes | request event | [event](#events) |
| biz | string | yes | line of business | [line of business](#bizs) |
| type | string | yes | business type | [type](#types) |
| product | string | yes | trading pair | BTC_USDT |
| interval | string | no | frequency | 1min |
| code | int | yes | error code | |
| status | string | yes | error code status | can be ignored |
| ts | long | yes | unix timestamp | ignorable |
| data | json | no | business data | refer to specific business data instructions |


<h2 id="v2-publilc-events">List of public channel events</h2>


| Event Name | Type | Description |
|:---------|:-------|-----------------|
| sub | string | Subscribe to events, initiated by the client |
| unsub | string | unsubscribe event, initiated by the client |
| req | string | request data event, initiated by the client |


<h2 id="v2-publilc-bizs">Public Channel Biz List</h2>

| Biz Name | Type | Description |
|:-------|:-------|------|
| market | string | spot market |



<h2 id="v2-publilc-types">List of Public Channel Types</h2>


| Type Name | Type | Description |
|:----------|:-------|------------|
| fills | string | transaction data |
| candles | string | candlestick data |
| orderbook | string | order book |
| ticker | string | 24 hour ticker |
| percent10 | string | depth |


----

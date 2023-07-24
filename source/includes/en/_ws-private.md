# WEBSOCKET FEED PRIVATE

- `wss://ws.bg.exchange/`


## Login

Authenticate the WS channel for users. Only authenticated channels can subscribe to user's asset information and order status change information.

### Subscribe

> request

```json
{
  "event": "login",
  "params": {
    "type": "api",
    "access-key": "de0535f81d51c998b7fbcf00f189f294",
    "access-sign": "sign",
    "access-timestamp": 14000000000
  }
}
```

#### Request Parameters

|Parameter Name|Required|Type| Description   |
|:----    |:---|:----- |------|
| params.type | Yes  |string | Authentication method: <br/>api: apiKey authentication; token: token authentication     |
| params.access-key     |Yes  |string | [Authentication Details](#auth)   |
| params.access-sign     |Yes  |string | [Authentication Details](#auth)    |
| params.access-timestamp     |Yes  |long | [Authentication Details](#auth)    |
| event     |Yes  |string | Event name [ Event List](#events)  |

> response

```json
{
    "result": "login",
    "data":
    {
        "result": true
    }
}
```

|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| result    |string | [Data Channel](#channels)|
| data.result     |bool | Whether the subscription is successful |

## Assets

Subscribe to user's asset changes. Currently, only subscription by product is supported. Subscription to full asset change information is under development.

### Subscribe

> request

```json
{
  "event": "sub",
  "params": {
    "biz": "exchange",
    "type": "assets",
    "product": "ETH_BTC",
    "zip": false
  }
}
```

#### Request Parameters

|Parameter Name|Required|Type| Description   |
|:----    |:---|:----- |------|
| params.biz | Yes  |string | [Subscription Module Type](#bizs)     |
| params.type     |Yes  |string | [Subscription Business Type](#types)  |
| params.product     |Yes  |string | Product information   |
| event     |Yes  |string | Event name [Event name Event List](#events)  |
| zip     |Yes  |bool | Whether to enable gzip|

> response

```json
{
  "channel": "subscribe",
  "biz": "exchange",
  "type": "assets",
  "product": "ETH_BTC",
  "data": {
    "result": false
  }
}
```

#### Response Parameters

|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| channel    |string | [Data Channel](#channels)|
| biz    |string | [Business Line](#bizs) |
| type | string |  [Protocol Type](#types) |
| product    |string | Product name|
| data.result     |bool | Whether the subscription is successful |

> feed

```json
{
  "biz": "exchange",
  "type": "assets",
  "product": "BTC_USDT",
  "zip": false,
  "data": [
    {
      "symbol": "BTC",
      "available": 100805.8,
      "hold": 13.2
    }
  ]
}
```

#### Feed Data

|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| channel    |string | [Data Channel](#channels)|
| biz    |string | [Business Line](#bizs) |
| type | string |  [Protocol Type](#types) |
| product    |string | Product name|
| $data.currency     |string | Currency name |
| $data.available     |bigdecimal | Available quantity |
| $data.hold     |bigdecimal | 	Hold quantity of currency|

## Orders

Subscribe to all order status changes.

### Subscribe

> request

```json
{
  "event": "sub",
  "params": {
    "biz": "exchange",
    "type": "orders",
    "product": "all",
    "zip": false
  }
}
```

#### Request Parameters

|Parameter Name|Required|Type| Description   |
|:----    |:---|:----- |------|
| params.biz | Yes  |string | [Subscription Module Type](#bizs)     |
| params.type     |Yes  |string | [Subscription Business Type](#types)  |
| params.product     |Yes  |string | Product information   |
| event     |Yes  |string | Event name [Event name Event List](#events)  |
| zip     |Yes  |bool | Whether to enable gzip |

> response

```json
{
  "channel": "subscribe",
  "biz": "exchange",
  "type": "orders",
  "product": "all",
  "data": {
    "result": true
  }
}
```

#### Response Parameters

|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| channel    |string | [Data Channel](#channels)|
| biz    |string | [Business Line](#bizs) |
| type | string |  [Protocol Type](#types) |
| product    |string | Product name|
| data.result     |bool | Whether the subscription is successful |
<aside>
RESPONSE PARAMETERS
</aside>

| Parameter Name | Description | Type | schema |
| -------- | -------- | ----- |----- | 
|order_id|Order ID|string||
|product|Product name|string||
|side| buy/sell |string||
|price|Price per unit of base currency|string||
|size|Quantity of base currency bought/sold|string||
|filled_amount|Filled quantity|string||
|funds|Quantity of quote currency used|string||
|filled_size| Filled amount |string||
|type|limit:limit: limit order / market: market order/|string||
|status|Status|string||

`status`: Trading status, value range 0-7

-0: Order received
-1: Order submitted
-2: Order partially filled
-3: Order fully filled
-4: Order initiated cancellation
-5: Order cancelled
-6: Order transaction failed
-7: Order reduced



> feed

```json
{
  "biz": "exchange",
  "type": "orders",
  "data": {
    "order_id": "124645019749408967",
    "product": "BTC_USDT",
    "side": "buy",
    "price": "60000",
    "size": "1",
    "filled_amount": "0",
    "funds": "1",
    "filled_size": "0",
    "type": "limit",
    "status": 0
  }
}
```

#### Feed Data

|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| channel    |string | [Data Channel](#channels)|
| biz    |string | [Business Line](#bizs) |
| type | string |  [Protocol Type](#types) |
| product    |string | Product name|
| $data    |object | [Order Details](#order_detail) |

## Event List

<a name="events"></a>

|Event 名称|Type|Description|
|:----    |:----- |-----   |
| sub    |string | Subscription event, initiated by the client|
| login    |string | Login event, initiated by the client |

## Business Line List

<a name="bizs"></a>

|Biz Name|Type|Description|
|:----    |:----- |-----   |
| exchange    |string | Spot trading|

## Protocol Type List

<a name="types"></a>

|Type Name|Type|Description|
|:----    |:----- |-----   |
| assets    |string | Asset changes|
| orders    |string | Order status changes|

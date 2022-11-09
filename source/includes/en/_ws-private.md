# WEBSOCKET FEED PRIVATE

- `wss://{host}/`


## Login

User authentication conducted through web socket channels. Only authenticated channels can process subscribers’ information on the assets and changes in order status.
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

#### Request parameters

|Parameter Name|Mandatory|Type| Description   |
|:----    |:---|:----- |------|
| params.type | Y  |string | Authentication method: `api`: apiKey authentication; `token`: token authentication     |
| params.access-key     |Y  |string | [Authentication Specifications](#Authentication Specifications)   |
| params.access-sign     |Y  |string | [Authentication Specifications](#Authentication Specifications)    |
| params.access-timestamp     |Y  |long | [Authentication Specifications](#Authentication Specifications)    |
| event     |Y  |string  | Event name [List of events](#events)  |

> response

```json
{
  "channel": "login",
  "data": {
    "result": true
  }
}
```

|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| result    |string | [Data channel](#channels)|
| data.result     |bool | Subscription successful or not |

## Assets

Subscription to the user’s balance changes. Only asset-based subscription is supported at the moment. Subscription to full asset change information is under development.
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

#### Request parameters

|Parameter Name|Mandatory|Type| Description   |
|:----    |:---|:----- |------|
| params.biz | Y  |string | [Subscription module type](#bizs)     |
| params.type     |Y  |string | [Subscription business type](#bizs)  |
| params.product     |Y  |string | Product information   |
| event     |Y  |string  | Event name [List of events](#events)  |
| zip     |Y  |bool | Enable GZIP or not |

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

#### Response parameters

|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| channel    |string | [Data channel](#channels)|
| biz    |string | [Subscription module type](#bizs) |
| type | string |  [Subscription business type](#bizs) |
| product    |string Product name|
| data.result     |bool | Subscription successful or not |

> feed

```json
{
  "biz": "exchange",
  "type": "assets",
  "product": "BTC_USDT",
  "zip": false,
  "data": [
    {
      "currency": "BTC",
      "available": 100805.8,
      "hold": 13.2
    }
  ]
}
```

#### 推送数据

|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| channel    |string | [Data channel](#channels)|
| biz    |string |[Subscription module type](#bizs) |
| type | string |  [Subscription business type](#bizs) |
| product    |string | Product name|
| $data.currency     |string | Currency name |
| $data.available     |bigdecimal | Name of available quantity |
| $data.hold     |bigdecimal | Name of currency and quantity on hold |

## Orders

Subscription to status changes of all orders

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

#### Request parameters

|Parameter Name|Mandatory|Type| Description   |
|:----    |:---|:----- |------|
| params.biz | Y  |string | [Subscription module type](#bizs)     |
| params.type     |Y  |string | [Subscription business type](#bizs)  |
| params.product     |Y  |string Product name   |
| event     |Y  |string  | Event name [List of events](#events)  |
| zip     |Y  |bool | Enable GZIP or not |

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

#### Response parameters

|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| channel    |string | [Data channel](#channels)|
| biz    |string |[Subscription module type](#bizs) |
| type | string |  [Subscription business type](#bizs) |
| product    |string Product name|
| data.result     |bool | Subscription successful or not |
<aside>
RESPONSE PARAMETERS
</aside>

| Parameter Name | Parameter Description | Type | schema |
| -------- | -------- | ----- |----- | 
|order_id|Order ID|string||
|product|Trading Pair|string||
|side| buy/sell |string||
|price|Price per unit of base currency|string||
|size|Quantity of base currency to buy/sell
Status|string||
|filled_amount|Amount of filled order|string||
|funds|The amount of quotation currency desired to use|string||
|filled_size| Value of filled order |string||
|type|limit: limit order/market: market order/|string||
|status|Status|string||

`status`: Transaction status, value range 0-7

- 0: Order received
- 1: Order submitted
- 2:  Order partially filled
- 3: Order fully filled
- 4: Order being cancelled
- 5: Order cancelled
- 6:  Order transaction failed
- 7: Order volume decreased



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

#### 推送数据

|Parameter Name|Type|Description|
|:----    |:----- |-----   |
| channel    |string | [Data channel](#channels)|
| biz    |string |[Subscription module type](#bizs) |
| type | string |  [Subscription business type](#bizs) |
| product    |string Product name|
| $data    |object | [Order details](#order_detail) |

<a name="events"></a>
## Event list

|Event name|Type|Description|
|:----    |:----- |-----   |
| sub    |string | Subscription event, initiated by the client|
| login    |string | Login event, initiated by the client |

<a name="bizs"></a>
## Biz list

|Biz Name|Type|Description|
|:----    |:----- |-----   |
| exchange    |string | Spot trading|

## Type list

<a name="types"></a>

|Type name|Type|Description|
|:----    |:----- |-----   |
| assets    |string | Change of asset|
| orders    |string | Change of order status|

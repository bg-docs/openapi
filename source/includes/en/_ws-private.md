# WEBSOCKET FEED PRIVATE

- `wss://{host}/`


## Login

进行WS通道用户认证。只有认证过的通道才可以进行订阅用户的资产信息以及订单状态变化信息

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
| params.type | Y  |string | 认证方式: <br/>`api`:apiKey认证;`token`:token认证     |
| params.access-key     |Y  |string | [Authentication Specifications](#auth)   |
| params.access-sign     |Y  |string | [Authentication Specifications](#auth)    |
| params.access-timestamp     |Y  |long | [Authentication Specifications](#auth)    |
| event     |Y  |string  | Event名 [事件列表](#events)  |

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
| result    |string | [数据频道](#channels)|
| data.result     |bool | 订阅是否成功 |

## Assets

订阅用户的资产变更。目前只支持按照产品进行订阅。订阅全量的资产变更信息正在开发中。

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
| params.biz | Y  |string | [订阅模块类型](#bizs)     |
| params.type     |Y  |string | [订阅业务类型](#types)  |
| params.product     |Y  |string | 产品信息   |
| event     |Y  |string  | Event名 [事件列表](#events)  |
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
| channel    |string | [数据频道](#channels)|
| biz    |string | [业务线](#bizs) |
| type | string |  [协议类型](#types) |
| product    |string | 产品名|
| data.result     |bool | 订阅是否成功 |

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
| channel    |string | [数据频道](#channels)|
| biz    |string | [业务线](#bizs) |
| type | string |  [协议类型](#types) |
| product    |string | 产品名|
| $data.currency     |string | 币种名称 |
| $data.available     |bigdecimal | 可用数量名称 |
| $data.hold     |bigdecimal | 冻结数量币种名称 |

## Orders

订阅所有订单的状态变化

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
| params.biz | Y  |string | [订阅模块类型](#bizs)     |
| params.type     |Y  |string | [订阅业务类型](#types)  |
| params.product     |Y  |string | 产品名   |
| event     |Y  |string  | Event名 [事件列表](#events)  |
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
| channel    |string | [数据频道](#channels)|
| biz    |string | [业务线](#bizs) |
| type | string |  [协议类型](#types) |
| product    |string | 产品名|
| data.result     |bool | 订阅是否成功 |
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
| channel    |string | [数据频道](#channels)|
| biz    |string | [业务线](#bizs) |
| type | string |  [协议类型](#types) |
| product    |string | 产品名|
| $data    |object | [订单详情](#order_detail) |

## Event 列表

<a name="events"></a>

|Event 名称|Type|Description|
|:----    |:----- |-----   |
| sub    |string | 订阅事件,由客户端主动发起|
| login    |string | 登录事件，由客户端主动发起 |

## Biz 列表

<a name="bizs"></a>

|Biz 名称|Type|Description|
|:----    |:----- |-----   |
| exchange    |string | 现货交易|

## Type 列表

<a name="types"></a>

|Type 名称|Type|Description|
|:----    |:----- |-----   |
| assets    |string | 资产变更|
| orders    |string | 订单状态变更|

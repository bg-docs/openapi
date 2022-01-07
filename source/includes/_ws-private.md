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

#### 请求参数

|参数名|必选|类型| 说明   |
|:----    |:---|:----- |------|
| params.type | 是  |string | 认证方式: <br/>`api`:apiKey认证;`token`:token认证     |
| params.access-key     |是  |string | [鉴权说明](#auth)   |
| params.access-sign     |是  |string | [鉴权说明](#auth)    |
| params.access-timestamp     |是  |long | [鉴权说明](#auth)    |
| event     |是  |string | 事件名 [事件列表](#events)  |

> response

```json
{
  "channel": "login",
  "data": {
    "result": true
  }
}
```

|参数名|类型|说明|
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

#### 请求参数

|参数名|必选|类型| 说明   |
|:----    |:---|:----- |------|
| params.biz | 是  |string | [订阅模块类型](#bizs)     |
| params.type     |是  |string | [订阅业务类型](#types)  |
| params.product     |是  |string | 产品信息   |
| event     |是  |string | 事件名 [事件列表](#events)  |
| zip     |是  |bool | 是否启用gzip |

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

#### 返回参数

|参数名|类型|说明|
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

|参数名|类型|说明|
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

#### 请求参数

|参数名|必选|类型| 说明   |
|:----    |:---|:----- |------|
| params.biz | 是  |string | [订阅模块类型](#bizs)     |
| params.type     |是  |string | [订阅业务类型](#types)  |
| params.product     |是  |string | 产品名   |
| event     |是  |string | 事件名 [事件列表](#events)  |
| zip     |是  |bool | 是否启用gzip |

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

#### 返回参数

|参数名|类型|说明|
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
  "type": "orders",
  "pairCode": "all",
  "data": {
    "id": 555,
    "orderId": "124645019749408967",
    "pairCode": "BTC_USDT",
    "side": "buy",
    "entrustPrice": "60000",
    "amount": "1",
    "dealAmount": "0",
    "quoteAmount": "1",
    "dealQuoteAmount": "0",
    "systemOrderType": 0,
    "status": 0,
    "sourceInfo": "web",
    "createOn": 1636459652099,
    "relationOrderId": ""
  }
}
```

#### 推送数据

|参数名|类型|说明|
|:----    |:----- |-----   |
| channel    |string | [数据频道](#channels)|
| biz    |string | [业务线](#bizs) |
| type | string |  [协议类型](#types) |
| product    |string | 产品名|
| $data    |object | [订单详情](#order_detail) |

## Event 列表

<a name="events"></a>

|Event 名称|类型|说明|
|:----    |:----- |-----   |
| sub    |string | 订阅事件,由客户端主动发起|
| login    |string | 登录事件，由客户端主动发起 |

## Biz 列表

<a name="bizs"></a>

|Biz 名称|类型|说明|
|:----    |:----- |-----   |
| exchange    |string | 现货交易|

## Type 列表

<a name="types"></a>

|Type 名称|类型|说明|
|:----    |:----- |-----   |
| assets    |string | 资产变更|
| orders    |string | 订单状态变更|

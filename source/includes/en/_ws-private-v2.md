# WEBSOCKET PRIVATE V2

- [Private channel V2 address](#WS_HOST_PRIVATE_V2)

## V2 private channel login authentication

Login authentication is required before subscribing to a private channel. Only authenticated users can subscribe to the user's asset information and order status change information.

### Note: If no login authentication operation is performed, subscribing to a private channel will return an error message

> Login request example

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


> Login success response example [status code comparison table](#WSERR)

```json
{
  "ts": 1690364037503,
  "code": 200,
  "status": "OK",
  "event": "login"
}
```


> Login Failure Response Example [Error Code Comparison Table](#ERR2)

```json
{
  "ts": 1690368819855,
  "code": 40001,
  "status": "ACCESS_KEY cannot be empty",
  "event": "login"
}
```

#### Login request parameter description

| parameter name          | required | type   | description                                               |
|:------------------------|:---------|:-------|-----------------------------------------------------------|
| params.type             | Yes      | string | Authentication method: <br/>`api`: apiKey authentication; |
| params.access-key       | Yes      | string | [Authentication Description](#auth)                       |
| params.access-sign      | Yes      | string | [Authentication Description](#auth)                       |
| params.access-timestamp | is       | long   | [authentication description](#auth)                       |
| event                   | yes      | string | event name [event list](#events)                          |



#### Login response parameter description

| parameter name | type | description |
|:-------|:-------|----------------------|
| event | string | event name [event list](#events) |
| status | string | status information |
| code | int | status code [status code comparison table](#WSERR) |
| ts | long | unix timestamp |




## V2 Private Channel Assets

Subscriber's asset changes will be pushed only when there is data update. Currently only supports subscription by product.

Please refer to [Common Request Parameter Description](#v2-req-param) and [General Response Parameter Description](#v2-rep-param) for request and response parameter description

### Subscribe to asset data

> Subscription request example

```json
{
  "event": "sub",
  "biz": "exchange",
  "type": "assets",
  "product": "ETH_USDT",
  "zip": false
}
```

> Subscription success response example

```json
{
  "biz": "exchange",
  "type": "assets",
  "product": "ETH_USDT",
  "ts": 1690357632710,
  "code": 200,
  "status": "OK",
  "event": "sub"
}
```


> Subscription failure response example [Error code comparison table](#WSERR)

```json
{
  "biz": "exchange",
  "type": "assets",
  "product": "ETH_USDT",
  "ts": 1690362052646,
  "code": 500,
  "status": "FAIL",
  "event": "sub"
}
```

> Asset push data example, this example is just to illustrate the data structure, the actual push data may only contain asset information of one currency

```json

{
  "biz": "exchange",
  "type": "assets",
  "product": "ETH_USDT",
  "data":
  [
    {
      "symbol": "USDT",
      "available": "999970.5238",
      "hold": "29.4762"
    },
    {
      "symbol": "ETH",
      "available": "999970.5238",
      "hold": "29.4762"
    }
  ]
}

```

<aside>
Asset push data field description
</aside>


| parameter name | type | description |
|:----------------|:-------|---------|
| product | string | product name/trading pair |
| $data.symbol | string | currency name |
| $data.available | string | available quantity |
| $data.hold | string | hold amount |


### Request the user's asset data for a single trading pair


> Request a single trading pair asset data example

```json
{
  "event": "req",
  "biz": "exchange",
  "type": "assets",
  "product": "BTC_USDT",
  "zip": false
}
```
> Request a single transaction pair asset data response example

```json
{
  "biz": "exchange",
  "type": "assets",
  "product": "BTC_USDT",
  "ts": 1690357632710,
  "code": 200,
  "status": "OK",
  "event": "req",
  "data":
  [
    {
      "symbol": "USDT",
      "available": "999970.5238",
      "hold": "29.4762"
    },
    {
      "symbol": "BTC",
      "available": "999970.5238",
      "hold": "29.4762"
    }
  ]
}
```

> Response example for failed request [Error code comparison table](#WSERR)

```json
{
  "biz": "exchange",
  "type": "assets",
  "product": "BTC_USDT",
  "ts": 1690376130387,
  "code": 500,
  "status": "FAIL",
  "event": "req"
}
```


<aside>
Request Asset Data Field Descriptions
</aside>


| parameter name | type | description |
|:----------------|:-------|---------|
| product | string | product name/trading pair |
| ts | long | unix timestamp |
| $data.symbol | string | currency name |
| $data.available | string | available quantity |
| $data.hold | string | hold amount |

## V2 private channel order

The status change of the subscription user's order will be pushed only when there is data update. Currently supports order status change subscription for all trading pairs. Supports asynchronous query of the user's current entrusted order data for a single trading pair.

Please refer to [Common Request Parameter Description](#v2-req-param) and [General Response Parameter Description](#v2-rep-param) for request and response parameter description

**Note: The order data supports subscribing to the full amount of trading pairs. When subscribing to orders for all trading pairs at once, please note that the `type` parameter uses `orders`, and the `product` parameter uses `all` (ignoring case)**


**Subscription order transaction pair order data**

**Subscribe to order data for all trading pairs**

> Subscription order trading pair order request example

```json
{
  "event": "sub",
  "biz": "exchange",
  "type": "orders",
  "product": "ETH_USDT",
  "zip": false
}
```
> Subscribe to all trading pairs order request example

```json
{
  "event": "sub",
  "biz": "exchange",
  "type": "orders",
  "product": "all",
  "zip": false
}
```

> Subscription order transaction pair order response success example

```json
{
  "biz": "exchange",
  "type": "orders",
  "product": "ETH_USDT",
  "ts": 1690363716709,
  "code": 200,
  "status": "OK",
  "event": "sub"
}
```

> Subscribe to all transaction pairs order response success example

```json
{
  "biz": "exchange",
  "type": "orders",
  "product": "all",
  "ts": 1690363716709,
  "code": 200,
  "status": "OK",
  "event": "sub"
}
```

> Example of Order Failure Response for Subscription Order [Error Code Comparison Table](#WSERR)

```json
{
  "biz": "exchange",
  "type": "orders",
  "product": "ETH_USDT",
  "ts": 1690362052646,
  "code": 500,
  "status": "FAIL",
  "event": "sub"
}
```

> Subscribe to all trading pairs order data failure response example [error code comparison table](#WSERR)

```json
{
  "biz": "exchange",
  "type": "orders",
  "product": "all",
  "ts": 1690362052646,
  "code": 500,
  "status": "FAIL",
  "event": "sub"
}
```

> Subscription order trading pair push order data example

```json
{
  "biz": "exchange",
  "type": "orders",
  "product": "BTC_USDT",
  "data":
  [
    {
      "orders_id": "179577241915696235",
      "product": "BTC_USDT",
      "side": "buy",
      "price": "3.53340000",
      "size": "1.00000000",
      "filled_amount": "0.00000000",
      "funds": "1.00000000",
      "filled_size": "0.00000000",
      "type": "limit",
      "status": "1"
    }
  ]
}
```


> Subscribe to all trading pairs to push orders and send data examples

```json
{
  "biz": "exchange",
  "type": "orders",//Note that this is different from a single trading pair
  "product": "all",//Note that this is different from a single trading pair
  "data":
  [
    //....Structure reference single transaction pair push order data example
  ]
}
```


**Request a single transaction pair for the current entrusted order data, if the request fails, a failed response will be returned. **

> Request the user's single transaction pair current entrusted order data example

```json
{
  "event": "req",
  "biz": "exchange",
  "type": "orders",
  "product": "BTC_USDT",
  "zip": false
}
```

> Response example for failed request [Error code comparison table](#WSERR)

```json
{
  "biz": "exchange",
  "type": "orders",
  "product": "BTC_USDT",
  "ts": 1690376130387,
  "code": 500,
  "status": "FAIL",
  "event": "req"
}
```


> An example of a successful response to requesting a single transaction from the user for the current entrusted order data

```json
{
  "biz": "exchange",
  "type": "orders",
  "product": "BTC_USDT",
  "ts": 1690375715106,
  "code": 200,
  "status": "OK",
  "data":
  [
    //....Structure reference single transaction pair push order data example
  ],
  "event": "req"
}
```

<aside>
Description of order data fields, please ignore other fields other than this description
</aside>

| Parameter name | Parameter description                    | Type   |
|:---------------|:-----------------------------------------|--------|
| orders_id      | order ID                                 | string |
| product        | commodity                                | string |
| side           | buy/sell                                 | string |
| price          | price per unit of base currency          | string |
| size           | Amount of base currency to buy/sell      | string |
| filled_amount  | filled amount                            | string ||
| funds          | Amount of quote currency to use          | string |
| filled_size    | transaction amount                       | string |
| type           | limit: limit order/market: market order/ | string |
| status         | status                                   | string |

`status`: transaction status, value range 0-7

- 0: order has been received
- 1: The order has been submitted
- 2: The order is partially executed
- 3: The order has been completely filled
- 4: The order is canceled
- 5: The order has been canceled
- 6: Order transaction failed
- 7: The order is reduced



----



## V2 private channel general request parameter description
<a name="v2-req-param"></a>

| parameter name | required | type | description |
|:----------|:----|:-------|---------------------|
| biz | is | string | [subscription module type](#bizs) |
| type | yes | string | [subscription business type](#types) |
| product | yes | string | product information |
| event | yes | string | event name [event list](#events) |
| zip | yes | bool | whether to enable gzip |


## V2 Private Channel General Response Parameter Description
<a name="v2-rep-param"></a>

| Parameter name | Type | Mandatory | Description | Reference value |
|:-------|:-------|:----|---------|------------- -|
| event | string | yes | request event | [event](#events) |
| biz | string | yes | line of business | [line of business](#bizs) |
| type | string | yes | business type | [type](#types) |
| product | string | yes | trading pair | BTC_USDT |
| code | number | yes | error code | |
| status | string | yes | error code status ||
| ts | long | yes | unix timestamp | |


## V2 private channel Event list

<a name="v2-private-events"></a>

| Event Name | Type   | Description                                  |
|:-----------|:-------|----------------------------------------------|
| sub        | string | Subscribe to events, initiated by the client |
| login      | string | login event, initiated by the client         |
| unsub      | string | unsubscribe event, initiated by the client   |

## V2 Private Channel Biz List

<a name="v2-private-bizs"></a>

| Biz Name | Type   | Description      |
|:---------|:-------|------------------|
| exchange | string | spot transaction |

## V2 private channel Type list

<a name="v2-private-types"></a>

| Type Name | Type   | Description         | Whether to support data push subscription for all trading pairs |
|:----------|:-------|---------------------|:----------------------------------------------------------------|
| assets    | string | asset changes       | no                                                              |
| orders    | string | order status change | yes                                                             |

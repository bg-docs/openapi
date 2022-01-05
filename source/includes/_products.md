# Products

## 获取所有已知的交易产品

**GET**: `/products`


<aside>
RESPONSE STATUS
</aside>

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request | [参考示例](#ResonpseExample1)
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

`base_currency`: 基础资产名

`quote_currency` : 计价资产名

`display_name`: 交易产品展示名，下单时，作为交易产品唯一标识

`status` : 交易产品状态
- `on`: 已上线，该产品开放交易，可以正常下单交易。
- `off`: 已下线。该产品关闭一切交易，已经存在挂单的订单，会被系统自动撤销。
- `pause`: 交易暂停，该产品关闭一些交易，但已经存在的挂单，不会被取消


`maxBuyPriceRate`: 限价买入价不能高于最新价格的比率，超过比率，订单下单失败。

`maxSellPriceRate`: 限价卖单不可以低于最新价格的比率。超过比率，订单下单失败。

`maxTradeUsdPerOrder`: 限价每笔订单最大下单金额。该金额会被折合成`美元`进行计算。

`minTradeUsdPerOrder`: 限价每笔订单最小下单金额。该金额会被折合成`美元`进行计算。

`maxMarketTradeUsdPerOrder`: 市价单笔最大下单金额。该金额会被折合成`美元`进行计算。

`minMarketTradeUsdPerOrder` : 市价单笔最小下单金额。该金额会被折合成`美元`进行计算。

| 参数名称 | 参数说明 | 类型 | schema |
| -------- | -------- | ----- |----- | 
|base_currency|基础资产|string||
|display_name|显示名称|string||
|maxBuyPriceRate|买入价格不能高于最新价(%)|string||
|maxSellPriceRate|卖出价格不能低于最新价(%)|string||
|maxTradeUsdPerOrder|单笔最大下单金额|string||
|minMarketTradeUsdPerOrder|单笔最小下单金额|string||
|maxMarketTradeUsdPerOrder|单笔最大下单金额|string||
|minTradeUsdPerOrder|单笔最小下单金额|string||
|status|状态|string||


> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
[
  {
    "id": "ETH_USD",
    "base_currency": "ETH",
    "quote_currency": "USD",
    "display_name": "ETH_USD",
    "status": "on",
    "maxBuyPriceRate": "1.000000",
    "maxSellPriceRate": "1.000000",
    "maxTradeUsdPerOrder": "",
    "minTradeUsdPerOrder": "",
    "maxMarketTradeUsdPerOrder": "",
    "minMarketTradeUsdPerOrder": ""
  }
]
```

## 获取单个产品详情

**GET**: `/products/{product_id}`


<aside>
RESPONSE STATUS
</aside>

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request | [参考示例](#ResonpseExample1)
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

`base_currency`: 基础资产名

`quote_currency` : 计价资产名

`display_name`: 交易产品展示名，下单时，作为交易产品唯一标识

`status` : 交易产品状态
- `on`: 已上线，该产品开放交易，可以正常下单交易。
- `off`: 已下线。该产品关闭一切交易，已经存在挂单的订单，会被系统自动撤销。
- `pause`: 交易暂停，该产品关闭一些交易，但已经存在的挂单，不会被取消


`maxBuyPriceRate`: 限价买入价不能高于最新价格的比率，超过比率，订单下单失败。

`maxSellPriceRate`: 限价卖单不可以低于最新价格的比率。超过比率，订单下单失败。

`maxTradeUsdPerOrder`: 限价每笔订单最大下单金额。该金额会被折合成`美元`进行计算。

`minTradeUsdPerOrder`: 限价每笔订单最小下单金额。该金额会被折合成`美元`进行计算。

`maxMarketTradeUsdPerOrder`: 市价单笔最大下单金额。该金额会被折合成`美元`进行计算。

`minMarketTradeUsdPerOrder` : 市价单笔最小下单金额。该金额会被折合成`美元`进行计算。

| 参数名称 | 参数说明 | 类型 | schema |
| -------- | -------- | ----- |----- | 
|base_currency|基础资产|string||
|display_name|显示名称|string||
|maxBuyPriceRate|买入价格不能高于最新价(%)|string||
|maxSellPriceRate|卖出价格不能低于最新价(%)|string||
|maxTradeUsdPerOrder|单笔最大下单金额|string||
|minMarketTradeUsdPerOrder|单笔最小下单金额|string||
|maxMarketTradeUsdPerOrder|单笔最大下单金额|string||
|minTradeUsdPerOrder|单笔最小下单金额|string||
|status|状态|string||


> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
[
  {
    "id": "ETH_USD",
    "base_currency": "ETH",
    "quote_currency": "USD",
    "display_name": "ETH_USD",
    "status": "on",
    "maxBuyPriceRate": "1.000000",
    "maxSellPriceRate": "1.000000",
    "maxTradeUsdPerOrder": "",
    "minTradeUsdPerOrder": "",
    "maxMarketTradeUsdPerOrder": "",
    "minMarketTradeUsdPerOrder": ""
  }
]
```


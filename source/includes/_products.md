# 产品

<h2 id="获取所有已知的交易产品">GET  获取所有已知的交易产品</h2>

获取所有的交易产品信息

**限速：无**

**限速规则：无**

**HTTP请求**

GET [HOST](#HTTP-HOST)/v1/products

<a id="Products"></a>


> <a name="ResonpseExample">RESPONSE EXAMPLE</a>

```json
[
  {
    "product": "ETH_USD",
    "base_currency": "ETH",
    "quote_currency": "USD",
    "display_name": "ETH_USD",
    "status": "on",
    "maker_fees_rate": "0.01",
    "taker_fees_rate": "0.02",
    "quote_precision": "5",
    "trade_precision": "8",
    "amount_precision": "6",
    "max_buy_price_rate": "1.000000",
    "max_sell_price_rate": "1.000000",
    "max_trade_usd_per_order": "",
    "min_trade_usd_per_order": "",
    "max_market_taker_trade_rate": "1.000000",
    "min_market_taker_trade_rate": "1.000000",
    "max_market_trade_usd_per_order": "",
    "min_market_trade_usd_per_order": ""
  }
]
```

<aside>
RESPONSE PARAMETERS

</aside>

`product`: 商品

`base_currency`: 基础资产名

`quote_currency` : 计价资产名

`display_name`: 交易产品展示名，下单时，作为交易产品唯一标识

`status` : 交易产品状态
- `on`: 已上线，该产品开放交易，可以正常下单交易。
- `off`: 已下线。该产品关闭一切交易，已经存在挂单的订单，会被系统自动撤销。
- `pause`: 交易暂停，该产品关闭一些交易，但已经存在的挂单，不会被取消


`amount_precision`: 交易货币数量单位精度

`quote_precision`: 计价货币数量单位精度

`trade_precision`: 交易货币价格单位精度

`maker_fees_rate`: 卖单方费率

`taker_fees_rate`: 买单方费率

`max_buy_price_rate`: 限价买入价不能高于最新价格的比率，超过比率，订单下单失败。

`max_sell_price_rate`: 限价卖单不可以低于最新价格的比率。超过比率，订单下单失败。

`max_trade_usd_per_order`: 限价每笔订单最大下单金额。该金额会被折合成`美元`进行计算。

`min_trade_usd_per_order`: 限价每笔订单最小下单金额。该金额会被折合成`美元`进行计算。

`max_market_taker_trade_rate`: 市价买入价不能高于最新价格的比率，超过比率，订单下单失败。

`min_market_taker_trade_rate` : 市价卖单不可以低于最新价格的比率。超过比率，订单下单失败。

`max_market_trade_usd_per_order` : 市价单笔最小下单金额。该金额会被折合成`美元`进行计算。

`min_market_trade_usd_per_order` : 市价单笔最小下单金额。该金额会被折合成`美元`进行计算。

| 参数名称 | 参数说明 | 类型 | 
| -------- | -------- | ----- | 
|product|商品|string|
|base_currency|基础资产|string|
|quote_currency|计价资产名|string|
|display_name|显示名称|string|
|amount_precision|交易货币数量单位精度|string|
|quote_precision|计价货币数量单位精度|string|
|trade_precision|	交易货币价格单位精度|string|
|maker_fees_rate|卖单方费率|string|
|taker_fees_rate|买单方费率|string|
|max_buy_price_rate|买入价格不能高于最新价(%)|string|
|max_sell_price_rate|卖出价格不能低于最新价(%)|string|
|max_trade_usd_per_order|单笔最大下单金额|string|
|min_trade_usd_per_order|单笔最小下单金额|string|
|max_market_taker_trade_rate|买单成交价格上限(%)|string|
|min_market_taker_trade_rate|买单成交价格下限(%)|string|
|max_market_trade_usd_per_order|单笔最大下单金额|string|
|min_market_trade_usd_per_order|单笔最小下单金额|string|
|status|状态|string|





<h2 id="获取单个产品详情">GET  获取单个产品详情</h2>

获取指定的交易产品信息

**限速：无**

**限速规则：无**

**HTTP请求**

GET [HOST](#HTTP-HOST)/v1/products/{product}

 
<aside>
REQUEST PARAMETERS
</aside>

| 参数名称 | 参数说明 | 是否必须 | 数据类型 | 
| -------- | -------- | -------- | -------- | 
|product|商品，例:ETH_USD|true|string|

> <a name="ResonpseExample">RESPONSE EXAMPLE</a>

```json
[
  {
    "product": "ETH_USD",
    "base_currency": "ETH",
    "quote_currency": "USD",
    "display_name": "ETH_USD",
    "status": "on",
    "maker_fees_rate": "0.01",
    "taker_fees_rate": "0.02",
    "quote_precision": "5",
    "trade_precision": "8",
    "amount_precision": "6",
    "max_buy_price_rate": "1.000000",
    "max_sell_price_rate": "1.000000",
    "max_trade_usd_per_order": "",
    "min_trade_usd_per_order": "",
    "max_market_taker_trade_rate": "1.000000",
    "min_market_taker_trade_rate": "1.000000",
    "max_market_trade_usd_per_order": "",
    "min_market_trade_usd_per_order": ""
  }
]
```


<aside>
RESPONSE PARAMETERS
</aside>

`product`: 商品

`base_currency`: 基础资产名

`quote_currency` : 计价资产名

`display_name`: 交易产品展示名，下单时，作为交易产品唯一标识

`status` : 交易产品状态
- `on`: 已上线，该产品开放交易，可以正常下单交易。
- `off`: 已下线。该产品关闭一切交易，已经存在挂单的订单，会被系统自动撤销。
- `pause`: 交易暂停，该产品关闭一些交易，但已经存在的挂单，不会被取消


`amount_precision`: 交易货币数量单位精度

`quote_precision`: 计价货币数量单位精度

`trade_precision`: 交易货币价格单位精度

`maker_fees_rate`: 卖单方费率

`taker_fees_rate`: 买单方费率

`max_buy_price_rate`: 限价买入价不能高于最新价格的比率，超过比率，订单下单失败。

`max_sell_price_rate`: 限价卖单不可以低于最新价格的比率。超过比率，订单下单失败。

`max_trade_usd_per_order`: 限价每笔订单最大下单金额。该金额会被折合成`美元`进行计算。

`min_trade_usd_per_order`: 限价每笔订单最小下单金额。该金额会被折合成`美元`进行计算。

`max_market_taker_trade_rate`: 市价买入价不能高于最新价格的比率，超过比率，订单下单失败。

`min_market_taker_trade_rate` : 市价卖单不可以低于最新价格的比率。超过比率，订单下单失败。

`max_market_trade_usd_per_order` : 市价单笔最小下单金额。该金额会被折合成`美元`进行计算。

`min_market_trade_usd_per_order` : 市价单笔最小下单金额。该金额会被折合成`美元`进行计算。

| 参数名称 | 参数说明 | 类型 | 
| -------- | -------- | -----| 
|product|商品|string|
|base_currency|基础资产|string|
|quote_currency|计价资产名|string|
|display_name|显示名称|string|
|amount_precision|交易货币数量单位精度|string|
|quote_precision|计价货币数量单位精度|string|
|trade_precision|	交易货币价格单位精度|string|
|maker_fees_rate|卖单方费率|string|
|taker_fees_rate|买单方费率|string|
|max_buy_price_rate|买入价格不能高于最新价(%)|string|
|max_sell_price_rate|卖出价格不能低于最新价(%)|string|
|max_trade_usd_per_order|单笔最大下单金额|string|
|min_trade_usd_per_order|单笔最小下单金额|string|
|max_market_taker_trade_rate|买单成交价格上限(%)|string|
|min_market_taker_trade_rate|买单成交价格下限(%)|string|
|max_market_trade_usd_per_order|单笔最大下单金额|string|
|min_market_trade_usd_per_order|单笔最小下单金额|string|
|status|状态|string|




# 產品

<h2 id="獲取所有已知的交易產品">GET  獲取所有已知的交易產品</h2>

獲取所有的交易產品信息

**限速：無**

**限速規則：無**

**HTTP請求**

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

`base_currency`: 基礎資產名

`quote_currency` : 計價資產名

`display_name`: 交易產品展示名，下單時，作為交易產品唯一標識

`status` : 交易產品狀態
- `on`: 已上線，該產品開放交易，可以正常下單交易。
- `off`: 已下線。該產品關閉一切交易，已經存在掛單的訂單，會被系統自動撤銷。
- `pause`: 交易暫停，該產品關閉一些交易，但已經存在的掛單，不會被取消


`amount_precision`: 交易貨幣數量單位精度

`quote_precision`: 計價貨幣數量單位精度

`trade_precision`: 交易貨幣價格單位精度

`maker_fees_rate`: 賣單方費率

`taker_fees_rate`: 買單方費率

`max_buy_price_rate`: 限價買入價不能高於最新價格的比率，超過比率，訂單下單失敗。

`max_sell_price_rate`: 限價賣單不可以低於最新價格的比率。超過比率，訂單下單失敗。

`max_trade_usd_per_order`: 限價每筆訂單最大下單金額。該金額會被折合成`美元`進行計算。

`min_trade_usd_per_order`: 限價每筆訂單最小下單金額。該金額會被折合成`美元`進行計算。

`max_market_taker_trade_rate`: 市價買入價不能高於最新價格的比率，超過比率，訂單下單失敗。

`min_market_taker_trade_rate` : 市價賣單不可以低於最新價格的比率。超過比率，訂單下單失敗。

`max_market_trade_usd_per_order` : 市價單筆最小下單金額。該金額會被折合成`美元`進行計算。

`min_market_trade_usd_per_order` : 市價單筆最小下單金額。該金額會被折合成`美元`進行計算。

| 參數名稱 | 參數說明 | 類型 | 
| -------- | -------- | ----- | 
|product|商品|string|
|base_currency|基礎資產|string|
|quote_currency|計價資產名|string|
|display_name|顯示名稱|string|
|amount_precision|交易貨幣數量單位精度|string|
|quote_precision|計價貨幣數量單位精度|string|
|trade_precision|	交易貨幣價格單位精度|string|
|maker_fees_rate|賣單方費率|string|
|taker_fees_rate|買單方費率|string|
|max_buy_price_rate|買入價格不能高於最新價(%)|string|
|max_sell_price_rate|賣出價格不能低於最新價(%)|string|
|max_trade_usd_per_order|單筆最大下單金額|string|
|min_trade_usd_per_order|單筆最小下單金額|string|
|max_market_taker_trade_rate|買單成交價格上限(%)|string|
|min_market_taker_trade_rate|買單成交價格下限(%)|string|
|max_market_trade_usd_per_order|單筆最大下單金額|string|
|min_market_trade_usd_per_order|單筆最小下單金額|string|
|status|狀態|string|





<h2 id="獲取單個產品詳情">GET  獲取單個產品詳情</h2>

獲取指定的交易產品信息

**限速：無**

**限速規則：無**

**HTTP請求**

GET [HOST](#HTTP-HOST)/v1/products/{product}


<aside>
REQUEST PARAMETERS
</aside>

| 參數名稱 | 參數說明 | 是否必須 | 數據類型 | 
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

`base_currency`: 基礎資產名

`quote_currency` : 計價資產名

`display_name`: 交易產品展示名，下單時，作為交易產品唯一標識

`status` : 交易產品狀態
- `on`: 已上線，該產品開放交易，可以正常下單交易。
- `off`: 已下線。該產品關閉一切交易，已經存在掛單的訂單，會被系統自動撤銷。
- `pause`: 交易暫停，該產品關閉一些交易，但已經存在的掛單，不會被取消


`amount_precision`: 交易貨幣數量單位精度

`quote_precision`: 計價貨幣數量單位精度

`trade_precision`: 交易貨幣價格單位精度

`maker_fees_rate`: 賣單方費率

`taker_fees_rate`: 買單方費率

`max_buy_price_rate`: 限價買入價不能高於最新價格的比率，超過比率，訂單下單失敗。

`max_sell_price_rate`: 限價賣單不可以低於最新價格的比率。超過比率，訂單下單失敗。

`max_trade_usd_per_order`: 限價每筆訂單最大下單金額。該金額會被折合成`美元`進行計算。

`min_trade_usd_per_order`: 限價每筆訂單最小下單金額。該金額會被折合成`美元`進行計算。

`max_market_taker_trade_rate`: 市價買入價不能高於最新價格的比率，超過比率，訂單下單失敗。

`min_market_taker_trade_rate` : 市價賣單不可以低於最新價格的比率。超過比率，訂單下單失敗。

`max_market_trade_usd_per_order` : 市價單筆最小下單金額。該金額會被折合成`美元`進行計算。

`min_market_trade_usd_per_order` : 市價單筆最小下單金額。該金額會被折合成`美元`進行計算。

| 參數名稱 | 參數說明 | 類型 | 
| -------- | -------- | -----| 
|product|商品|string|
|base_currency|基礎資產|string|
|quote_currency|計價資產名|string|
|display_name|顯示名稱|string|
|amount_precision|交易貨幣數量單位精度|string|
|quote_precision|計價貨幣數量單位精度|string|
|trade_precision|	交易貨幣價格單位精度|string|
|maker_fees_rate|賣單方費率|string|
|taker_fees_rate|買單方費率|string|
|max_buy_price_rate|買入價格不能高於最新價(%)|string|
|max_sell_price_rate|賣出價格不能低於最新價(%)|string|
|max_trade_usd_per_order|單筆最大下單金額|string|
|min_trade_usd_per_order|單筆最小下單金額|string|
|max_market_taker_trade_rate|買單成交價格上限(%)|string|
|min_market_taker_trade_rate|買單成交價格下限(%)|string|
|max_market_trade_usd_per_order|單筆最大下單金額|string|
|min_market_trade_usd_per_order|單筆最小下單金額|string|
|status|狀態|string|

# Products and Quotations

## Obtaining All Known Trading Products

<font class="httpget">GET</font> */v1/products*


<aside>
RESPONSE PARAMETERS

</aside>

`product`:  Trading Pair

`base_currency`: Name of the base currency

`quote_currency` : Name of quote currency

`display_name`: Display name of the trading product, which is the unique identifier of the trading product when placing an order

`status` : Status of the trading product
- `on`: Product is online. The product is open for trading and can be traded normally.
- `off`: Product is offline. All transactions of the product are closed, and pending orders will be automatically cancelled by the system.
- `pause`: Transaction suspended. Some transactions of the product are closed, but existing pending orders will not be canceled.


`amount_precision`: Precision of amount unit of the quote currency

`quote_precision`: Precision of amount unit of the quotation currency

`trade_precision`:  Precision of pricing unit of the trading currency

`maker_fees_rate`: Rate of maker fees

`taker_fees_rate`: Rate of taker fees

`max_buy_price_rate`: Percentage of the best bid that the buying price of a limit order cannot exceed. Placement of order will fail if the percentage is exceeded.

`max_sell_price_rate`: Percentage of the best ask that the selling price of a limit order cannot be lower than. Placement of order will fail if the percentage is exceeded.

`max_trade_usd_per_order`: The maximum order amount per limit order. This amount will be converted into `USD` for calculation.

`min_trade_usd_per_order`: he minimum order amount per limit order. This amount will be converted into `USD` for calculation.

`max_market_taker_trade_rate`: Percentage of the best bid that the buying price of a market order cannot exceed. Placement of order will fail if the percentage is exceeded.

`min_market_taker_trade_rate` : Percentage of the best ask that the selling price of a market order cannot be lower than. Placement of order will fail if the percentage is exceeded.

`max_market_trade_usd_per_order` : The maximum order amount per market order. This amount will be converted into `USD` for calculation.

`min_market_trade_usd_per_order` : The minimum order amount per market order. This amount will be converted into `USD` for calculation.

| Parameter Name | Parameter Description | Type | schema |
| -------- | -------- | ----- |----- | 
|product|Trading Pair|string||
|base_currency|Base asset|string||
|quote_currency|Name of quote currency|string||
|display_name|Display name|string||
|amount_precision|Precision of amount unit of the trading currency|string||
|quote_precision|Precision of amount unit of the quotation currency|string||
|trade_precision|	Precision of pricing unit of the trading currency|string||
|maker_fees_rate|Rate of maker fees|string||
|taker_fees_rate|Rate of taker fees|string||
|max_buy_price_rate|Bid price cannot exceed latest price (%)|string||
|max_sell_price_rate|Ask price cannot be lower than latest price (%)|string||
|max_trade_usd_per_order|Maximum amount per order|string||
|min_trade_usd_per_order|Minimum amount per order|string||
|max_market_taker_trade_rate|Upper limit of transaction price of buying order (%)|string||
|min_market_taker_trade_rate|Lower limit of transaction price of buying order (%)|string||
|max_market_trade_usd_per_order|Maximum amount per order|string||
|min_market_trade_usd_per_order|Minimum amount per order|string||
|status|Status|string||


> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

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


## Obtaining Details of a Particular Trading Product

<font class="httpget">GET</font> */v1/products/{product}*



<aside>
RESPONSE PARAMETERS
</aside>

`product`: Trading Pair

`base_currency`: Base asset

`quote_currency` : Name of quote currency

`display_name`: Display name of the trading pair, which is the unique identifier of the trading product when placing an order

`status` : Status of the trading product
- `on`: Product is online. The product is open for trading and can be traded normally.
- `off`: Product is offline. All transactions of the product are closed, and pending orders will be automatically cancelled by the system.
- `pause`: Transaction suspended. Some transactions of the product are closed, but existing pending orders will not be canceled.


`amount_precision`: Precision of amount unit of the trading currency 

`quote_precision`: Precision of amount unit of the quotation currency

`trade_precision`: Precision of pricing unit of the trading currency

`maker_fees_rate`: Rate of maker fees

`taker_fees_rate`: Rate of taker fees

`max_buy_price_rate`: Percentage of the best bid that the buying price of a limit order cannot exceed. Placement of order will fail if the percentage is exceeded.

`max_sell_price_rate`: Percentage of the best ask that the selling price of a limit order cannot be lower than. Placement of order will fail if the percentage is exceeded.

`max_trade_usd_per_order`: The maximum order amount per limit order. This amount will be converted into `USD` for calculation.

`min_trade_usd_per_order`: The minimum order amount per limit order. This amount will be converted into `USD` for calculation.

`max_market_taker_trade_rate`: Percentage of the best bid that the buying price of a market order cannot exceed. Placement of order will fail if the percentage is exceeded.

`min_market_taker_trade_rate` : Percentage of the best ask that the selling price of a market order cannot be lower than. Placement of order will fail if the percentage is exceeded.

`max_market_trade_usd_per_order` : The maximum order amount per market order. This amount will be converted into `USD` for calculation.

`min_market_trade_usd_per_order` : The minimum order amount per market order. This amount will be converted into `USD` for calculation.

| Parameter Name | Parameter Description | Type | schema |
| -------- | -------- | ----- |----- | 
|product|Trading Pair|string||
|base_currency|Base asset|string||
|quote_currency|Name of quote currency|string||
|display_name|Display name|string||
|amount_precision|Precision of amount unit of the trading currency|string||
|quote_precision|Precision of amount unit of the quotation currency|string||
|trade_precision|	Precision of pricing unit of the trading currency|string||
|maker_fees_rate|Rate of maker fees|string||
|taker_fees_rate|Rate of taker fees|string||
|max_buy_price_rate|Bid price cannot exceed latest price (%)|string||
|max_sell_price_rate|Ask price cannot be lower than latest price (%)|string||
|max_trade_usd_per_order|Maximum amount per order|string||
|min_trade_usd_per_order|Minimum amount per order|string||
|max_market_taker_trade_rate|Upper limit of transaction price of buying order (%)|string||
|min_market_taker_trade_rate|Lower limit of transaction price of buying order (%)|string||
|max_market_trade_usd_per_order|Maximum amount per order|string||
|min_market_trade_usd_per_order|Minimum amount per order|string||
|status|Status|string||


> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

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


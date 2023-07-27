# Product

<h2 id="Get all known trading products"><font class="httpget">GET</font> Get all known trading products</h2>

Get all trading product information

**Speed Limit: None**

**Speed limit rules: None**

**HTTP request**

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

`product`: product

`base_currency`: base asset name

`quote_currency` : quote asset name

`display_name`: The display name of the transaction product, which is used as the unique identifier of the transaction product when placing an order

`status` : trading product status
- `on`: has been launched, the product is open for trading, and orders can be placed and traded normally.
- `off`: offline. This product closes all transactions, and orders that already have pending orders will be automatically canceled by the system.
- `pause`: Trading is paused, the product closes some trades, but existing pending orders will not be canceled


`amount_precision`: transaction currency amount unit precision

`quote_precision`: Quotation currency quantity unit precision

`trade_precision`: trade currency price unit precision

`maker_fees_rate`: Maker fee rate

`taker_fees_rate`: taker fee rate

`max_buy_price_rate`: The rate at which the limit buy price cannot be higher than the latest price. If the rate exceeds the rate, the order will fail.

`max_sell_price_rate`: The rate at which a limit sell order cannot be lower than the latest price. If the ratio is exceeded, the order will fail to be placed.

`max_trade_usd_per_order`: The maximum order amount per order at the limit price. The amount will be converted into `USD` for calculation.

`min_trade_usd_per_order`: The minimum order amount per order at the limit price. The amount will be converted into `USD` for calculation.

`max_market_taker_trade_rate`: The rate at which the market buy price cannot be higher than the latest price. If the rate exceeds the rate, the order will fail.

`min_market_taker_trade_rate` : The rate at which market taker orders cannot be lower than the latest price. If the ratio is exceeded, the order will fail to be placed.

`max_market_trade_usd_per_order` : The minimum order amount for a single order at the market price. The amount will be converted into `USD` for calculation.

`min_market_trade_usd_per_order` : The minimum order amount for a single order at the market price. The amount will be converted into `USD` for calculation.

| Parameter name | Parameter description | Type |
| -------- | -------- | ----- |
|product|product|string|
|base_currency|base asset|string|
|quote_currency|Price asset name|string|
|display_name|display name |string|
|amount_precision|trading currency amount unit precision |string|
|quote_precision|quote currency quantity unit precision|string|
|trade_precision| trade currency price unit precision |string|
|maker_fees_rate|Seller fee rate|string|
|taker_fees_rate|taker fee rate|string|
|max_buy_price_rate|The buying price cannot be higher than the latest price (%)|string|
|max_sell_price_rate|The selling price cannot be lower than the latest price (%)|string|
|max_trade_usd_per_order|The maximum amount of a single order|string|
|min_trade_usd_per_order|Single minimum order amount|string|
|max_market_taker_trade_rate|The upper limit of taker trade price (%)|string|
|min_market_taker_trade_rate|Minimum limit of taker trade price (%)|string|
|max_market_trade_usd_per_order|The maximum amount of a single order|string|
|min_market_trade_usd_per_order|Single minimum order amount|string|
|status|status|string|





<h2 id="Get single product details"><font class="httpget">GET</font> Get single product details</h2>

Get the specified trading product information

**Speed Limit: None**

**Speed limit rules: None**

**HTTP request**

GET [HOST](#HTTP-HOST)/v1/products/{product}


<aside>
REQUEST PARAMETERS
</aside>

| Parameter name | Parameter description | Required | Data type |
| -------- | -------- | -------- | -------- |
|product|commodity, for example: ETH_USD|true|string|

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

`product`: product

`base_currency`: base asset name

`quote_currency` : quote asset name

`display_name`: The display name of the transaction product, which is used as the unique identifier of the transaction product when placing an order

`status` : trading product status
- `on`: has been launched, the product is open for trading, and orders can be placed and traded normally.
- `off`: offline. This product closes all transactions, and orders that already have pending orders will be automatically canceled by the system.
- `pause`: Trading is paused, the product closes some trades, but existing pending orders will not be canceled


`amount_precision`: transaction currency amount unit precision

`quote_precision`: Quotation currency quantity unit precision

`trade_precision`: trade currency price unit precision

`maker_fees_rate`: Maker fee rate

`taker_fees_rate`: taker fee rate

`max_buy_price_rate`: The rate at which the limit buy price cannot be higher than the latest price. If the rate exceeds the rate, the order will fail.

`max_sell_price_rate`: The rate at which a limit sell order cannot be lower than the latest price. If the ratio is exceeded, the order will fail to be placed.

`max_trade_usd_per_order`: The maximum order amount per order at the limit price. The amount will be converted into `USD` for calculation.

`min_trade_usd_per_order`: The minimum order amount per order at the limit price. The amount will be converted into `USD` for calculation.

`max_market_taker_trade_rate`: The rate at which the market buy price cannot be higher than the latest price. If the rate exceeds the rate, the order will fail.

`min_market_taker_trade_rate` : The rate at which market taker orders cannot be lower than the latest price. If the ratio is exceeded, the order will fail to be placed.

`max_market_trade_usd_per_order` : The minimum order amount for a single order at the market price. The amount will be converted into `USD` for calculation.

`min_market_trade_usd_per_order` : The minimum order amount for a single order at the market price. The amount will be converted into `USD` for calculation.

| Parameter name | Parameter description | Type |
| -------- | -------- | -----|
|product|product|string|
|base_currency|base asset|string|
|quote_currency|Price asset name|string|
|display_name|display name |string|
|amount_precision|trading currency amount unit precision |string|
|quote_precision|quote currency quantity unit precision|string|
|trade_precision| trade currency price unit precision |string|
|maker_fees_rate|Seller fee rate|string|
|taker_fees_rate|taker fee rate|string|
|max_buy_price_rate|The buying price cannot be higher than the latest price (%)|string|
|max_sell_price_rate|The selling price cannot be lower than the latest price (%)|string|
|max_trade_usd_per_order|The maximum amount of a single order|string|
|min_trade_usd_per_order|Single minimum order amount|string|
|max_market_taker_trade_rate|The upper limit of taker trade price (%)|string|
|min_market_taker_trade_rate|Minimum limit of taker trade price (%)|string|
|max_market_trade_usd_per_order|The maximum amount of a single order|string|
|min_market_trade_usd_per_order|Single minimum order amount|string|
|status|status|string|

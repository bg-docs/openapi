<h1 id="v2-public-market">Public Data V2</h1>

<h2 id="http-kline">GET Kline</h2>

Get K-line data. The K-line data is grouped and returned according to the requested granularity, and the most recent 2,000 K-line data can be retrieved.

**Speed Limit: None**

**Speed limit rules: None**

**HTTP request**

GET [HOST](#HTTP-HOST)/public/v2/products/{product}/candles


<aside>
REQUEST PARAMETERS
</aside>

| parameter name | required | type | description                                                                                                                                                                                 |
|:---------|:------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| product | true | string | path parameter commodity, such as: ETH_USD                                                                                                                                                  |
| interval | false | string | Default time granularity `1min` Reference value: [1min, 5min, 15min, 30min, 60min, 4hour, 1day, 1week, 1mon] For details, please refer to [K Line Channel Subscription](#v2-public-candles) |
| from | true | long | start time, request data after this timestamp (seconds)                                                                                                                                     |
| to | true | long | end time, the data (seconds) before the requested timestamp                                                                                                                                 |
| size | false | int | default 500, maximum 1000[1,1000]                                                                                                                                                           |


> <a name="candles-req-demo">REQUEST EXAMPLE</a>


```json

GET /public/v2/products/ETH_USDT/candles?interval=1min&from=1639584000&to=1639584000&size=100

```





> <a name="ResonpseExample">RESPONSE EXAMPLE</a>


```json
{
  "code": 200,
  "data":
  [
    {
      "id": 1690952460,
      "open": "3.5334",
      "close": "3.5334",
      "high": "3.5334",
      "low": "3.5334",
      "vol": "0",
      "count": 0,
      "filled_size": "0"
    },
    {
      "id": 1690952520,
      "open": "3.5334",
      "close": "3.5334",
      "high": "3.5334",
      "low": "3.5334",
      "vol": "0",
      "count": 0,
      "filled_size": "0"
    }
  ],
  "message": "OK"
}

```


<aside>
RESPONSE PARAMETERS
</aside>

| parameter name | type | description |
|:------------|:-------|:-------------|
| close | string | The last transaction price during this K-line period |
| high | string | The highest transaction price during this K-line |
| low | string | The lowest transaction price during this K-line period |
| open | string | The first transaction price during this K-line period |
| filled_size | string | turnover |
| count | int | The number of transactions during this k-line period |
| vol | string | volume |
| id | long | unique id |



<h2 id="http-orderbook">GET order book</h2>


Get Order-book data. Order-book data is sorted by price from high to low, and those with the same price are sorted by time.

**Speed Limit: None**

**Speed limit rules: None**

**HTTP request**

GET [HOST](#HTTP-HOST)/public/v2/products/{product}/orderbook


<aside>
REQUEST PARAMETERS
</aside>


| parameter name | required | type | description |
|:---------|:------|:-------|:----------------------------------------------------------------|
| product | true | string | path parameter commodity, such as: ETH_USD |
| interval | false | string | Indicator period Default value `0` Valid value range `0-11` Please refer to [Deep Channel Subscription](#v2-public-orderbook) |


> <a name="req-orderbook-demo">REQUEST EXAMPLE</a>


```http

GET /public/v2/products/ETH_USDT/orderbook?interval=0

```





> <a name="ResonpseExample">RESPONSE EXAMPLE</a>


```json
{
  "code": 200,
  "data":
  {
    "bids":
    [
      [
        "5", //price
        "3.6" //quantity
      ],
      [
        "3.5334",
        "3"
      ]
    ],
    "asks":
    [],
    "seq_id": 18867339
  },
  "message": "OK"
}

```


<aside>
RESPONSE PARAMETERS
</aside>

| parameter name | type | description |
|:-------|:-------|---------|
| seq_id | string | ordered and unique id |
| bids | [] | buyer |
| asks | [] | seller |


<h2 id="http-get-all-tickers">GET 24-hour market data of all currency pairs</h2>

Get all product market information

**Speed Limit: None**

**Speed limit rules: None**

**HTTP request**

GET [HOST](#HTTP-HOST)/public/v2/products/overview/tickers


> <a name="req-overview-demo">REQUEST EXAMPLE</a>


```http

GET /public/v2/products/overview/tickers

```


> <a name="ResonpseExample">RESPONSE EXAMPLE</a>

```json
{
  "code": 200,
  "data":
  [
    {
      "id": 1691132221,
      "product": "BTC_USDT",
      "open": "7.13",
      "close": "3.2713",
      "high": "7.13",
      "low": "2.9313",
      "vol": "1979.89",
      "count": 0,
      "change": "-3.8587",
      "seq_id": 22757,
      "filled_size": "6916.093957",
      "change_percent": "-0.5412"
    }
  ],
  "message": "OK"
}
```

<aside>
RESPONSE PARAMETERS
</aside>



| parameter name | type | description |
|:---------------|:-------|:---------------|
| close | int | 24-hour latest transaction price |
| high | int | The highest transaction price within 24 hours |
| low | int | The lowest transaction price within 24 hours |
| open | int | The first transaction price started 24 hours ago |
| filled_size | string | turnover within 24 hours |
| vol | string | Trading volume within 24 hours |
| change | string | 24 hour price change |
| change_percent | string | 24 hour price change (percentage) |
| seq_id | long | unique and ordered id |
| count | int | 24-hour transaction count |
| product | string | commodity, for example: ETH_USD |
| id | long | unique id |





<h2 id="http-get-ticker">GET single currency pair 24-hour market data</h2>

Obtain product market information

**Speed Limit: None**

**Speed limit rules: None**

**HTTP request**

GET [HOST](#HTTP-HOST)/public/v2/products/{product}/ticker


<aside>
REQUEST PARAMETERS
</aside>

| parameter name | required | type | description |
|:-------|:-----|:-------|-------------------|
| product | true | string | path parameter commodity, such as: ETH_USD |



> <a name="req-ticker-demo">REQUEST EXAMPLE</a>


```http

GET /public/v2/products/ETH_USDT/ticker

```

> <a name="ResonpseExample">RESPONSE EXAMPLE</a>


```json
{
  "code": 200,
  "data":
  {
    "id": 1691132024,
    "product": "ETH_USDT",
    "open": "7.13",
    "close": "3.2713",
    "high": "7.13",
    "low": "2.9313",
    "vol": "1979.89",
    "count": 0,
    "change": "-3.8587",
    "seq_id": 22757,
    "filled_size": "6916.093957",
    "change_percent": "-0.5412"
  },
  "message": "OK"
}
```

<aside>
RESPONSE PARAMETERS
</aside>


| parameter name | type | description |
|:---------------|:-------|:---------------|
| close | int | 24-hour latest transaction price |
| high | int | The highest transaction price within 24 hours |
| low | int | The lowest transaction price within 24 hours |
| open | int | The first transaction price started 24 hours ago |
| filled_size | string | turnover within 24 hours |
| vol | string | Trading volume within 24 hours |
| change | string | 24 hour price change |
| change_percent | string | 24 hour price change (percentage) |
| seq_id | long | unique and ordered id |
| count | int | 24-hour transaction count |
| product | string | commodity, for example: ETH_USD |
| id | long | unique id |


<h2 id="http-get-fiils">GET single currency pair real-time transaction data</h2>


Get the latest deals list for products

**Speed Limit: None**

**Speed limit rules: None**

**HTTP request**

GET [HOST](#HTTP-HOST)/public/v2/products/{product}/trades


<aside>
REQUEST PARAMETERS
</aside>

| parameter name | required | type | description                                                |
|:-------|:------|:-------|------------------------------------------------------------|
| product | true | string | path parameter commodity, such as: ETH_USD                 |
| size | false | int | size per request: default value `500` maximum value `1000` |



> <a name="req-fills-demo">REQUEST EXAMPLE</a>

```http

GET /public/v2/products/ETH_USDT/trades?size=1

```


> <a name="ResonpseExample">RESPONSE EXAMPLE</a>


```json
{
  "code": 200,
  "data":
  [
    {
      "vol": "0.1",
      "ts": 1691029846352,
      "price": "5",
      "direction": "sell",
      "id": 17078143
    }
  ],
  "message": "OK"
}
```

<aside>
RESPONSE PARAMETERS
</aside>

| parameter name | type | description |
|:----------|:-------|-----------------|
| direction | string | transaction direction buy / sell |
| price | string | transaction price |
| vol | string | volume |
| id | string | unique id |
| ts | long | transaction time stamp |


----

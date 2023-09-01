<h1 id="v2-public-market">公共數據V2</h1>

<h2 id="http-kline">GET  K線</h2>

獲取K線數據。 K線數據按請求的粒度分組返回，K線數據最多可獲取最近2,000條。

**限速：無**

**限速規則：無**

**HTTP請求**

GET [HOST](#HTTP-HOST)/public/v2/products/{product}/candles


<aside>
REQUEST PARAMETERS
</aside>

| 參數名      | 必選    | 類型     | 說明                                                                                                      |
|:---------|:------|:-------|:--------------------------------------------------------------------------------------------------------|
| product  | true  | string | 路徑參數 商品，如:ETH_USD                                                                                       |
| interval | false | string | 時間粒度默認值`1min` 參考值：[1min,5min,15min,30min,60min,4hour,1day,1week,1mon] 具體請參考[K線頻道訂閱](#v2-public-candles) |
| from     | true  | long   | 開始時間 ，請求此時間戳之後的數據(秒)                                                                                    |
| to       | true | long   | 結束時間 ，請求次時間戳之前的數據(秒)                                                                                    |
| size     | false | int    | 默認500 ，最大1000[1,1000]                                                                                   |


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

| 參數名         | 類型     | 說明           |
|:------------|:-------|:-------------|
| close       | string | 這根K線期間末一筆成交價 |
| high        | string | 這根K線期間最高成交價  |
| low         | string | 這根K線期間最低成交價  |
| open        | string | 這根K線期間第一筆成交價 |
| filled_size | string | 成交額          |
| count       | int    | 這根k線期間的成交筆數  |
| vol         | string | 成交量          |
| id          | long   | 唯一id         |



<h2 id="http-orderbook">GET  訂單book</h2>


獲取訂單簿（Order-book)數據。 Order-book數據按價格從高到低排序，價格相同的按照時間優先排序。

**限速：無**

**限速規則：無**

**HTTP請求**

GET [HOST](#HTTP-HOST)/public/v2/products/{product}/orderbook


<aside>
REQUEST PARAMETERS
</aside>


| 參數名      | 必選    | 類型     | 說明                                                            |
|:---------|:------|:-------|:--------------------------------------------------------------|
| product  | true  | string | 路徑參數 商品，如:ETH_USD                                             |
| interval | false | string | 指標週期 默認值 `0` 有效取值範圍 `0-11` 請參考 [深度頻道訂閱](#v2-public-orderbook) |


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
        "5",   //價格
        "3.6"  //數量
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

| 參數名    | 類型     | 說明      |
|:-------|:-------|---------|
| seq_id | string | 有序且唯一id |
| bids   | []     | 買方      |
| asks   | []     | 賣方      |


<h2 id="http-get-all-tickers">GET  全部幣對24小時行情數據</h2>

獲取所有產品行情信息

**限速：無**

**限速規則：無**

**HTTP請求**

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



| 參數名            | 類型     | 說明             |
|:---------------|:-------|:---------------|
| close          | int    | 24小時最新成交價格     |
| high           | int    | 24小時內最高成交價     |
| low            | int    | 24小時內最低成交價     |
| open           | int    | 24小時前開始第一筆成交價格 |
| filled_size    | string | 24小時內成交額       |
| vol            | string | 24小時內成交量       |
| change         | string | 24小時價格變化       |
| change_percent | string | 24小時價格變化(百分比)  |
| seq_id         | long   | 唯一且有序id        |
| count          | int    | 24小時成交筆數       |
| product        | string | 商品，例:ETH_USD   |
| id             | long   | 唯一id           |





<h2 id="http-get-ticker">GET  單幣對24小時行情數據</h2>

獲取產品行情信息

**限速：無**

**限速規則：無**

**HTTP請求**

GET [HOST](#HTTP-HOST)/public/v2/products/{product}/ticker


<aside>
REQUEST PARAMETERS
</aside>

| 參數名     | 必選   | 類型     | 說明                |
|:--------|:-----|:-------|-------------------|
| product | true | string | 路徑參數 商品，如:ETH_USD |



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


| 參數名            | 類型     | 說明             |
|:---------------|:-------|:---------------|
| close          | int    | 24小時最新成交價格     |
| high           | int    | 24小時內最高成交價     |
| low            | int    | 24小時內最低成交價     |
| open           | int    | 24小時前開始第一筆成交價格 |
| filled_size    | string | 24小時內成交額       |
| vol            | string | 24小時內成交量       |
| change         | string | 24小時價格變化       |
| change_percent | string | 24小時價格變化(百分比)  |
| seq_id         | long   | 唯一且有序id        |
| count          | int    | 24小時成交筆數       |
| product        | string | 商品，例:ETH_USD   |
| id             | long   | 唯一id           |


<h2 id="http-get-fiils">GET  單幣對實時成交數據</h2>


獲取產品的最新交易列表

**限速：無**

**限速規則：無**

**HTTP請求**

GET [HOST](#HTTP-HOST)/public/v2/products/{product}/trades


<aside>
REQUEST PARAMETERS
</aside>

| 參數名     | 必選    | 類型     | 說明                           |
|:--------|:------|:-------|------------------------------|
| product | true  | string | 路徑參數 商品，如:ETH_USD            |
| size    | false | int    | 每次請求的數量：默認值 `500` 最大值 `1000` |



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

| 參數名       | 類型     | 說明              |
|:----------|:-------|-----------------|
| direction | string | 成交方向 buy / sell |
| price     | string | 成交價格            |
| vol       | string | 成交量             |
| id        | string | 唯一id            |
| ts        | long   | 成交時間戳           |


----

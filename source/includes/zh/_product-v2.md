<h1 id="v2-public-market">公共数据V2</h1>

<h2 id="http-kline">GET  K线</h2>

获取K线数据。K线数据按请求的粒度分组返回，K线数据最多可获取最近2,000条。

**限速：无**

**限速规则：无**

**HTTP请求**

GET [HOST](#HTTP-HOST)/public/v2/products/{product}/candles

 
<aside>
REQUEST PARAMETERS
</aside>

| 参数名      | 必选    | 类型     | 说明                                                                                                         |
|:---------|:------|:-------|:-----------------------------------------------------------------------------------------------------------|
| product  | true  | string | 路径参数 商品，如:ETH_USD                                                                                          |
| interval | false | string | 时间粒度 默认值 `1min` 参考值：[1min,5min,15min,30min,60min,4hour,1day,1week,1mon] 具体请参考 [K线频道订阅](#v2-public-candles) |
| from     | true  | long   | 开始时间 ，请求此时间戳之后的数据(秒)                                                                                       |
| to       | true | long   | 结束时间 ，请求次时间戳之前的数据(秒)                                                                                       |
| size     | false | int    | 默认500 ，最大1000[1,1000]                                                                                      |


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

| 参数名         | 类型     | 说明           |
|:------------|:-------|:-------------|
| close       | string | 这根K线期间末一笔成交价 |
| high        | string | 这根K线期间最高成交价  |
| low         | string | 这根K线期间最低成交价  |
| open        | string | 这根K线期间第一笔成交价 |
| filled_size | string | 成交额          |
| count       | int    | 这根k线期间的成交笔数  |
| vol         | string | 成交量          |
| id          | long   | 唯一id         |



<h2 id="http-orderbook">GET  订单book</h2>


获取订单簿（Order-book)数据。Order-book数据按价格从高到低排序，价格相同的按照时间优先排序。

**限速：无**

**限速规则：无**

**HTTP请求**

GET [HOST](#HTTP-HOST)/public/v2/products/{product}/orderbook


<aside>
REQUEST PARAMETERS
</aside>


| 参数名      | 必选    | 类型     | 说明                                                            |
|:---------|:------|:-------|:--------------------------------------------------------------|
| product  | true  | string | 路径参数 商品，如:ETH_USD                                             |
| interval | false | string | 指标周期 默认值 `0` 有效取值范围 `0-11` 请参考 [深度频道订阅](#v2-public-orderbook) |


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
        "5",   //价格
        "3.6"  //数量
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

| 参数名    | 类型     | 说明      |
|:-------|:-------|---------|
| seq_id | string | 有序且唯一id |
| bids   | []     | 买方      |
| asks   | []     | 卖方      |


<h2 id="http-get-all-tickers">GET  全部币对24小时行情数据</h2>

获取所有产品行情信息

**限速：无**

**限速规则：无**

**HTTP请求**

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



| 参数名            | 类型     | 说明             |
|:---------------|:-------|:---------------|
| close          | int    | 24小时最新成交价格     |
| high           | int    | 24小时内最高成交价     |
| low            | int    | 24小时内最低成交价     |
| open           | int    | 24小时前开始第一笔成交价格 |
| filled_size    | string | 24小时内成交额       |
| vol            | string | 24小时内成交量       |
| change         | string | 24小时价格变化       |
| change_percent | string | 24小时价格变化(百分比)  |
| seq_id         | long   | 唯一且有序id        |
| count          | int    | 24小时成交笔数       |
| product        | string | 商品，例:ETH_USD   |
| id             | long   | 唯一id           |





<h2 id="http-get-ticker">GET  单币对24小时行情数据</h2>

获取产品行情信息

**限速：无**

**限速规则：无**

**HTTP请求**

GET [HOST](#HTTP-HOST)/public/v2/products/{product}/ticker


<aside>
REQUEST PARAMETERS
</aside>

| 参数名     | 必选   | 类型     | 说明                |
|:--------|:-----|:-------|-------------------|
| product | true | string | 路径参数 商品，如:ETH_USD |



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


| 参数名            | 类型     | 说明             |
|:---------------|:-------|:---------------|
| close          | int    | 24小时最新成交价格     |
| high           | int    | 24小时内最高成交价     |
| low            | int    | 24小时内最低成交价     |
| open           | int    | 24小时前开始第一笔成交价格 |
| filled_size    | string | 24小时内成交额       |
| vol            | string | 24小时内成交量       |
| change         | string | 24小时价格变化       |
| change_percent | string | 24小时价格变化(百分比)  |
| seq_id         | long   | 唯一且有序id        |
| count          | int    | 24小时成交笔数       |
| product        | string | 商品，例:ETH_USD   |
| id             | long   | 唯一id           |


<h2 id="http-get-fiils">GET  单币对实时成交数据</h2>


获取产品的最新交易列表

**限速：无**

**限速规则：无**

**HTTP请求**

GET [HOST](#HTTP-HOST)/public/v2/products/{product}/trades


<aside>
REQUEST PARAMETERS
</aside>

| 参数名     | 必选    | 类型     | 说明                           |
|:--------|:------|:-------|------------------------------|
| product | true  | string | 路径参数 商品，如:ETH_USD            |
| size    | false | int    | 每次请求的数量：默认值 `500` 最大值 `1000` |



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

| 参数名       | 类型     | 说明              |
|:----------|:-------|-----------------|
| direction | string | 成交方向 buy / sell |
| price     | string | 成交价格            |
| vol       | string | 成交量             |
| id        | string | 唯一id            |
| ts        | long   | 成交时间戳           |


----


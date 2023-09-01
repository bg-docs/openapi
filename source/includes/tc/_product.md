# ~~公共數據(DEPRECATED)~~

<h2 id="K線">GET  K線</h2>

歷史產品的k線圖， 數據以數組形式返回，每個對象保函[`close`，`count`，`high`，`low`，`open`，`turnOver`，`vol`]

**限速：無**

**限速規則：無**

**HTTP請求**

GET [HOST](#HTTP-HOST)/public/v1/products/{product}/candles


<aside>
REQUEST PARAMETERS
</aside>

|參數名| 必選    |類型| 說明                                                                                                                                                                     |
|:----    |:------|:----- |:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| product | true  |string | 路徑參數 商品，例:ETH_USD                                                                                                                                         商品，例:ETH_USD |
| period | true  |string | 指標週期 [1min,5min,15min,30min,60min,4hour,1day,1week,1mon]                                                                                                               |
|start     | true  |string | timestamp 毫秒                                                                                                                                                開始  (毫秒)   |
|end     | true  |string | 結束   (毫秒)                                                                                                                                                              |
|size     | false |string | 數據長度默認500 ，最大1000[1,1000]                                                                                                                                              |

> <a name="ResonpseExample">RESPONSE EXAMPLE</a>


```json 
  {
    "code": 200,
    "data": [
        {
            "close": 11.9,
            "count": 2,
            "high": 11.9,
            "id": 1639584000,
            "low": 11,
            "open": 11,
            "turnOver": 22.9,
            "vol": 2
        }
    ],
    "interval": "1day",
    "msg": "success",
    "productId": "ETH_USDT",
    "ts": 1639650753079
}

```


<aside>
RESPONSE PARAMETERS
</aside>

|參數名|類型|   說明 |
|:------|:----|:-----|
| close | int  |   收盤價格 |
| high | int  |   最高價格 |
| low | int  |   最低價格 |
| open | int  |  開盤價格 |
| turnOver | string  |  交易量 |
| vol | string  |  交易額 |
| productId | string  |  商品，例:ETH_USD  |





<h2 id="訂單book">GET  訂單book</h2>


訂單book

**限速：無**

**限速規則：無**

**HTTP請求**

GET [HOST](#HTTP-HOST)/public/v1/products/{product}/orderbook


<aside>
REQUEST PARAMETERS
</aside>


|參數名|必選|類型| 說明                                                            |
|:----    |:---|:----- |:--------------------------------------------------------------|
| product |true  |string | 路徑參數 商品，例:ETH_USD                                             |
| interval | true   |string | 指標週期  有效取值範圍 `step0-step11`請參考 [深度頻道訂閱](#v2-public-orderbook) |

> <a name="ResonpseExample">RESPONSE EXAMPLE</a>


```json 
{
	"interval": "step1",
	"status": "ok",
	"ts": 1641378313942,
	"type": "orderBook",
	"tick": {
		"seqId": 9996,
		"id": 1641378313,
		"bids": [
			[1, 65]
		],
		"asks": [
			[48349.99, 5.3795],
			[48562.27, 94.1076],
			[48998.82, 49.924],
			[49322.83, 15.03636],
			[49324.72, 8.1281],
			[49334.76, 82.7552],
			[49342.59, 44.9204],
			[49364.66, 28.5769],
			[49365.2, 6.2237],
			[49390.8, 44.7102],
			[49414.67, 92.3859],
			[49428.24, 46.7245],
			[49430.6, 66.2994],
			[49435.96, 68.4281],
			[49437.07, 20.5226],
			[49443.47, 51.3443],
			[49444.4, 73.2709],
			[49448.78, 41.5535],
			[49454.19, 77.954],
			[49458.74, 29.2196],
			[49477.83, 50.3074],
			[49492.03, 93.2679],
			[49500.02, 11.1431],
			[49506.89, 74.3294],
			[49519.14, 45.8255],
			[49525.62, 19.6835],
			[49538.88, 97.1741],
			[49544.83, 70.238],
			[49551.81, 38.3689],
			[49557.84, 69.0679],
			[49565.77, 55.5486],
			[49571.15, 55.1521],
			[49589.14, 83.2236],
			[49590.11, 1.5069],
			[49593.9, 45.1853],
			[49601.42, 21.826],
			[49602.74, 2.7914],
			[49609.3, 79.3817],
			[49615.55, 81.7304],
			[49653.07, 12.2331],
			[49662.5, 68.8741],
			[49675.13, 31.3474],
			[49686.03, 6.1158],
			[49690.92, 79.5905],
			[49699.37, 91.9541],
			[49719.33, 80.5142],
			[49724.29, 61.7956],
			[49726.37, 96.1342],
			[49752.36, 71.4982],
			[49769.78, 49.3641],
			[49785.77, 43.4184],
			[49815.95, 91.9892],
			[49820.16, 74.1338],
			[49847.76, 20.297],
			[49888.07, 76.3738],
			[49888.44, 8.6581],
			[49907.97, 12.634],
			[49932.43, 63.1484],
			[49951.37, 5.0352],
			[49952.08, 81.9681],
			[49958.58, 99.3703],
			[49977.74, 62.3056],
			[49986.53, 34.2252],
			[49998.03, 47.7642],
			[49998.3, 88.6624]
		],
		"ts": 1641378313486,
		"version": 1641378313,
		"type": "orderBook",
		"pairCode": "BTC_USDT",
		"interval": "1"
	}
}

```


<aside>
RESPONSE PARAMETERS
</aside>

| 參數名     |類型| 說明  |
|:--------|:----- |-----|
| interval   |string | 檔位  |
| status   |string | 狀態碼  |
| ts   |string | 時間戳  |
| type   |string | 類型  |
| seqId   |string | 有序且唯一id  |
| id   |string | 消息唯一id  |
| bids   |[] | 買方  |
| asks   |[] | 賣方  |
| pairCode   |string | 商品，例:ETH_USD  |

<h2 id="全部幣對24小時行情數據">GET  全部幣對24小時行情數據</h2>

行情總覽,獲取有關交易（報價變動）、最佳買價/賣價和 24 小時交易量的快照信息。

**限速：無**

**限速規則：無**

**HTTP請求**

GET [HOST](#HTTP-HOST)/public/v1/products/{product}/tickers


<aside>
REQUEST PARAMETERS
</aside>

| 參數名     |必選|類型| 說明                |
|:--------|:---|:----- |-------------------|
| product |true  |string | 路徑參數 商品，例:ETH_USD |

> <a name="ResonpseExample">RESPONSE EXAMPLE</a>

```json
 {
  "type": "overview",
  "code": 200,
  "ts": 1641378730830,
  "msg": "success",
  "data": [{
    "open": "19.56",
    "close": "48174.19",
    "low": "1",
    "high": "54969.49",
    "turnOver": "2397481368.57161866",
    "count": 0,
    "vol": "49659.154689",
    "pairCode": "BTC_USDT",
    "change": "48154.63",
    "changePercent": "2461.8931492842535787"
  }, {
    "open": "11.9",
    "close": "11.9",
    "low": "11.9",
    "high": "11.9",
    "turnOver": "0",
    "count": 0,
    "vol": "0",
    "pairCode": "ETH_USDT",
    "change": "0",
    "changePercent": "0"
  }]
}
```

<aside>
RESPONSE PARAMETERS
</aside>

|參數名|類型|   說明 |
|:------|:----|:--|
| close | int  |   收盤價格 |
| high | int  |   最高價格 |
| low | int  |   最低價格 |
| open | int  |  開盤價格 |
| turnOver | string  |  交易量 |
| vol | string  |  交易額 |
| pairCode | string  |  商品，例:ETH_USD  |

<h2 id="單幣對24小時行情數據">GET  單幣對24小時行情數據</h2>

獲取有關最後交易（報價）、最佳買價/賣價和 24 小時交易量的快照信息。

**限速：無**

**限速規則：無**

**HTTP請求**

GET [HOST](#HTTP-HOST)/public/v1/products/{product}/ticker


<aside>
REQUEST PARAMETERS
</aside>

| 參數名     |必選|類型| 說明                |
|:--------|:---|:----- |-------------------|
| product |true  |string | 路徑參數 商品，例:ETH_USD |

> <a name="ResonpseExample">RESPONSE EXAMPLE</a>


```json
{
  "ch": "market.ETH_USDT.detail",
  "status": "ok",
  "tick": {
    "open": "11.9",
    "close": "11.9",
    "low": "11.9",
    "high": "11.9",
    "turnOver": "0",
    "count": 0,
    "vol": "0",
    "pairCode": "ETH_USDT",
    "change": "0",
    "changePercent": "0"
  },
  "ts": 1641378912756
}
```

<aside>
RESPONSE PARAMETERS
</aside>

|參數名|類型| 說明   |
|:-----  |:-----|------|
| close |int   | 收盤價格 |
| high |int   | 最高價格   |
| low |int   | 最低價格   |
| open |int   | 開盤價格  |
| turnOver |string   | 交易量  |
| vol |string   | 交易額  |

<h2 id="單幣對單條實時成交">GET  單幣對單條實時成交</h2>


獲取產品的最新交易列表

**限速：無**

**限速規則：無**

**HTTP請求**

GET [HOST](#HTTP-HOST)/public/v1/products/{product}/trade


<aside>
REQUEST PARAMETERS
</aside>

| 參數名     |必選|類型| 說明                |
|:--------|:---|:----- |-------------------|
| product |true  |string | 路徑參數 商品，例:ETH_USD |


> <a name="ResonpseExample">RESPONSE EXAMPLE</a>


```json 
{
	"status": "ok",
	"tick": {
		"data": [{
			"direction": "sell",
			"id": 28730000,
			"price": "11.9",
			"ts": 1639585820376,
			"vol": "1"
		}],
		"id": 1641379110358,
		"ts": 1641379110358
	},
	"ts": 1641379110358
}
```

<aside>
RESPONSE PARAMETERS
</aside>

|參數名|類型| 說明         |
|:-----  |:-----|------------|
| direction |string   | buy / sell |
| price |string   | 價格         |
| vol |string   | 成交量        |

----

<h2 id="單幣對多條實時成交">GET  單幣對多條實時成交</h2>


獲取產品的最新交易列表

**限速：無**

**限速規則：無**

**HTTP請求**

GET [HOST](#HTTP-HOST)/public/v1/products/{product}/trades


<aside>
REQUEST PARAMETERS
</aside>

| 參數名     | 必選    | 類型     | 說明                         |
|:--------|:------|:-------|----------------------------|
| product | true  | string | 路徑參數 商品，例:ETH_USD          |
| size       | false | int      | 數據長度 默認500 ，最大1000[1,1000] |

> <a name="ResonpseExample">RESPONSE EXAMPLE</a>


```json 
{
	"data": [{
		"data": [{
			"direction": "buy",
			"id": 28470000,
			"price": "11",
			"ts": 1639585820373,
			"vol": "1"
		}],
		"id": 2847,
		"ts": 1639585820373,
		"type": "fills"
	}, {
		"data": null,
		"id": 2871,
		"ts": 1639585820376,
		"type": "fills"
	}, {
		"data": [{
			"direction": "sell",
			"id": 28730000,
			"price": "11.9",
			"ts": 1639585820376,
			"vol": "1"
		}],
		"id": 2873,
		"ts": 1639585820376,
		"type": "fills"
	}],
	"status": "ok",
	"ts": 1641379702364
}
```

<aside>
RESPONSE PARAMETERS
</aside>

|參數名|類型| 說明         |
|:-----  |:-----|------------|
| direction |string   | buy / sell |
| price |string   | 價格         |
| vol |string   | 成交量        |

<h1 id="v2-public-ws">WEBSOCKET公共頻道V2</h1>


- [公共頻道V2地址](#WS_HOST_PUBLIC_V2)

**序列號 `seq_id` 說明**

1. `seq_id` 是交易所行情的一個序列號，當用戶使用一個或多個 WebSocket 連接到同一個頻道時，除了實時成交數據外，都會收到相同序列號的數據推送，用戶需要自己處理重複數據，可以使用 `seq_id` 來構建消息序列，這將允許用戶檢測數據包丟失和消息的排序。

2. `seq_id` 是一個單調遞增的數字，最小值為 0。


<h2 id="v2-public-candles">K線頻道</h2>


訂閱或者請求獲取K線(最新一根K線)數據的推送

**K線圖間隔參數:**

min -> 分鐘; hour -> 小時; day -> 天; week -> 週; mon -> 月

- 1min
- 5min
- 15min
- 30min
- 60min
- 4hour
- 1day
- 1week
- 1mon


**字段說明:**

- `id` 消息唯一id
- `open` 這根K線期間第一筆成交價
- `close` 這根K線期間末一筆成交價
- `low` 這根K線期間最低成交價
- `high` 這根K線期間最高成交價
- `filled_size` 這根K線期間成交額
- `vol` 這根K線期間成交量
- `seq_id` 唯一且有序id
- `cot` 這根K線期間成交筆數
- `interval` K線間隔
- `product` 交易對


**訂閱**

> 請求示例

```json
{
    "event": "sub",
    "biz": "market",
    "type": "candles",
    "product": "BTC_USDT",
    "interval": "15min",
    "zip": false
}

```

> 響應示例

```json
{
    "biz": "market",
    "type": "candles",
    "ts": 1666851880448,
    "code": 200,
    "status": "OK",
    "event": "sub",
    "product": "BTC_USDT",
    "interval": "15min"
}

```


**取消訂閱**

> 請求示例

```json
{
    "event": "unsub",
    "biz": "market",
    "type": "candles",
    "product": "BTC_USDT",
    "interval": "15min",
    "zip": false
}

```

> 響應示例

```json
{
    "biz": "market",
    "type": "candles",
    "ts": 1666851880448,
    "code": 200,
    "status": "OK",
    "event": "unsub",
    "product": "BTC_USDT",
    "interval": "15min"
}

```

**推送數據**

> 推送數據示例

```json
{
    "id": "1689144300",
    "biz": "market",
    "type": "candles",
    "data":
    {
        "id": 1689144300,
        "open": "3.7366",
        "close": "3.7366",
        "high": "3.7366",
        "low": "3.7366",
        "filled_size": "0",
        "vol": "0",
        "cot": 0,
        "seq_id": 112588635
    },
    "product": "BTC_USDT",
    "interval": "15min"
}

```

**請求數據**

**參數說明:**

- `id` 每個K線消息的唯一id
- `from` 開始時間的ix時間戳
- `to` 結束時間的ix時間戳
- `interval` K線間隔
- `product` 交易對

> 獲取指定範圍的K線數據請求示例

```json
{
    "event": "req",
    "biz": "market",
    "type": "candles",
    "product": "BTC_USDT",
    "interval": "15min",
    "zip": false,
    "from": 1687561511,
    "to": 1688641511
}
```

> 獲取指定範圍的K線數據響應示例

```json
{
    "biz": "market",
    "type": "candles",
    "product": "BTC_USDT",
    "ts": 1690252632272,
    "code": 200,
    "status": "OK",
    "data":
    [
        {
            "id": 1688398200,
            "open": "3.3706",
            "close": "3.3706",
            "high": "3.3706",
            "low": "3.3706",
            "filled_size": "0",
            "vol": "0",
            "cot": 0
        },
        {
            "id": 1688399100,
            "open": "3.3706",
            "close": "3.3706",
            "high": "3.3706",
            "low": "3.3706",
            "filled_size": "0",
            "vol": "0",
            "cot": 0
        }
    ],
    "event": "req",
    "interval": "15min"
}


```

----


<h2 id="v2-public-fills">成交頻道</h2>


訂閱獲取產品實時成交增量推送數據

獲取最近的成交數據，有成交數據就推送，每次推送可能包含多條成交數據。

**字段說明:**

- `id` 消息唯一id
- `ts` 成交時間戳
- `direction` 成交方向
- `price` 成交價格
- `vol` 成交量


**訂閱**

> 請求示例

```json
{
    "event": "sub",
    "biz": "market",
    "type": "fills",
    "product": "BTC_USDT",
    "zip": false
}
```

> 響應示例

```json
{
    "biz": "market",
    "type": "fills",
    "product": "BTC_USDT",
    "ts": 1690165577416,
    "code": 200,
    "status": "OK",
    "event": "sub"
}
```

**取消訂閱**

> 請求示例

```json

{
    "event": "unsub",
    "biz": "market",
    "type": "fills",
    "product": "BTC_USDT",
    "zip": false
}

```

> 響應示例

```json
{
    "biz": "market",
    "type": "fills",
    "ts": 1666851880448,
    "code": 200,
    "status": "OK",
    "event": "unsub",
    "product": "BTC_USDT"
}

```
**推送數據**

> 推送數據示例

```json
{
    "id": "310529",
    "biz": "market",
    "type": "fills",
    "data":
    [
        {
            "vol": "0.79",
            "ts": 1689152279117,
            "price": "3.4134",
            "direction": "buy",
            "id": 310529000
        }
    ],
    "product": "BTC_USDT"
} 
```

-----

<h2 id="v2-public-orderbook">深度頻道</h2>


訂閱獲取產品訂單薄增量推送數據

最快500毫秒推送一次，沒有觸發事件時也推送，盤口無數據 bids 和 asks可能為空數組

**OrderBook訂閱interval參數：[當前檔位支持最大精度, 當前檔位支持最大深度]:**

- 0 : [0.000000000000000001, 150]
- 1 : [0.00001, 150]
- 2 : [0.0001, 150]
- 3 : [0.001, 150]
- 4 : [0.01, 150]
- 5 : [0.1, 150]
- 6 : [0.000000000000000001, 20]
- 7 : [0.00001, 20]
- 8 : [0.0001, 20]
- 9 : [0.001, 20]
- 10 : [0.01, 20]
- 11 : [0.1, 20]

說明：interval=5，推送的bids裡的買方價格只能精確到小數點後一位，bids的數組大小最大是150


**字段說明:**

- `id` 消息唯一id
- `biz` 業務線
- `type` 類型
- `data.seq_id` 忽略
- `data.bids` 買方
- `data.bids[][0]` 買方價格
- `data.bids[][1]` 買方數量
- `data.asks` 賣方
- `data.asks[][0]` 賣方價格
- `data.asks[][1]` 賣方數量
- `data.product` 交易對
- `data.interval` 檔位



**訂閱**

> 請求示例

```json
{
    "event": "sub",
    "biz": "market",
    "type": "orderbook",
    "product": "BTC_USDT",
    "interval": "0",
    "zip": false
}
```

> 響應示例

```json
{
    "biz": "market",
    "type": "orderbook",
    "ts": 1666851880448,
    "code": 200,
    "status": "OK",
    "event": "sub",
    "product": "BTC_USDT",
    "interval": 0
}
```

**取消訂閱**
> 請求示例

```json
{
    "event": "unsub",
    "biz": "market",
    "type": "orderbook",
    "product": "BTC_USDT",
    "interval": "0",
    "zip": false
}

```
> 響應示例

```json
{
    "biz": "market",
    "type": "orderbook",
    "ts": 1666851880448,
    "code": 200,
    "status": "OK",
    "event": "unsub",
    "product": "BTC_USDT",
    "interval": 0
}

```

**推送數據**

> 推送數據示例

```json

{
    "id": "1689143926",
    "biz": "market",
    "type": "orderbook",
    "data":
    {
        "seq_id":112588640,//有序且唯一id
        "bids":           //買方
        [
            [
                "3.7366", //價格
                "0.66"    //數量
            ],
            [
                "3.6866",
                "0.98"
            ],
            [
                "3.4666",
                "0.33"
            ],
            [
                "3.3766",
                "0.76"
            ],
            [
                "3.3666",
                "0.7"
            ],
            [
                "3.1966",
                "0.75"
            ],
            [
                "3.1766",
                "0.06"
            ],
            [
                "3.0666",
                "0.91"
            ],
            [
                "3.0266",
                "0.73"
            ]
        ],
        "asks":           //賣方
        [
            [
                "3.9966", //價格
                "0.9"     //數量
            ]
        ]
    },
    "product": "BTC_USDT",//交易對
    "interval": "0"
}


```
----


<h2 id="v2-public-depth">深度depth頻道</h2>


訂閱獲取產品深度圖增量推送數據

說明：買賣盤各拿平均價格的10%以內的最多200條，賣1價向上浮動10%內的委託，買1向下浮動10%以內的委託

最快500毫秒推送一次，沒有觸發事件時也推送，盤口無數據 bids 和 asks可能為空數組


**字段說明:**

- `id` 消息唯一id
- `biz` 業務線
- `seq_id` 忽略
- `type` 類型
- `data.bids` 買方深度
- `data.bids[][0]` 買方深度價格
- `data.bids[][1]` 買方深度數量
- `data.asks` 賣方深度
- `data.asks[][0]` 賣方深度價格
- `data.asks[][1]` 賣方深度數量
- `data.seq_id` 有序且唯一id
- `data.product` 交易對


**訂閱**

> 請求示例

```json
{
    "event": "sub",
    "biz": "market",
    "type": "percent10",
    "product": "BTC_USDT",
    "zip": false
}
```

> 響應示例

```json
{
    "biz": "market",
    "type": "percent10",
    "ts": 1666851880448,
    "code": 200,
    "status": "OK",
    "event": "sub",
    "product": "BTC_USDT"
}
```
**取消訂閱**

> 請求示例

```json
{
    "event": "unsub",
    "biz": "market",
    "type": "percent10",
    "product": "BTC_USDT",
    "zip": false
}
```

> 響應示例

```json
{
    "biz": "market",
    "type": "percent10",
    "product": "BTC_USDT",
    "ts": 1690193555943,
    "code": 200,
    "status": "OK",
    "event": "unsub"
}
```


**推送數據**

> 推送數據示例

```json

{
    "id": "1689143539",     //消息唯一id
    "biz": "market",
    "seq_id": 112588640,     //有序且唯一id
    "type": "percent10",    //業務類型
    "data":
    {
        "bids":             //買方
        [
            [
                "3.8646667",//價格
                "0"         //數量
            ]
        ],
        "asks":             //賣方
        [
            [
                "3.8685333",//價格
                "0"         //數量
            ],
            [
                "3.8704666",
                "0"
            ]
        ],
        "seq_id": 112588640
    },
    "product": "BTC_USDT"
}
 
```

----


<h2 id="v2-public-ticker">行情頻道</h2>


獲取產品24小時ticker增量推送數據

**字段說明:**

- `id` 消息唯一id
- `open` 24小時前開始第一筆成交價格
- `close` 24小時最新成交價格
- `low` 24小時內最低成交價
- `high` 24小時內最高成交價
- `filled_size` 24小時內成交額
- `vol` 24小時內成交量
- `seq_id` 唯一且有序id
- `cot` 24小時成交筆數
- `change` 24小時價格變化
- `change_percent` 24小時價格變化(百分比)



**訂閱**

> 請求示例

```json
{
    "event": "sub",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "zip": false
}	
```


> 響應示例

```json
{
    "biz": "market",
    "type": "ticker",
    "ts": 1666851880448,
    "code": 200,
    "status": "OK",
    "event": "sub",
    "product": "BTC_USDT"
}
```

**取消訂閱**

> 請求示例

```json
{
    "event": "unsub",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "zip": false
}
```


> 響應示例

```json
{
    "biz": "market",
    "type": "ticker",
    "ts": 1689946788754,
    "code": 200,
    "status": "OK",
    "event": "unsub",
    "product": "BTC_USDT"
}
```
**推送數據**

> 推送數據示例

```json

{
    "id": "1689144487",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "data":
    [
        {
            "id": 1689144487,
            "seq_id": 112588640,
            "open": "3.7366",
            "close": "3.7366",
            "high": "3.7366",
            "low": "3.7366",
            "filled_size": "0",
            "vol": "0",
            "cot": 0,
            "change": "0",
            "change_percent": "0"
        }
    ]
}
```

**請求  指定交易對最新行情數據**

> 獲取指定交易對最新行情數據請求示例


```json
{
    "event": "req",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "zip": false
}

```

> 獲取指定交易對最新行情數據響應示例


```json
{
    "biz": "market",
    "type": "ticker",
    "ts": 1689133337870,
    "code": 200,
    "status": "OK",
    "data":
    {
        "id": 1689133336,
        "seq_id": 112588640,
        "open": "3.7366",
        "close": "3.7366",
        "high": "3.7366",
        "low": "3.7366",
        "filled_size": "0",
        "vol": "0",
        "cot": 0,
        "change": "0",
        "change_percent": "0"
    },
    "event": "req",
    "product": "BTC_USDT"
}

```

<h2 id="v2-public-req-param">公共頻道Request字段說明</h2>

| 參數名      | 類型     | 必選  | 說明        | 參考值           |
|:---------|:-------|:----|-----------|---------------|
| event    | string | 是   | 請求事件      | [事件](#events) |
| biz      | string | 是   | 業務線       | [業務線](#bizs)  |
| type     | string | 是   | 業務類型      | [類型](#types)  |
| product  | string | 是   | 交易對	      | BTC_USDT      |
| interval | string | 否   | 頻率        | 1min          |
| zip      | bool   | 是   | 是否啟用gzip	 | true,false    |

<h2 id="v2-public-rep-param">公共頻道Response字段說明</h2>


| 參數名      | 類型     | 必選  | 說明      | 參考值           |
|:---------|:-------|:----|---------|---------------|
| event    | string | 是   | 請求事件    | [事件](#events) |
| biz      | string | 是   | 業務線     | [業務線](#bizs)  |
| type     | string | 是   | 業務類型    | [類型](#types)  |
| product  | string | 是   | 交易對	    | BTC_USDT      |
| interval | string | 否   | 頻率      | 1min          |
| code     | int    | 是   | 錯誤碼     |               |
| status   | string | 是   | 錯誤碼狀態   | 可忽略           |
| ts       | long   | 是   | unix時間戳 | 可忽略           |
| data     | json   | 否   | 業務數據    | 參考具體業務數據說明    |


<h2 id="v2-publilc-events">公共頻道Event列表</h2>


| Event 名稱 | 類型     | 說明              |
|:---------|:-------|-----------------|
| sub      | string | 訂閱事件,由客戶端主動發起   |
| unsub    | string | 取消訂閱事件，由客戶端主動發起 |
| req      | string | 請求數據事件，由客戶端主動發起 |


<h2 id="v2-publilc-bizs">公共頻道Biz列表</h2>

| Biz 名稱 | 類型     | 說明   |
|:-------|:-------|------|
| market | string | 現貨行情 |



<h2 id="v2-publilc-types">公共頻道Type列表</h2>


| Type 名稱   | 類型     | 說明         |
|:----------|:-------|------------|
| fills     | string | 成交數據       |
| candles   | string | K線數據       |
| orderbook | string | 訂單薄        |
| ticker    | string | 24小時ticker |
| percent10 | string | 深度depth    |


----

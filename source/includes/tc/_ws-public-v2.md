# WEBSOCKET FEED PUBLIC V2

- `wss://ws.bg.exchange/v2/ws/`

## 請求字段說明

| 參數名稱 | 類型 | 必選 | 說明 | 範例值 |
|:-------- |:---- |:---- |:---- |:------ |
| event | string | 是 | 請求事件 | [事件](#events) |
| biz | string | 是 | 業務線 | [業務線](#bizs) |
| type | string | 是 | 業務類型 | [類型](#types) |
| product | string | 是 | 交易對 | BTC_USDT |
| interval | string | 否 | 頻率 | 1min |
| zip | bool | 是 | 是否開啟壓縮 | true, false |
| params | JSON | 否 | 業務參數 | 可以為空 |

## 回應字段說明

| 參數名稱 | 類型 | 必選 | 說明 | 範例值 |
|:-------- |:---- |:---- |:---- |:------ |
| event | string | 是 | 請求事件 | [事件](#events) |
| biz | string | 是 | 業務線 | [業務線](#bizs) |
| type | string | 是 | 業務類型 | [類型](#types) |
| product | string | 是 | 交易對 | BTC_USDT |
| interval | string | 否 | 頻率 | 1min |
| zip | bool | 是 | 是否開啟壓縮 | true, false |
| id | string | 否 | 唯一消息ID |
| code | number | 是 | 錯誤碼 | |
| status | string | 是 | 錯誤碼狀態 | |
| data | JSON | 否 | 業務數據 | 參考具體業務數據說明 |

## 事件列表

<a name="events"></a>

|事件名稱|類型|說明|
|:-------|:---|:----|
| sub | string | 訂閱事件，由客戶端主動發起 |
| unsub | string | 取消訂閱事件，由客戶端主動發起 |
| req | string | 請求數據事件，由客戶端主動發起 |

## 業務線列表

<a name="bizs"></a>

| 業務線名稱 | 類型 | 說明 |
|:----    |:----- |-----   |
| market    | string | 現貨行情 |

## 業務類型列表
<a name="types"></a>

| 業務類型名稱 | 類型 | 說明 |
|:----    |:----- |-----   |
| fills    | string | 成交數據 |
| candles    | string | K線數據 |
| orderbook    | string | 訂單薄 |
| ticker    | string | 24小時ticker |
| percent10    | string | 有限檔位深度 |



## K線訂閱/取消訂閱與請求

訂閱或請求以獲取K線（最新一根K線）數據的更新。

**K線圖間隔參數：**

 min -> 分鐘; hour -> 小时; day -> 天; week -> 周; mon -> 月

- 1min
- 5min
- 15min
- 30min
- 1hour
- 4hour
- 1day
- 1week
- 1mon

**字段說明：**

- `id` 消息唯一ID
- `open` 這根K線期間第一筆成交價
- `close` 這根K線期間末一筆成交價
- `low` 這根K線期間最低成交價
- `high` 這根K線期間最高成交價
- `turnOver` 這根K線期間成交額
- `vol` 這根K線期間成交量
- `seqId` 唯一且有序ID
- `count` 這根K線期間成交筆數
- `interval` K線間隔
- `product` 交易對


#### Subscribe

> Subscribe request

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

> Subscribe response

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


#### UnSubscribe

> UnSubscribe request

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

> UnSubscribe response

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

#### Feed Stream 

> Feed Stream

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
        "turnOver": "0",
        "vol": "0",
        "count": 0,
        "seqId": 112588635
    },
    "product": "BTC_USDT",
    "interval": "15min"
}

```

#### Request Candles

> Req request 

**參數說明：**

- `id` 每個K線消息的唯一ID
- `from` 開始時間的Unix時間戳
- `to` 結束時間的Unix時間戳
- `interval` K線間隔
- `product` 交易對

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

> Req response

```json
{
    "biz": "market",
    "type": "candles",
    "ts": 1689133139813,
    "code": 200,
    "status": "OK",
    "data":
    [
        {
            "count": 505866,
            "turnOver": 471315.660750,
            "vol": 132286.14,
            "id": 1688107500,
            "high": 4.0584,
            "open": 3.354,
            "low": 3.0616,
            "close": 3.4575
        },
        {
            "count": 492245,
            "turnOver": 458095.923364,
            "vol": 128555.52,
            "id": 1688108400,
            "high": 4.0584,
            "open": 3.4575,
            "low": 3.0637,
            "close": 3.3665
        }
    ],
    "event": "req",
    "product": "BTC_USDT",
    "interval": "15min"
} 


```

----

##  Fills Subscribe/UnSubscribe

**字段說明：**

- `id` 消息唯一ID
- `ts` 成交時間戳
- `direction` 成交方向
- `price` 成交價格
- `vol` 成交量



#### Subscribe

> Subscribe request

```json
{
    "event": "sub",
    "biz": "market",
    "type": "fills",
    "product": "BTC_USDT",
    "zip": false
}
```

> Subscribe response

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

#### UnSubscribe

> UnSubscribe request

```json

{
    "event": "unsub",
    "biz": "market",
    "type": "fills",
    "product": "BTC_USDT",
    "zip": false
}

```

> UnSubscribe response  

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
#### Feed Stream 

> Feed Stream

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

## OrderBook Subscribe/UnSubscribe

#### Subscribe

> Subscribe request

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

> Subscribe response

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

#### UnSubscribe 
> UnSubscribe request

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
> UnSubscribe response

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

#### Feed Stream 

> Feed Stream

```json

{
    "id": "1689143926",
    "biz": "market",
    "type": "orderBook",
    "data":
    {
        "seqId": 112588640,
        "bids":
        [
            [
                "3.7366",
                "0.66"
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
        "asks":
        [
            [
                "3.9966",
                "0.9"
            ]
        ]
    },
    "product": "BTC_USDT",
    "interval": "0"
}


```
----

## Percent10 Subscribe/Unsubscribe

限制深度的訂單簿數據。


#### Subscribe

> Subscribe request

```json
{
    "event": "sub",
    "biz": "market",
    "type": "percent10",
    "product": "BTC_USDT",
    "zip": false
}
```

> Subscribe response

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
#### UnSubscribe

> UnSubscribe request

```json
{
    "event": "unsub",
    "biz": "market",
    "type": "percent10",
    "product": "BTC_USDT",
    "zip": false
}
```

> UnSubscribe response

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


#### Feed Stream 

> Feed Stream

```json

{
    "id": "1689143539",     //消息唯一id
    "biz": "market",
    "seqId": 112588640,     //唯一且有序id
    "type": "percent10",    //業務類型
    "data":
    {
        "bids":             //買方
        [
            [
                "3.8646667",//价格
                "0"         //数量
            ]
        ],
        "asks":             //卖方
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
        "seqId": 112588640
    },
    "product": "BTC_USDT"
}
 
```

----


##  Ticker Subscribe/UnSubscribe and Req

**字段說明:**

- `id` 消息唯一id
- `open` 24小時前開始第一筆成交價格
- `close` 24小時最新成交價格
- `low` 24小時內最低成交價
- `high` 24小時內最高成交價
- `turnOver` 24小時內成交額
- `vol` 24小時內成交量
- `seqId` 唯一且有序id
- `count` 24小時成交筆數
- `change` 24小時價格變化
- `changePercent` 24小時價格變化(百分比)



#### Subscribe

> Subscribe request

```json
{
    "event": "sub",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "zip": false
}	
```


> Subscribe response

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

#### UnSubscribe

> UnSubscribe request

```json
{
    "event": "unsub",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "zip": false
}
```


> UnSubscribe response

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
#### Feed Stream 

> Feed Stream

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
            "seqId": 112588640,
            "open": "3.7366",
            "close": "3.7366",
            "high": "3.7366",
            "low": "3.7366",
            "turnOver": "0",
            "vol": "0",
            "count": 0,
            "change": "0",
            "changePercent": "0"
        }
    ]
}
```

#### Request Ticker

> Req request


```json
{
    "event": "req",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "zip": false
}

```

> Req response


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
        "seqId": 112588640,
        "open": "3.7366",
        "close": "3.7366",
        "high": "3.7366",
        "low": "3.7366",
        "turnOver": "0",
        "vol": "0",
        "count": 0,
        "change": "0",
        "changePercent": "0"
    },
    "event": "req",
    "product": "BTC_USDT"
}

```

----






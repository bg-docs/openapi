<h1 id="v2-public-ws">WEBSOCKET公共频道V2</h1>

- [公共频道V2地址](#WS_HOST_PUBLIC_V2)

**序列号 `seq_id` 说明**

1. `seq_id` 是交易所行情的一个序列号，当用户使用一个或多个 WebSocket 连接到同一个频道时，除了实时成交数据外，都会收到相同序列号的数据推送，用户需要自己处理重复数据，可以使用 `seq_id` 来构建消息序列，这将允许用户检测数据包丢失和消息的排序。

2. `seq_id` 是一个单调递增的数字，最小值为 0。


<h2 id="v2-public-candles">K线频道</h2>


订阅或者请求获取K线(最新一根K线)数据的推送

**K线图间隔参数:**

min -> 分钟; hour -> 小时; day -> 天; week -> 周; mon -> 月

- 1min
- 5min
- 15min
- 30min
- 60min
- 4hour
- 1day
- 1week
- 1mon


**字段说明:**

- `id` 消息唯一id
- `open` 这根K线期间第一笔成交价
- `close` 这根K线期间末一笔成交价
- `low` 这根K线期间最低成交价
- `high` 这根K线期间最高成交价
- `filled_size` 这根K线期间成交额
- `vol` 这根K线期间成交量
- `seq_id` 唯一且有序id
- `cot` 这根K线期间成交笔数
- `interval` K线间隔
- `product` 交易对


**订阅**

> 请求示例

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

> 响应示例

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


**取消订阅**

> 请求示例

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

> 响应示例

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

**推送数据**

> 推送数据示例

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

**请求数据**

**参数说明:**

- `id` 每个K线消息的唯一id
- `from` 开始时间的ix时间戳
- `to` 结束时间的ix时间戳
- `interval` K线间隔
- `product` 交易对

> 获取指定范围的K线数据请求示例

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

> 获取指定范围的K线数据响应示例

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


<h2 id="v2-public-fills">成交频道</h2>


订阅获取产品实时成交增量推送数据

获取最近的成交数据，有成交数据就推送，每次推送可能包含多条成交数据。

**字段说明:**

- `id` 消息唯一id
- `ts` 成交时间戳
- `direction` 成交方向
- `price` 成交价格
- `vol` 成交量


**订阅**

> 请求示例

```json
{
    "event": "sub",
    "biz": "market",
    "type": "fills",
    "product": "BTC_USDT",
    "zip": false
}
```

> 响应示例

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

**取消订阅**

> 请求示例

```json

{
    "event": "unsub",
    "biz": "market",
    "type": "fills",
    "product": "BTC_USDT",
    "zip": false
}

```

> 响应示例

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
**推送数据**

> 推送数据示例

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

<h2 id="v2-public-orderbook">深度频道</h2>


订阅获取产品订单薄增量推送数据

最快500毫秒推送一次，没有触发事件时也推送，盘口无数据 bids 和 asks可能为空数组

**OrderBook订阅interval参数：[当前档位支持最大精度, 当前档位支持最大深度]:**

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

说明：interval=5，推送的bids里的买方价格只能精确到小数点后一位，bids的数组大小最大是150


**字段说明:**

- `id` 消息唯一id
- `biz` 业务线
- `type` 类型
- `data.seq_id` 忽略
- `data.bids` 买方
- `data.bids[][0]` 买方价格
- `data.bids[][1]` 买方数量
- `data.asks` 卖方
- `data.asks[][0]` 卖方价格
- `data.asks[][1]` 卖方数量
- `data.product` 交易对
- `data.interval` 档位



**订阅**

> 请求示例

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

> 响应示例

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

**取消订阅**
> 请求示例

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
> 响应示例

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

**推送数据**

> 推送数据示例

```json

{
    "id": "1689143926",
    "biz": "market",
    "type": "orderbook",
    "data":
    {
        "seq_id":112588640,//有序且唯一id
        "bids":           //买方
        [
            [
                "3.7366", //价格
                "0.66"    //数量
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
        "asks":           //卖方
        [
            [
                "3.9966", //价格
                "0.9"     //数量
            ]
        ]
    },
    "product": "BTC_USDT",//交易对
    "interval": "0"
}


```
----


<h2 id="v2-public-depth">深度depth频道</h2>


订阅获取产品深度图增量推送数据

说明：买卖盘各拿平均价格的10%以内的最多200条，卖1价向上浮动10%内的委托，买1向下浮动10%以内的委托

最快500毫秒推送一次，没有触发事件时也推送，盘口无数据 bids 和 asks可能为空数组


**字段说明:**

- `id` 消息唯一id
- `biz` 业务线
- `seq_id` 忽略
- `type` 类型
- `data.bids` 买方深度
- `data.bids[][0]` 买方深度价格
- `data.bids[][1]` 买方深度数量
- `data.asks` 卖方深度
- `data.asks[][0]` 卖方深度价格
- `data.asks[][1]` 卖方深度数量
- `data.seq_id` 有序且唯一id
- `data.product` 交易对


**订阅**

> 请求示例

```json
{
    "event": "sub",
    "biz": "market",
    "type": "percent10",
    "product": "BTC_USDT",
    "zip": false
}
```

> 响应示例

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
**取消订阅**

> 请求示例

```json
{
    "event": "unsub",
    "biz": "market",
    "type": "percent10",
    "product": "BTC_USDT",
    "zip": false
}
```

> 响应示例

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


**推送数据**

> 推送数据示例

```json

{
    "id": "1689143539",     //消息唯一id
    "biz": "market",
    "seq_id": 112588640,     //有序且唯一id
    "type": "percent10",    //业务类型
    "data":
    {
        "bids":             //买方
        [
            [
                "3.8646667",//价格
                "0"         //数量
            ]
        ],
        "asks":             //卖方
        [
            [
                "3.8685333",//价格
                "0"         //数量
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


<h2 id="v2-public-ticker">行情频道</h2>


获取产品24小时ticker增量推送数据

**字段说明:**

- `id` 消息唯一id
- `open` 24小时前开始第一笔成交价格
- `close` 24小时最新成交价格
- `low` 24小时内最低成交价
- `high` 24小时内最高成交价
- `filled_size` 24小时内成交额
- `vol` 24小时内成交量
- `seq_id` 唯一且有序id
- `cot` 24小时成交笔数
- `change` 24小时价格变化
- `change_percent` 24小时价格变化(百分比)



**订阅**

> 请求示例

```json
{
    "event": "sub",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "zip": false
}	
```


> 响应示例

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

**取消订阅**

> 请求示例

```json
{
    "event": "unsub",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "zip": false
}
```


> 响应示例

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
**推送数据**

> 推送数据示例

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

**请求  指定交易对最新行情数据**

> 获取指定交易对最新行情数据请求示例


```json
{
    "event": "req",
    "biz": "market",
    "type": "ticker",
    "product": "BTC_USDT",
    "zip": false
}

```

> 获取指定交易对最新行情数据响应示例


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

<h2 id="v2-public-req-param">公共频道Request字段说明</h2>

| 参数名      | 类型     | 必选  | 说明        | 参考值           |
|:---------|:-------|:----|-----------|---------------|
| event    | string | 是   | 请求事件      | [事件](#events) |
| biz      | string | 是   | 业务线       | [业务线](#bizs)  |
| type     | string | 是   | 业务类型      | [类型](#types)  |
| product  | string | 是   | 交易对	      | BTC_USDT      |
| interval | string | 否   | 频率        | 1min          |
| zip      | bool   | 是   | 是否启用gzip	 | true,false    |

<h2 id="v2-public-rep-param">公共频道Response字段说明</h2>


| 参数名      | 类型     | 必选  | 说明      | 参考值           |
|:---------|:-------|:----|---------|---------------|
| event    | string | 是   | 请求事件    | [事件](#events) |
| biz      | string | 是   | 业务线     | [业务线](#bizs)  |
| type     | string | 是   | 业务类型    | [类型](#types)  |
| product  | string | 是   | 交易对	    | BTC_USDT      |
| interval | string | 否   | 频率      | 1min          |
| code     | int    | 是   | 错误码     |               |
| status   | string | 是   | 错误码状态   | 可忽略           |
| ts       | long   | 是   | unix时间戳 | 可忽略           |
| data     | json   | 否   | 业务数据    | 参考具体业务数据说明    |


<h2 id="v2-publilc-events">公共频道Event列表</h2>


| Event 名称 | 类型     | 说明              |
|:---------|:-------|-----------------|
| sub      | string | 订阅事件,由客户端主动发起   |
| unsub    | string | 取消订阅事件，由客户端主动发起 |
| req      | string | 请求数据事件，由客户端主动发起 |


<h2 id="v2-publilc-bizs">公共频道Biz列表</h2>

| Biz 名称 | 类型     | 说明   |
|:-------|:-------|------|
| market | string | 现货行情 |



<h2 id="v2-publilc-types">公共频道Type列表</h2>


| Type 名称   | 类型     | 说明         |
|:----------|:-------|------------|
| fills     | string | 成交数据       |
| candles   | string | K线数据       |
| orderbook | string | 订单薄        |
| ticker    | string | 24小时ticker |
| percent10 | string | 深度depth    |


----


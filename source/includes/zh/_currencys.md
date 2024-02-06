# 币种信息

<h2 id="获取所有已知货币">GET  获取所有已知货币</h2>


获取所有币种的信息列表

**限速：无**

**限速规则：无**

**HTTP请求**

GET [HOST](#HTTP-HOST)/v1/currencies


> <a name="ResonpseExample">RESPONSE EXAMPLE</a>

```json
[
  {
    "currency": "ETH",
    "min_size": "0",
    "status": "on",
    "max_precision": "10",
    "type": "crypto",
    "deposit_status": "on",
    "withdraw_status": "on",
    "accuracy": "8",
    "details": [
      {
        "network_confirmations": "12",
        "sort_order": "3",
        "display_name": "ETH",
        "deposit_status": "on",
        "accuracy": "8",
        "withdraw_status": "on"
      }
    ]
  }
]
```


<aside>
RESPONSE PARAMETERS
</aside>





`currency`: 币种名称，可唯一标识币种

`accuracy`: fiat存取款精度

`max_precision` : 最大精度。取之范围在`[18,-18]`

- `max_precision >= 0` 时，代表币种精度在小数点后 max_precision 位；
- `max_precision < 0` 时，代表币种精度为整数，且精度为 10 的 abs(max_precision) 次方位

`min_size`: 最小出入金数量

`status`: 币种状态

`type`: 货币类型，`fiat` 为法币, `crypto` 为数字币

`details`: 链信息，只有数字币类型才会有此部分信息

`deposit_status`: fiat 存款状态

`withdraw_status`: fiat  取款状态

- `dispaly_name`: 显示名称
- `network_confirmations`: 最低网络确认次数
- `currency`: 币种名称，可唯一标识币种
- `accuracy`: crypto存取款精度
- `deposit_status`: crypto 存款状态
- `withdraw_status`: crypto 取款状态

| 参数名称 | 参数说明 | 类型 | 
| -------- | -------- | ----- |
|currency|币种名称|string|
|accuracy|fiat存取款精度|string|
|max_precision|最大精度|string|
|min_size|最小出入金数量|string|
|status|币种状态|string|
|type|货币类型|string|
|details|链信息|string|
|deposit_status|fiat 存款状态|string|
|withdraw_status|fiat  取款状态|string|


<h2 id="获取单个币种信息">GET  获取单个币种信息</h2>


获取指定币种的信息

**限速：无**

**限速规则：无**

**HTTP请求**

GET [HOST](#HTTP-HOST)/v1/currencies/{currency}


<aside>
REQUEST PARAMETERS
</aside>

| 参数名称 | 参数说明 | 是否必须 | 数据类型 | 
| -------- | -------- | -------- | -------- | 
|currency|币种名称，例:BTC|true|string|

> <a name="ResonpseExample">RESPONSE EXAMPLE</a>

```json
[
  {
    "currency": "ETH",
    "min_size": "0",
    "status": "on",
    "max_precision": "10",
    "type": "crypto",
    "deposit_status": "on",
    "withdraw_status": "on",
    "accuracy": "8",
    "details": [
      {
        "network_confirmations": "12",
        "display_name": "ETH",
        "accuracy": "8",
        "deposit_status": "on",
        "withdraw_status": "on"
      }
    ]
  }
]
```

<aside>
RESPONSE PARAMETERS
</aside>

`currency`: 币种名称，可唯一标识币种

`accuracy`: fiat存取款精度

`max_precision` : 最大精度。取之范围在`[18,-18]`

- `max_precision >= 0` 时，代表币种精度在小数点后 max_precision 位；
- `max_precision < 0` 时，代表币种精度为整数，且精度为 10 的 abs(max_precision) 次方位

`min_size`: 最小出入金数量

`status`: 币种状态

`type`: 货币类型，`fiat` 为法币, `crypto` 为数字币

`details`: 链信息，只有数字币类型才会有此部分信息

`deposit_status`: fiat 存款状态

`withdraw_status`: fiat  取款状态

- `dispaly_name`: 显示名称
- `network_confirmations`: 最低网络确认次数
- `currency`: 币种名称
- `accuracy`: crypto存取款精度
- `deposit_status`: crypto 存款状态
- `withdraw_status`: crypto 取款状态

| 参数名称 | 参数说明 | 类型 | 
| -------- | -------- | ----- |
|currency|币种名称|string|
|accuracy|fiat存取款精度|string|
|max_precision|最大精度|string|
|min_size|最小出入金数量|string|
|status|币种状态|string|
|type|货币类型|string|
|details|链信息|string|
|deposit_status|fiat 存款状态|string|
|withdraw_status|fiat  取款状态|string|



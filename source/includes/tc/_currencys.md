# 幣種信息

## 獲取所有已知貨幣

<font class="httpget">GET</font> */v1/currencies*



<aside>
RESPONSE STATUS
</aside>

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request | [參考示例](#ResonpseExample1)
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

`currency`: 幣種名稱，可唯一標識幣種

`accuracy`: fiat存取款精度

`max_precision` : 最大精度。取之範圍在`[18,-18]`

- `max_precision >= 0` 時，代表幣種精度在小數點後 max_precision 位；
- `max_precision < 0` 時，代表幣種精度為整數，且精度為 10 的 abs(max_precision) 次方位

`min_size`: 最小出入金數量

`status`: 幣種狀態

`type`: 貨幣類型，`fiat` 為法幣, `crypto` 為數字幣

`details`: 鏈信息，只有數字幣類型才會有此部分信息

`deposit_status`: fiat 存款狀態

`withdraw_status`: fiat  取款狀態

- `dispaly_name`: 顯示名稱
- `network_confirmations`: 最低網絡確認次數
- `currency`: 數字幣標識符
- `accuracy`: crypto存取款精度
- `deposit_status`: crypto 存款狀態
- `withdraw_status`: crypto 取款狀態

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

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

## 獲取單個幣種信息

<font class="httpget">GET</font> */v1/currencies/{currency}*


<aside>
RESPONSE STATUS
</aside>

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request | [參考示例](#ResonpseExample1)
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

`currency`: 幣種名稱，可唯一標識幣種

`accuracy`: fiat存取款精度

`max_precision` : 最大精度。取之範圍在`[18,-18]`

- `max_precision >= 0` 時，代表幣種精度在小數點後 max_precision 位；
- `max_precision < 0` 時，代表幣種精度為整數，且精度為 10 的 abs(max_precision) 次方位

`min_size`: 最小出入金數量

`status`: 幣種狀態

`type`: 貨幣類型，`fiat` 為法幣, `crypto` 為數字幣

`details`: 鏈信息，只有數字幣類型才會有此部分信息

`deposit_status`: fiat 存款狀態

`withdraw_status`: fiat  取款狀態

- `dispaly_name`: 顯示名稱
- `network_confirmations`: 最低網絡確認次數
- `currency`: 數字幣標識符
- `accuracy`: crypto存取款精度
- `deposit_status`: crypto 存款狀態
- `withdraw_status`: crypto 取款狀態

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

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

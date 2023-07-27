# 幣種信息

<h2 id="獲取所有已知貨幣"><font class="httpget">GET</font>  獲取所有已知貨幣</h2>


獲取所有幣種的信息列表

**限速：無**

**限速規則：無**

**HTTP請求**

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
- `currency`: 幣種名稱，可唯一標識幣種
- `accuracy`: crypto存取款精度
- `deposit_status`: crypto 存款狀態
- `withdraw_status`: crypto 取款狀態

| 參數名稱 | 參數說明 | 類型 | 
| -------- | -------- | ----- |
|currency|幣種名稱|string|
|accuracy|fiat存取款精度|string|
|max_precision|最大精度|string|
|min_size|最小出入金數量|string|
|status|幣種狀態|string|
|type|貨幣類型|string|
|details|鏈信息|string|
|deposit_status|fiat 存款狀態|string|
|withdraw_status|fiat  取款狀態|string|


<h2 id="獲取單個幣種信息"><font class="httpget">GET</font>  獲取單個幣種信息</h2>


獲取指定幣種的信息

**限速：無**

**限速規則：無**

**HTTP請求**

GET [HOST](#HTTP-HOST)/v1/currencies/{currency}


<aside>
REQUEST PARAMETERS
</aside>

| 參數名稱 | 參數說明 | 是否必須 | 數據類型 | 
| -------- | -------- | -------- | -------- | 
|currency|幣種名稱，例:BTC|true|string|

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
- `currency`: 幣種名稱
- `accuracy`: crypto存取款精度
- `deposit_status`: crypto 存款狀態
- `withdraw_status`: crypto 取款狀態

| 參數名稱 | 參數說明 | 類型 | 
| -------- | -------- | ----- |
|currency|幣種名稱|string|
|accuracy|fiat存取款精度|string|
|max_precision|最大精度|string|
|min_size|最小出入金數量|string|
|status|幣種狀態|string|
|type|貨幣類型|string|
|details|鏈信息|string|
|deposit_status|fiat 存款狀態|string|
|withdraw_status|fiat  取款狀態|string|

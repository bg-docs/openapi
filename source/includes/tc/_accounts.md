# 賬戶信息

<h2 id="獲取所有賬戶餘額信息">GET  獲取所有賬戶餘額信息</h2>

獲取用戶所有的交易賬戶信息

**限速：10次/s**

**限速規則：ApiKey**

**HTTP請求**

GET [HOST](#HTTP-HOST)/v1/accounts

> 鑑權信息

> 私有信息的鑑權信息，請參考 [鑑權說明](#auth)



<aside class="notice">
  <span style="color: blue;">
凍結賬戶：當用戶下單完成，自己會被劃撥到凍結賬戶。被劃撥到凍結賬戶的資金不能被用於其他交易，以及提現操作。當訂單成交或被取消，凍結賬戶的資金會被釋放。
  </span>
</aside>

> <a name="ResonpseExample">RESPONSE EXAMPLE</a>

```json
[
  {
    "available": "10.0001",
    "balance": "11.0001",
    "currency": "BTC",
    "hold": "1.0"
  }
]
```



<aside>
RESPONSE PARAMETERS
</aside>

| 參數名稱 | 參數說明 | 類型 | 
| -------- | -------- | ----- |
|available|可用額度|string|
|hold|凍結額度|string|
|balance|餘額,包含 可用額度為凍結額度之和|string|
|currency|資產名稱|string|




<h2 id="獲取單個賬戶餘額信息">GET  獲取單個賬戶餘額信息</h2>

獲取用戶指定的交易賬戶信息

**限速：10次/s**

**限速規則：ApiKey**

**HTTP請求**

GET [HOST](#HTTP-HOST)/v1/accounts/{currency}

> 鑑權信息

> 私有信息的鑑權信息，請參考 [鑑權說明](#auth)


<aside class="notice">
  <span style="color: blue;">
凍結賬戶：當用戶下單完成，自己會被劃撥到凍結賬戶。被劃撥到凍結賬戶的資金不能被用於其他交易，以及提現操作。當訂單成交或被取消，凍結賬戶的資金會被釋放。
  </span>
</aside>

<aside>
REQUEST PARAMETERS
</aside>

| 參數名稱 | 參數說明 | 是否必須 | 數據類型 | 
| -------- | -------- | -------- | -------- | 
|currency|資產名稱，例:BTC|true|string|




> <a name="ResonpseExample">RESPONSE EXAMPLE</a>

```json
{
  "available": "10.0001",
  "balance": "11.0001",
  "currency": "BTC",
  "hold": "1.0"
}
```


<aside>
RESPONSE PARAMETERS
</aside>

| 參數名稱 | 參數說明 | 類型 | 
| -------- | -------- | ----- |
|available|可用額度|string|
|hold|凍結額度|string|
|balance|餘額,包含 可用額度與凍結額度之和|string|
|currency|資產名稱|string|

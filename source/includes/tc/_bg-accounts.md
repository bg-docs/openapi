# BGE accounts

## 獲取所有BGE錢包

<code>GET /bge-accounts</code>

獲取用戶所有可用的BGE錢包/賬戶（用戶可以用這些錢包/賬戶在 www.bg.exchange 上進行買入和賣出活動）。

> 鑑權信息

> 私有信息的鑑權信息，請參考 [鑑權說明](#auth)


<aside>
RESPONSE PARAMETERS
</aside>

| 參數名稱 | 參數說明 | 類型 | schema |
| -------- | -------- | ----- |----- | 
|active|active|boolean||
|available_on_consumer|available_on_consumer|boolean||
|balance|只包含可用餘額|string||
|currency|標記BGE錢包/賬戶的標識|string||
|id|id|string||
|name|姓名|string||
|primary|primary|boolean||
|ready|買入或賣出的基礎貨幣數量 - limit/stop訂單和market sells所需|boolean||
|type|類型：wallet|string||
|wire_deposit_information|要購買的報價貨幣數量 - market buys所需|||
|&emsp;&emsp;account_number|賬號|string||
|&emsp;&emsp;bank_name|銀行名|string||
|&emsp;&emsp;routing_number|路由號碼|string||

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
[
	{
		"active": false,
		"available_on_consumer": false,
		"balance": "",
		"currency": "",
		"id": "",
		"name": "",
		"primary": false,
		"ready": false,
		"type": "",
		"wire_deposit_information": {
			"account_number": "",
			"bank_name": "",
			"routing_number": ""
		}
	}
]
```

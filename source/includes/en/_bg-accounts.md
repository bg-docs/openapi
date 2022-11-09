# BGE accounts

## 获取所有BGE钱包

<code>GET /bge-accounts</code>

获取用户所有可用的BGE钱包/账户（用户可以用这些钱包/账户在 www.bg.exchange 上进行买入和卖出活动）。

> Authentication information 

> For the authentication information of private information, please refer to [Authentication Specifications](#Authentication Specifications)

<aside>
RESPONSE STATUS
</aside>

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request | [Examples](#ResonpseExample1)
401 | Unauthorized -- Your API key is wrong, See [Authentication Specifications](#Authentication Specifications) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

| Parameter Name | Parameter Description | Type | schema |
| -------- | -------- | ----- |----- | 
|active|active|boolean||
|available_on_consumer|available_on_consumer|boolean||
|balance|只包含可用余额|string||
|currency|标记BGE钱包/账户的标识|string||
|id|id|string||
|name|姓名|string||
|primary|primary|boolean||
|ready|买入或卖出的基础货币数量 - limit/stop订单和market sells所需|boolean||
|type|类型：wallet|string||
|wire_deposit_information|要购买的报价货币数量 - market buys所需|||
|&emsp;&emsp;account_number|账号|string||
|&emsp;&emsp;bank_name|银行名|string||
|&emsp;&emsp;routing_number|路由号码|string||

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


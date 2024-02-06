# BGE accounts

## 获取所有BGE钱包

<code>GET /bge-accounts</code>

获取用户所有可用的BGE钱包/账户（用户可以用这些钱包/账户在 www.bg.exchange 上进行买入和卖出活动）。

> 鉴权信息 

> 私有信息的鉴权信息，请参考 [鉴权说明](#auth)

<aside>
RESPONSE PARAMETERS
</aside>

| 参数名称 | 参数说明 | 类型 | schema |
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


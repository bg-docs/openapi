# 账户信息

<h2 id="获取所有账户余额信息">GET  获取所有账户余额信息</h2>

获取用户所有的交易账户信息

**限速：10次/s**

**限速规则：ApiKey**

**HTTP请求**

GET [HOST](#HTTP-HOST)/v1/accounts

> 鉴权信息

> 私有信息的鉴权信息，请参考 [鉴权说明](#auth)



<aside class="notice">
  <span style="color: blue;">
冻结账户：当用户下单完成，自己会被划拨到冻结账户。被划拨到冻结账户的资金不能被用于其他交易，以及提现操作。当订单成交或被取消，冻结账户的资金会被释放。
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

| 参数名称 | 参数说明 | 类型 | 
| -------- | -------- | ----- |
|available|可用额度|string|
|hold|冻结额度|string|
|balance|余额,包含 可用额度为冻结额度之和|string|
|currency|资产名称|string|




<h2 id="获取单个账户余额信息">GET  获取单个账户余额信息</h2>

获取用户指定的交易账户信息

**限速：10次/s**

**限速规则：ApiKey**

**HTTP请求**

GET [HOST](#HTTP-HOST)/v1/accounts/{currency}

> 鉴权信息

> 私有信息的鉴权信息，请参考 [鉴权说明](#auth)


<aside class="notice">
  <span style="color: blue;">
冻结账户：当用户下单完成，自己会被划拨到冻结账户。被划拨到冻结账户的资金不能被用于其他交易，以及提现操作。当订单成交或被取消，冻结账户的资金会被释放。
  </span>
</aside>

<aside>
REQUEST PARAMETERS
</aside>

| 参数名称 | 参数说明 | 是否必须 | 数据类型 | 
| -------- | -------- | -------- | -------- | 
|currency|资产名称，例:BTC|true|string|




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

| 参数名称 | 参数说明 | 类型 | 
| -------- | -------- | ----- |
|available|可用额度|string|
|hold|冻结额度|string|
|balance|余额,包含 可用额度与冻结额度之和|string|
|currency|资产名称|string|

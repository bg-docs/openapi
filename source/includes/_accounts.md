# 账户

## 获取所有账户余额信息

**请求方式**:`GET`

**接口地址**:`/accounts`

获取用户所有的交易账户信息

**冻结账户**

当用户下单完成，自己会被划拨到冻结账户。被划拨到冻结账户的资金不能被用于其他交易，以及提现操作。当订单成交或被取消，冻结账户的资金会被释放。

> 鉴权信息

> 私有信息的鉴权信息，请参考 [鉴权说明](#auth)

<aside>
RESPONSE STATUS
</aside>

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request | [参考示例](#ResonpseExample1)
401 | Unauthorized -- Your API key is wrong, See [鉴权说明](#auth) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

| 参数名称 | 参数说明 | 类型 | schema |
| -------- | -------- | ----- |----- | 
|available|可用额度|string||
|hold|冻结额度|string||
|balance|余额,包含 可用额度为冻结额度之和|string||
|currency|资产ID|string||

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

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


## 获取单个账户余额信息

**请求方式**:`GET`

**接口地址**:`/accounts/{account_id}`

获取用户指定的交易账户信息

**冻结账户**

当用户下单完成，自己会被划拨到冻结账户。被划拨到冻结账户的资金不能被用于其他交易，以及提现操作。当订单成交或被取消，冻结账户的资金会被释放。


<aside>
REQUEST PARAMETERS
</aside>

| 参数名称 | 参数说明 | 是否必须 | 数据类型 | schema |
| -------- | -------- | -------- | -------- | ------ |
|account_id|账户ID，例:BTC||true|string||


> 鉴权信息

> 私有信息的鉴权信息，请参考 [鉴权说明](#auth)

<aside>
RESPONSE STATUS
</aside>

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request | [参考示例](#ResonpseExample1)
401 | Unauthorized -- Your API key is wrong, See [鉴权说明](#auth) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

| 参数名称 | 参数说明 | 类型 | schema |
| -------- | -------- | ----- |----- | 
|available|可用额度|string||
|hold|冻结额度|string||
|balance|余额,包含 可用额度为冻结额度之和|string||
|currency|资产ID|string||

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
{
  "available": "10.0001",
  "balance": "11.0001",
  "currency": "BTC",
  "hold": "1.0"
}
```

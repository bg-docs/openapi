# 资金划转

## 资金账户划转到交易账户


<font class="httppost">POST</font> */v1/deposits/account*


**请求数据类型**:`application/json`


将资金从资金账户划转到指定的交易账户。







> 鉴权信息

> 私有信息的鉴权信息，请参考 [鉴权说明](#auth)


<aside>
REQUEST PARAMETERS
</aside>

| 参数名称 | 参数说明 | 是否必须 | 数据类型 | 
| -------- | -------- | -------- | -------- | 
|amount|划转数量 |false|string||
|currency|划转资产名称|false|string||

> REQUEST EXAMPLE

```json
{
  "amount": 100,
  "currency": "HKD"
}
```

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

| 参数名称 | 参数说明 | 类型 | 
| -------- | -------- | ----- |
|amount|划转数量|string|
|currency|划转资产名称|string|

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
{
  "amount": 100,
  "currency": "HKD"
}
```


## 交易账户划转到资金账户

<font class="httppost">POST</font> */v1/withdrawals/account*

**请求数据类型**:`application/json`

将资金从交易账户划转到资金账户，划转后，可以进行提现操作。







> 鉴权信息

> 私有信息的鉴权信息，请参考 [鉴权说明](#auth)


<aside>
REQUEST PARAMETERS
</aside>

| 参数名称 | 参数说明 | 是否必须 | 数据类型 | 
| -------- | -------- | -------- | -------- | 
|amount|划转数量 |false|string||
|currency|划转资产名称|false|string||

> REQUEST EXAMPLE

```json
{
  "amount": 100,
  "currency": "HKD"
}
```

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

| 参数名称 | 参数说明 | 类型 | 
| -------- | -------- | ----- |
|amount|划转数量|string|
|currency|划转资产名称|string|

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
{
  "amount": 100,
  "currency": "HKD"
}
```


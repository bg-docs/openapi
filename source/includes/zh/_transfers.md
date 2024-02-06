# 资金划转

<h2 id="资金账户划转到交易账户">POST  资金账户划转到交易账户</h2>

 
将资金从资金账户划转到指定的交易账户

**限速：10次/s**

**限速规则：ApiKey**

**HTTP请求**



POST [HOST](#HTTP-HOST)/v1/deposits/account


> 鉴权信息

> 私有信息的鉴权信息，请参考 [鉴权说明](#auth)


> <a name="RequestExample">REQUEST EXAMPLE</a>

```json
{
  "amount": 100,
  "currency": "HKD"
}
```


<aside>
REQUEST PARAMETERS
</aside>

| 参数名称 | 参数说明 | 是否必须 | 数据类型 | 
| -------- | -------- | -------- | -------- | 
|amount|划转数量 |true|string||
|currency|划转资产名称|true|string||

> <a name="ResponseExample">RESPONSE EXAMPLE</a>

```json
{
  "amount": 100,
  "currency": "HKD"
}
```


<aside>
RESPONSE PARAMETERS
</aside>

| 参数名称 | 参数说明 | 类型 | 
| -------- | -------- | ----- |
|amount|划转数量|string|
|currency|划转资产名称|string|






<h2 id="交易账户划转到资金账户">POST  交易账户划转到资金账户</h2>

将资金从交易账户划转到资金账户，划转后，可以进行提现操作。


**限速：10次/s**

**限速规则：ApiKey**

**HTTP请求**

POST [HOST](#HTTP-HOST)/v1/withdrawals/account


> 鉴权信息

> 私有信息的鉴权信息，请参考 [鉴权说明](#auth)

> <a name="RequestExample">REQUEST EXAMPLE</a>

```json
{
  "amount": 100,
  "currency": "HKD"
}
```


<aside>
REQUEST PARAMETERS
</aside>

| 参数名称 | 参数说明 | 是否必须 | 数据类型 | 
| -------- | -------- | -------- | -------- | 
|amount|划转数量 |true|string||
|currency|划转资产名称|true|string||


> <a name="ResonpseExample">RESPONSE EXAMPLE</a>

```json
{
  "amount": 100,
  "currency": "HKD"
}
```

<aside>
RESPONSE PARAMETERS
</aside>

| 参数名称 | 参数说明 | 类型 | 
| -------- | -------- | ----- |
|amount|划转数量|string|
|currency|划转资产名称|string|






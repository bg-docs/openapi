# Fund Transfer

<h2 id="Transfer from fund account to transaction account">POST Transfer from fund account to transaction account</h2>

Transfer funds from the Fund Account to a specified Trading Account.

**Speed limit: 10 times/s**

**Speed limit rules: ApiKey**

**HTTP request**



POST [HOST](#HTTP-HOST)/v1/deposits/account


> Authentication information

> For the authentication information of private information, please refer to [Authentication Specifications](#Authentication Specifications)
> For authentication information of private information, please refer to [Authentication Instructions](#auth)


> <a name="ReeuestExample">REQUEST EXAMPLE</a>


```json
{
  "amount": 100,
  "currency": "HKD"
}
```

<aside>
REQUEST PARAMETERS
</aside>

| Parameter Name | Parameter Description | Mandatory  | Data Type | 
| -------- | -------- | -------- | -------- | 
|amount|Transfer amount|false|string||
|currency|Name of transfer asset|false|string||



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

| Parameter Name | Parameter Description | Type |
| -------- | -------- | ----- |
|amount|Transfer amount|string|
|currency|Name of transfer asset|string|


<h2 id="Transfer from trading account to capital account">POST Transfer from trading account to capital account</h2>

Transfer the funds from the trading account to the capital account. After the transfer, you can carry out the cash withdrawal operation.


**Speed limit: 10 times/s**

**Speed limit rules: ApiKey**

**HTTP request**

POST [HOST](#HTTP-HOST)/v1/withdrawals/account


> Authentication information

> For authentication information of private information, please refer to [Authentication Instructions](#auth)


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

| Parameter Name | Parameter Description | Mandatory  | Data Type | 
| -------- | -------- | -------- | -------- | 
|amount|Transfer amount|false|string||
|currency|Name of transfer asset|false|string||



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

| Parameter Name | Parameter Description | Type |
| -------- | -------- | ----- |
|amount|Transfer amount|string|
|currency|Name of transfer asset|string|


# Fund Transfer

## Transfer from Fund Account to Trading Account


POST [HOST](#HTTP-HOST)/v1/deposits/account


**Request Data Type**:`application/json`


Transfer funds from the Fund Account to a specified Trading Account.







> Authentication information

> For the authentication information of private information, please refer to [Authentication Specifications](#Authentication Specifications)


<aside>
REQUEST PARAMETERS
</aside>

| Parameter Name | Parameter Description | Mandatory  | Data Type | 
| -------- | -------- | -------- | -------- | 
|amount|Transfer amount|false|string||
|currency|Name of transfer asset|false|string||

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
200 | Success Request | [Examples](#ResonpseExample1)
401 | Unauthorized -- Your API key is wrong, See [Authentication Specifications](#Authentication Specifications) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

| Parameter Name | Parameter Description | Type | 
| -------- | -------- | ----- |
|amount|Transfer amount|string|
|currency|Name of transfer asset|string|

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
{
  "amount": 100,
  "currency": "HKD"
}
```


## Transfer from Trading Account to Fund Account

POST [HOST](#HTTP-HOST)/v1/withdrawals/account

**Request Data Type:**:`application/json`

Transfer funds from the Trading Account to the Fund Account. Withdrawal operations allowed after the transfer.







> Authentication information

> For the authentication information of private information, please refer to [Authentication Specifications](#Authentication Specifications)


<aside>
REQUEST PARAMETERS
</aside>

| Parameter Name | Parameter Description | Mandatory  | Data Type | 
| -------- | -------- | -------- | -------- | 
|amount|Transfer amount|false|string||
|currency|Name of transfer asset|false|string||

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
200 | Success Request | [Examples](#ResonpseExample1)
401 | Unauthorized -- Your API key is wrong, See [Authentication Specifications](#Authentication Specifications) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

| Parameter Name | Parameter Description | Type | 
| -------- | -------- | ----- |
|amount|Transfer amount|string|
|currency|Name of transfer asset|string|

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
{
  "amount": 100,
  "currency": "HKD"
}
```



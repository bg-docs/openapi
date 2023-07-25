# Fund Transfer

## Transfer from Fund Account to Trading Account


<font class="httppost">POST</font> */v1/deposits/account*


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

<font class="httppost">POST</font> */v1/withdrawals/account*

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


# Account Information

<h2 id="Get all account balance information"><font class="httpget">GET</font> Get all account balance information</h2>

Get all the trading account information of the user

**Speed limit: 10 times/s**

**Speed limit rules: ApiKey**

**HTTP request**

GET [HOST](#HTTP-HOST)/v1/accounts

> Authentication information

> For authentication information of private information, please refer to [Authentication Instructions](#auth)




<span style="color: blue;">
Frozen account: When the user places an order, he or she will be transferred to the frozen account. The funds transferred to the frozen account cannot be used for other transactions and withdrawal operations. When the order is executed or canceled, the funds in the frozen account will be released.
</span>


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

| Parameter name | Parameter description | Type |
| -------- | -------- | ----- |
|available|Available Quota|string|
|hold|Freeze Quota|string|
|balance| balance, including the available amount is the sum of the frozen amount |string|
|currency|Asset name|string|




<h2 id="Get single account balance information"><font class="httpget">GET</font> Get single account balance information</h2>

Get the trading account information specified by the user

**Speed limit: 10 times/s**

**Speed limit rules: ApiKey**

**HTTP request**

GET [HOST](#HTTP-HOST)/v1/accounts/{currency}

> Authentication information

> For authentication information of private information, please refer to [Authentication Instructions](#auth)


<span style="color: blue;">
Frozen account: When the user places an order, he or she will be transferred to the frozen account. The funds transferred to the frozen account cannot be used for other transactions and withdrawal operations. When the order is executed or canceled, the funds in the frozen account will be released.
</span>

<aside>
REQUEST PARAMETERS
</aside>

| Parameter name | Parameter description | Required | Data type |
| -------- | -------- | -------- | -------- |
|currency|Asset name, for example: BTC|true|string|




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

| Parameter name | Parameter description | Type |
| -------- | -------- | ----- |
|available|Available Quota|string|
|hold|Freeze Quota|string|
|balance| balance, including the sum of available quota and frozen quota |string|
|currency|Asset name|string|

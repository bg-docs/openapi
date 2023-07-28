# Transfer Of Funds

<h2 id="Transfer from fund account to transaction account">POST transfer from fund account to transaction account</h2>

Transfer funds from the fund account to the designated trading account

**Speed limit: 10 times/s**

**Speed limit rules: ApiKey**

**HTTP request**

POST [HOST](#HTTP-HOST)/v1/deposits/accounttrue


> Authentication information

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

| Parameter name | Parameter description | Required | Data type |
| -------- | -------- | -------- | -------- |
|amount|transfer amount |true|string||
|currency|Transfer asset name|true|string||


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

| Parameter name | Parameter description | Type |
| -------- | -------- | ----- |
|amount|transfer amount|string|
|currency|Transfer asset name|string|




<h2 id="Transfer from transaction account to fund account">POST transfer from transaction account to fund account</h2>

Transfer the funds from the trading account to the capital account. After the transfer, you can carry out the cash withdrawal operation.


**Speed limit: 10 times/s**

**Speed limit rules: ApiKey**

**HTTP request**

POST [HOST](#HTTP-HOST)/v1/withdrawals/accounttrue


> Authentication information

> For authentication information of private information, please refer to [Authentication Instructions](#auth)


> REQUEST EXAMPLE

```json
{
  "amount": 100,
  "currency": "HKD"
}
```

<aside>
REQUEST PARAMETERS
</aside>

| Parameter name | Parameter description | Required | Data type |
| -------- | -------- | -------- | -------- |
|amount|transfer amount |true|string||
|currency|Transfer asset name|true|string||


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

| Parameter name | Parameter description | Type |
| -------- | -------- | ----- |
|amount|transfer amount|string|
|currency|Transfer asset name|string|

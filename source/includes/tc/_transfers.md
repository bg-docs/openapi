# 資金劃轉

## 資金賬戶劃轉到交易賬戶


<font class="httppost">POST</font> */v1/deposits/account*


**請求數據類型**:`application/json`


將資金從資金賬戶劃轉到指定的交易賬戶。







> 鑑權信息

> 私有信息的鑑權信息，請參考 [鑑權說明](#auth)


<aside>
REQUEST PARAMETERS
</aside>

| 參數名稱 | 參數說明 | 是否必須 | 數據類型 | 
| -------- | -------- | -------- | -------- | 
|amount|劃轉數量 |false|string||
|currency|劃轉資產名稱|false|string||

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
200 | Success Request | [參考示例](#ResonpseExample1)
401 | Unauthorized -- Your API key is wrong, See [鑑權說明](#auth) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

| 參數名稱 | 參數說明 | 類型 | 
| -------- | -------- | ----- |
|amount|劃轉數量|string|
|currency|劃轉資產名稱|string|

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
{
  "amount": 100,
  "currency": "HKD"
}
```


## 交易賬戶劃轉到資金賬戶

<font class="httppost">POST</font> */v1/withdrawals/account*

**請求數據類型**:`application/json`

將資金從交易賬戶劃轉到資金賬戶，劃轉後，可以進行提現操作。







> 鑑權信息

> 私有信息的鑑權信息，請參考 [鑑權說明](#auth)


<aside>
REQUEST PARAMETERS
</aside>

| 參數名稱 | 參數說明 | 是否必須 | 數據類型 | 
| -------- | -------- | -------- | -------- | 
|amount|劃轉數量 |false|string||
|currency|劃轉資產名稱|false|string||

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
200 | Success Request | [參考示例](#ResonpseExample1)
401 | Unauthorized -- Your API key is wrong, See [鑑權說明](#auth) | <code>message</code> string
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

| 參數名稱 | 參數說明 | 類型 | 
| -------- | -------- | ----- |
|amount|劃轉數量|string|
|currency|劃轉資產名稱|string|

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
{
  "amount": 100,
  "currency": "HKD"
}
```

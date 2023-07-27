# 資金劃轉

<h2 id="資金賬戶劃轉到交易賬戶"><font class="httpget">POST</font>  資金賬戶劃轉到交易賬戶</h2>

將資金從資金賬戶劃轉到指定的交易賬戶

**限速：10次/s**

**限速規則：ApiKey**

**HTTP請求**

POST [HOST](#HTTP-HOST)/v1/deposits/accounttrue


> 鑑權信息

> 私有信息的鑑權信息，請參考 [鑑權說明](#auth)


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

| 參數名稱 | 參數說明 | 是否必須 | 數據類型 | 
| -------- | -------- | -------- | -------- | 
|amount|劃轉數量 |true|string||
|currency|劃轉資產名稱|true|string||


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

| 參數名稱 | 參數說明 | 類型 | 
| -------- | -------- | ----- |
|amount|劃轉數量|string|
|currency|劃轉資產名稱|string|




<h2 id="交易賬戶劃轉到資金賬戶"><font class="httpget">POST</font>  交易賬戶劃轉到資金賬戶</h2>

將資金從交易賬戶劃轉到資金賬戶，劃轉後，可以進行提現操作。


**限速：10次/s**

**限速規則：ApiKey**

**HTTP請求**

POST [HOST](#HTTP-HOST)/v1/withdrawals/accounttrue


> 鑑權信息

> 私有信息的鑑權信息，請參考 [鑑權說明](#auth)


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

| 參數名稱 | 參數說明 | 是否必須 | 數據類型 | 
| -------- | -------- | -------- | -------- | 
|amount|劃轉數量 |true|string||
|currency|劃轉資產名稱|true|string||


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

| 參數名稱 | 參數說明 | 類型 | 
| -------- | -------- | ----- |
|amount|劃轉數量|string|
|currency|劃轉資產名稱|string|

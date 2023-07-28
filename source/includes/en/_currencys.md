# Currency Information

<h2 id="Get all known currencies">GET Get all known currencies</h2>


Get information list of all currencies

**Speed Limit: None**

**Speed limit rules: None**

**HTTP request**

GET [HOST](#HTTP-HOST)/v1/currencies


> <a name="ResonpseExample">RESPONSE EXAMPLE</a>

```json
[
  {
    "currency": "ETH",
    "min_size": "0",
    "status": "on",
    "max_precision": "10",
    "type": "crypto",
    "deposit_status": "on",
    "withdraw_status": "on",
    "accuracy": "8",
    "details": [
      {
        "network_confirmations": "12",
        "sort_order": "3",
        "display_name": "ETH",
        "deposit_status": "on",
        "accuracy": "8",
        "withdraw_status": "on"
      }
    ]
  }
]
```


<aside>
RESPONSE PARAMETERS
</aside>





`currency`: currency name, which can uniquely identify the currency

`accuracy`: fiat deposit and withdrawal accuracy

`max_precision` : Maximum precision. Take the range in `[18,-18]`

- When `max_precision >= 0`, it means that the currency precision is max_precision digits after the decimal point;
- When `max_precision < 0`, it means that the precision of the currency is an integer, and the precision is the abs(max_precision) subdivision of 10

`min_size`: minimum deposit and withdrawal amount

`status`: currency status

`type`: Currency type, `fiat` is fiat currency, `crypto` is digital currency

`details`: chain information, only digital currency type will have this part of information

`deposit_status`: fiat deposit status

`withdraw_status`: fiat withdrawal status

- `dispaly_name`: display name
- `network_confirmations`: minimum number of network confirmations
- `currency`: currency name, which can uniquely identify the currency
- `accuracy`: crypto deposit and withdrawal accuracy
- `deposit_status`: crypto deposit status
- `withdraw_status`: crypto withdrawal status

| Parameter name | Parameter description | Type |
| -------- | -------- | ----- |
|currency|currency name|string|
|accuracy|fiat deposit and withdrawal accuracy|string|
|max_precision|maximum precision |string|
|min_size|Minimum deposit and withdrawal amount|string|
|status|currency status|string|
|type|currency type|string|
|details|chain information |string|
|deposit_status|fiat deposit status|string|
|withdraw_status|fiat withdrawal status|string|


<h2 id="Get single currency information">GET get single currency information</h2>


Get the information of the specified currency

**Speed Limit: None**

**Speed limit rules: None**

**HTTP request**

GET [HOST](#HTTP-HOST)/v1/currencies/{currency}


<aside>
REQUEST PARAMETERS
</aside>

| Parameter name | Parameter description | Required | Data type |
| -------- | -------- | -------- | -------- |
|currency|currency name, for example: BTC|true|string|

> <a name="ResonpseExample">RESPONSE EXAMPLE</a>

```json
[
  {
    "currency": "ETH",
    "min_size": "0",
    "status": "on",
    "max_precision": "10",
    "type": "crypto",
    "deposit_status": "on",
    "withdraw_status": "on",
    "accuracy": "8",
    "details": [
      {
        "network_confirmations": "12",
        "display_name": "ETH",
        "accuracy": "8",
        "deposit_status": "on",
        "withdraw_status": "on"
      }
    ]
  }
]
```

<aside>
RESPONSE PARAMETERS
</aside>

`currency`: currency name, which can uniquely identify the currency

`accuracy`: fiat deposit and withdrawal accuracy

`max_precision` : Maximum precision. Take the range in `[18,-18]`

- When `max_precision >= 0`, it means that the currency precision is max_precision digits after the decimal point;
- When `max_precision < 0`, it means that the precision of the currency is an integer, and the precision is the abs(max_precision) subdivision of 10

`min_size`: minimum deposit and withdrawal amount

`status`: currency status

`type`: Currency type, `fiat` is fiat currency, `crypto` is digital currency

`details`: chain information, only digital currency type will have this part of information

`deposit_status`: fiat deposit status

`withdraw_status`: fiat withdrawal status

- `dispaly_name`: display name
- `network_confirmations`: minimum number of network confirmations
- `currency`: currency name
- `accuracy`: crypto deposit and withdrawal accuracy
- `deposit_status`: crypto deposit status
- `withdraw_status`: crypto withdrawal status

| Parameter name | Parameter description | Type |
| -------- | -------- | ----- |
|currency|currency name|string|
|accuracy|fiat deposit and withdrawal accuracy|string|
|max_precision|maximum precision |string|
|min_size|Minimum deposit and withdrawal amount|string|
|status|currency status|string|
|type|currency type|string|
|details|chain information |string|
|deposit_status|fiat deposit status|string|
|withdraw_status|fiat withdrawal status|string|

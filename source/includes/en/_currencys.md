# Information of Currency Types

## Obtaining All Known Currencies

<font class="httpget">GET</font> */v1/currencies*



<aside>
RESPONSE STATUS
</aside>

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request | [Examples](#ResonpseExample1)
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

`currency`: A uniquely identifiable name of the currency

`accuracy`: Accuracy of the fiat deposits and withdrawals

`max_precision` : Maximum precision. Range taken within`[18,-18]`

- `max_precision >= 0` means that the currency type precision is max_precision decimal places;
- `max_precision < 0` means that the currency type precision is an integer, and the precision is 10 to the abs(max_precision) power

`min_size`:  Minimum deposit and withdrawal amount

`status`:  Currency status

`type`: Currency type, `fiat` is legal tender, `crypto` is digital currency

`details`: Blockchain information, only a digital currency type will contain this information

`deposit_status`: Fiat deposit status

`withdraw_status`: Fiat withdrawal status

- `dispaly_name`: Display name
- `network_confirmations`: Minimum number of network confirmations
- `currency`: Digital currency identifier
- `accuracy`: Accuracy of crypto deposits and withdrawals
- `deposit_status`: Crypto deposit status
- `withdraw_status`:  Crypto withdrawal status

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

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

## Obtaining Information of a Particular Currency

<font class="httpget">GET</font> */v1/currencies/{currency}*


<aside>
RESPONSE STATUS
</aside>

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request | [Examples](#ResonpseExample1)
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

`currency`: A uniquely identifiable name of the currency

`accuracy`: Accuracy of the fiat deposits and withdrawals

`max_precision` : Maximum precision. Range taken within`[18,-18]`

- `max_precision >= 0` means that the currency type precision is max_precision decimal places;
- `max_precision < 0` means that the currency type precision is an integer, and the precision is 10 to the abs(max_precision) power

`min_size`: Minimum deposit and withdrawal amount

`status`:  Currency status

`type`: Currency type, `fiat` is legal tender, `crypto` is digital currency

`details`: Blockchain information, only a digital currency type will contain this information

`deposit_status`: Deposit status

`withdraw_status`: Withdrawal status

- `dispaly_name`: Display name
- `network_confirmations`: Minimum number of network confirmations
- `currency`: Digital currency identifier
- `accuracy`: Accuracy of crypto deposits and withdrawals
- `deposit_status`:  Crypto deposit status
- `withdraw_status`: Crypto withdrawal status

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

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

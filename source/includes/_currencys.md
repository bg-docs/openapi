# Currencies

## 获取所有已知货币

<font class="httpget">GET</font> */currencies*



<aside>
RESPONSE STATUS
</aside>

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request | [参考示例](#ResonpseExample1)
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

`id`: 币种名称，可唯一标识币种

`max_precision` : 最大精度。取之范围在`[18,-18]`

- `max_precision >= 0` 时，代表币种精度在小数点后 max_precision 位；
- `max_precision < 0` 时，代表币种精度为整数，且精度为 10 的 abs(max_precision) 次方位

`min_size`: 最小出入金数量

`status`: 币种状态

`type`: 货币类型，`fiat` 为法币, `crypto` 为数字币

`details`: 链信息，只有数字币类型才会有此部分信息

- `dispaly_name`: 显示名称
- `network_confirmations`: 最低网络确认次数
- `currency`: 数字币标识符

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
[
  {
    "id": "USDT",
    "min_size": "0",
    "status": "online",
    "max_precision": "10",
    "type": "crypto",
    "details": [
      {
        "currency": "USDT",
        "network_confirmations": "12",
        "sort_order": "5",
        "crypto_address_link": "0xf71fc630730cf866a95aebc2744452c76903f7a",
        "display_name": "USDT"
      }
    ]
  }
]
```

## 获取单个币种信息

<font class="httpget">GET</font> */currencies/{currency_id}*


<aside>
RESPONSE STATUS
</aside>

Status Code | Meaning | Example
---------- | ------- | --------
200 | Success Request | [参考示例](#ResonpseExample1)
500 | Internal Server Error -- We had a problem with our server. Try again later. | <code>message</code> string

<aside>
RESPONSE PARAMETERS
</aside>

`id`: 币种名称，可唯一标识币种

`max_precision` : 最大精度。取之范围在`[18,-18]`

- `max_precision >= 0` 时，代表币种精度在小数点后 max_precision 位；
- `max_precision < 0` 时，代表币种精度为整数，且精度为 10 的 abs(max_precision) 次方位

`min_size`: 最小出入金数量

`status`: 币种状态

`type`: 货币类型，`fiat` 为法币, `crypto` 为数字币

`details`: 链信息，只有数字币类型才会有此部分信息

- `dispaly_name`: 显示名称
- `network_confirmations`: 最低网络确认次数
- `currency`: 数字币标识符

> <a name="ResonpseExample">RESONPSE EXAMPLE</a>

```json
{
  "id": "USDT",
  "min_size": "0",
  "status": "online",
  "max_precision": "10",
  "type": "crypto",
  "details": [
    {
      "currency": "USDT",
      "network_confirmations": "12",
      "sort_order": "5",
      "crypto_address_link": "0xf71fc630730cf866a95aebc2744452c76903f7a",
      "display_name": "USDT"
    }
  ]
}
```

# Data dictionary

## WEBSOCKET Error Code Comparison Table
| Error Code | Description |
|---|---|
| 400 | Invalid Request |


## User authentication error code checklist

|Error code|Description|
|---|---|
|40001| ACCESS_KEY cannot be empty|
|40002| ACCESS_SIGN cannot be empty|
|40003| ACCESS_TIMESTAMP cannot be empty|
|40005| Invalid  ACCESS_TIMESTAMP|
|40006| Invalid  ACCESS_KEY|
|40007| Invalid  Content_Type，please use "application/json" format|
|40008| Request timestamp expired|
|40010| api verification failed|
|40011| ACCESS_KEY or PASSPHRASE error|
|40012| Invalid  API user|
|40013| User banned|
|40014| User frozen|
|40015| Invalid  IP request|

## Business error code checklist
`amount limit value` are the upper/lower limits of the transaction amount/quantity configured for the products. To uphold market stability, BGE imposes transaction limits based on real-time market conditions. The specific amounts will fluctuate in real time with the market trading circumstances.

|Error code|Description|
|---|---|
|999|Query data is empty|
|1000|Not logged in|
|1001|Parameter error|
|1006|Currency information does not exist|
|1008|Candlestick chart does not exist|
|1009|Quotation does not exist|
|1050|Currency pair does not exist|
|1051|Tier depth does not exist|
|1053|Order has been disrupted|
|1054|Below the minimum order quantity|
|1055|Value less than balance|
|1056|Exceeds the maximum order quantity|
|1057|Invalid value for market order|
|1058|Order placement failed|
|1059|Order does not exist|
|1060|Order cancellation failed|
|1061|Order cancelled|
|1062|Order filled|
|1063|Order cancellation failed|
|1099|Currency does not exist|
|1029|Transfer amount greater than available amount|
|1049|Interface requests of user are too frequent|
|1100|Insufficient available balance|
|1064|KYC authentication failed|
|1065|Unable to place order as your account is on hold|
|1066|Transaction password no longer valid|
|1067|Price, Price ≥ ${amount limit value}|
|1068|Price, Price ≤ ${amount limit value}|
|1069|Incorrect trading volume precision|
|1070|Incorrect quantity precision|
|1071|Incorrect price precision|
|1072|Order quantity cannot be 0|
|1073|Order price cannot be 0|
|1074|Insufficient account balance|
|1075|Amount, Amount ≥ ${amount limit value}|
|1076|Amount, Amount ≤ ${amount limit value}|
|1077|Value, Total ≥ ${amount limit value}|
|1078|Amount, Amount ≥ ${amount limit value}|
|1079|Value, Total ≤ ${amount limit value}|
|1080|Amount, Amount ≤ ${amount limit value}|
|1081|Order cancelled automatically as market order’s buying price has reached the maximum transaction limit price|
|1082|Order cancelled automatically as selling price of market order has reached the minimum transaction limit price|
|1083|User data access failure|
|1084|No open order|
|1085|Exceeded the maximum number of consignable orders|
|1087| Data does not exist|
|1096| Account does not exist|


# WEBSOCKET

歡迎使用BGE數字幣交易所 WebSocket 訂閱消息協議。該協議允許您通過 WebSocket 連接實時訂閱並接收市場數據、交易信息和其他相關信息。

希望該文檔能夠幫助您快速了解我們的數字幣交易所 WebSocket 訂閱消息協議。如果您有任何疑問或需要進一步的幫助，請隨時聯繫我們的技術支持團隊。祝您使用愉快！


## WEBSOCKET 基本說明

WebSocket 是一種在單個 TCP 連接上進行全雙工通信的網絡協議，它提供了一種在客戶端和服務器之間進行實時數據傳輸的方式。通過使用 WebSocket，您可以實時地訂閱和接收來自數字幣交易所的實時市場數據和其他信息。

## 連接說明

在訂閱消息之前，您需要建立 WebSocket 連接。連接說明如下：

### 當訂閱公有頻道時，使用公有服務的地址；當訂閱私有頻道時，使用私有服務的地址

- 公有頻道：公有頻道是向所有連接到交易所的客戶端廣播的頻道，包含市場行情、交易深度等信息。
  接入方法請參考: [WEBSOCKET PUBLIC V2](#websocket-feed-public-v2)
- 私有頻道：私有頻道是指僅向特定客戶端推送個人相關信息的頻道，例如訂單通知、賬戶餘額等。
  接入方法請參考: [WEBSOCKET PRIVATE V2](#websocket-feed-private-v2)

請根據您的需求選擇相應的服務地址連接到公有或私有頻道。

## 訂閱限制：每個連接1s 最多可以發送 50 條消息，否則強制關閉連接

為了保持連接的穩定性和公平性，我們對發送消息做了限制，每個連接每秒最多可以發送 50 條消息。如果您在 1 秒內發送超過 50 條消息，系統將強制關閉連接，請注意遵守此限制。

## 連接保持：我們會定時發送 ping消息，期待您返回 pong消息作為回應，如果超過 30s 沒有收到您的響應服務器會關閉連接

同時，需要注意以下情況：

網絡問題：如果出現網絡問題，系統會自動斷開連接。

連接超時：如果連接成功後 30 秒內未訂閱或訂閱後 30 秒內服務器未向用戶推送數據，系統會自動斷開連接。

為了確保連接的活躍性，我們會定時向客戶端發送 JSON 格式的 ping 消息：`{"ping": timestamp}`。您需要在收到 ping 消息後，及時發送 `{"pong": timestamp}` 文本消息，以表明連接處於活躍狀態。如果在 30 秒內沒有收到您的響應，我們將關閉連接，建議您進行以下操作：

1. 每次接收到`{"ping": timestamp}`消息後，立即回復一個`{"pong": timestamp}`。

2. 期待一個文字字符串 `{"ping": timestamp}`  作為心跳消息。如果在 N 秒內未收到，請發出錯誤或重新連接。


<aside>
PING PONG EXAMPLE
</aside>
<a name="ping_pong_demo"></a>

> Ping request

```json

{
    "ping": 1635065532000
}

```
> Pong request

```json

{
    "pong": 1635065532000
}

```

## 通用請求錯誤：錯誤消息主要由兩部分組成：錯誤代碼和消息。代碼是通用的，但是消息可能會有所不同。

當您發送的請求服務器處理失敗時，服務器將返回錯誤消息。

其他錯誤代碼和消息請參考：[錯誤碼](#WSERR)

<aside>
ERROR RESPONSE EXAMPLE
</aside>

<a name="error_ws_request_response_demo"></a>

> Error request message

```json
{
    "event": "sub",
    "para":
    {
        "biz": "market",
        "type": "percent10",
        "product": "ETH_USDT"
    },
    "zip": true
} 

```

> Response message

```json
{
    "event": "error",
    "code": "400",
    "msg": "Invalid request: {\"event\":\"sub\",\"para\":{\"biz\":\"market\",\"type\":\"percent10\",\"pairCode\":\"ETH_USDT\"},\"zip\":true}"
}

```

# WEBSOCKET

欢迎使用BGE数字币交易所 WebSocket 订阅消息协议。该协议允许您通过 WebSocket 连接实时订阅并接收市场数据、交易信息和其他相关信息。

希望该文档能够帮助您快速了解我们的数字币交易所 WebSocket 订阅消息协议。如果您有任何疑问或需要进一步的帮助，请随时联系我们的技术支持团队。祝您使用愉快！


## WEBSOCKET 基本说明

WebSocket 是一种在单个 TCP 连接上进行全双工通信的网络协议，它提供了一种在客户端和服务器之间进行实时数据传输的方式。通过使用 WebSocket，您可以实时地订阅和接收来自数字币交易所的实时市场数据和其他信息。

## 连接说明

在订阅消息之前，您需要建立 WebSocket 连接。连接说明如下：

### 当订阅公有频道时，使用公有服务的地址；当订阅私有频道时，使用私有服务的地址

- 公有频道：公有频道是向所有连接到交易所的客户端广播的频道，包含市场行情、交易深度等信息。
  接入方法请参考: [WEBSOCKET PUBLIC V2](#websocket-feed-public-v2)
- 私有频道：私有频道是指仅向特定客户端推送个人相关信息的频道，例如订单通知、账户余额等。
  接入方法请参考: [WEBSOCKET PRIVATE V2](#websocket-feed-private-v2)

请根据您的需求选择相应的服务地址连接到公有或私有频道。

## 订阅限制：每个连接1s 最多可以发送 50 条消息，否则强制关闭连接

为了保持连接的稳定性和公平性，我们对发送消息做了限制，每个连接每秒最多可以发送 50 条消息。如果您在 1 秒内发送超过 50 条消息，系统将强制关闭连接，请注意遵守此限制。

## 连接保持：我们会定时发送 ping消息，期待您返回 pong消息作为回应，如果超过 30s 没有收到您的响应服务器会关闭连接

同时，需要注意以下情况：

网络问题：如果出现网络问题，系统会自动断开连接。

连接超时：如果连接成功后 30 秒内未订阅或订阅后 30 秒内服务器未向用户推送数据，系统会自动断开连接。

为了确保连接的活跃性，我们会定时向客户端发送 JSON 格式的 ping 消息：`{"ping": timestamp}`。您需要在收到 ping 消息后，及时发送 `{"pong": timestamp}` 文本消息，以表明连接处于活跃状态。如果在 30 秒内没有收到您的响应，我们将关闭连接，建议您进行以下操作：

1. 每次接收到`{"ping": timestamp}`消息后，立即回复一个`{"pong": timestamp}`。

2. 期待一个文字字符串 `{"ping": timestamp}`  作为心跳消息。如果在 N 秒内未收到，请发出错误或重新连接。


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

## 通用请求错误：错误消息主要由两部分组成：错误代码和消息。代码是通用的，但是消息可能会有所不同。

当您发送的请求服务器处理失败时，服务器将返回错误消息。

其他错误代码和消息请参考：[错误码](#WSERR)

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




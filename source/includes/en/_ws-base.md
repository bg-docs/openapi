# WEBSOCKET

Welcome to the BGE Cryptocurrency Exchange WebSocket Subscription Message Protocol. This protocol allows you to subscribe and receive real-time market data, trade information, and other relevant updates through a WebSocket connection.

## WEBSOCKET Basics

WebSocket is a network protocol that enables full-duplex communication over a single TCP connection, providing a way for real-time data transfer between clients and servers. By using WebSocket, you can subscribe and receive real-time market data and other information from the cryptocurrency exchange.

## Connection Instructions

Before subscribing to messages, you need to establish a WebSocket connection. Here are the connection instructions:

### Use Public Service Address when subscribing to public channels; Use Private Service Address when subscribing to private channels.

- Public Channels: Public channels broadcast information to all clients connected to the exchange, including market quotes, order depth, and more.
  Access method: [WEBSOCKET FEED PUBLIC V2](#websocket-feed-public-v2)
- Private Channels: Private channels only push personal-related information to specific clients, such as order notifications, account balances, etc.
  Access method: [WEBSOCKET FEED PRIVATE](#websocket-feed-private)

Please choose the appropriate service address based on your needs for connecting to public or private channels.

### Message Limit: Maximum 50 messages per connection per second; otherwise, the connection will be forcibly closed.

To maintain connection stability and fairness, we have imposed a restriction on the number of messages sent per second for each connection. You can send a maximum of 50 messages per second. If you exceed this limit, the system will forcibly close the connection. Please ensure compliance with this limitation.

### Connection Keep-Alive: We will send periodic ping messages and expect you to respond with pong messages within 30 seconds. Otherwise, the server will close the connection.

To ensure connection activity, we will periodically send `json` format ping messages `{"ping": timestamp}` to the client. Upon receiving a ping message, you should promptly respond with the text message `{"pong": timestamp}` to indicate an active connection. If we do not receive your response within 30 seconds, we will close the connection.

### Subscription Errors: Error messages consist of two main parts: error codes and messages. While the codes are standardized, the messages may vary.

When the server cannot process the request you send, it will return an error message.

Hope this document helps you quickly understand our BGE Cryptocurrency Exchange WebSocket Subscription Message Protocol. If you have any questions or need further assistance, please feel free to contact our technical support team. Happy trading!

<aside>
PING PONG EXAMPLE
</aside>
<a name="ping_pong_demo"></a>

> ping request

```json
{
    "ping": 1635065532000
}

```
> pong request

```json

{
    "pong": 1635065532000
}

```

<aside>
ERROR RESPONSE EXAMPLE
</aside>

<a name="error_response_demo"></a>

> error response message

```json
{
    "event": "error",
    "code": "400",
    "msg": "Invalid request: {\"event\":\"sub\",\"para\":{\"biz\":\"market\",\"type\":\"percent10\",\"pairCode\":\"BTC_USDT\"},\"zip\":true}"
}

```
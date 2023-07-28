<h1 id="v2-base-ws">WEBSOCKET</h1>

Welcome to the BGE digital currency exchange WebSocket subscription message protocol. The protocol allows you to subscribe to and receive market data, trading information and other relevant information in real time through a WebSocket connection.

Hope this document can help you quickly understand our digital currency exchange WebSocket subscription message protocol. If you have any questions or need further assistance, please do not hesitate to contact our technical support team. I wish you a happy use!


## WEBSOCKET basic instructions

WebSocket is a network protocol for full-duplex communication over a single TCP connection, which provides a means of real-time data transfer between a client and a server. By using WebSocket, you can subscribe and receive real-time market data and other information from digital currency exchanges in real time.

## Connection instructions

Before subscribing to messages, you need to establish a WebSocket connection. Connection instructions are as follows:

### When subscribing to a public channel, use the address of the public service; when subscribing to a private channel, use the address of the private service

- Public channel: The public channel is a channel broadcast to all clients connected to the exchange, including market conditions, transaction depth and other information.
  For the access method, please refer to: [WEBSOCKET PUBLIC V2](#websocket-feed-public-v2)
- Private channel: A private channel refers to a channel that only pushes personal-related information to specific clients, such as order notifications, account balances, etc.
  For the access method, please refer to: [WEBSOCKET PRIVATE V2](#websocket-feed-private-v2)

Please select the corresponding service address to connect to public or private channels according to your needs.

## Subscription Limits

Each connection can send up to 50 messages in 1s, otherwise the connection will be closed forcibly

In order to maintain the stability and fairness of the connection, we have set a limit on sending messages, and each connection can send up to 50 messages per second. If you send more than 50 messages within 1 second, the connection will be forcibly closed, please be aware of this limit.

## keep the connection

<aside class="notice">
  <span style="color: blue;">
NOTE: This instruction currently only applies to the V2 release. </span>
</aside>

We will send ping messages regularly, expecting you to return pong messages as a response, if you do not receive your response for more than 30s, the server will close the connection

At the same time, you need to pay attention to the following situations:

Network problems: If there are network problems, the system will automatically disconnect.

Connection timeout: If the user does not subscribe within 30 seconds after the connection is successful or the server does not push data to the user within 30 seconds after the subscription, the system will automatically disconnect.

In order to ensure the liveness of the connection, we will regularly send ping messages in JSON format to the client: `{"ping": timestamp}`. You need to send a `{"pong": timestamp}` text message promptly after receiving the ping message to indicate that the connection is alive. If we do not receive a response from you within 30 seconds, we will close the connection and recommend the following:

1. Reply a `{"pong": timestamp}` immediately after receiving a `{"ping": timestamp}` message.

2. Expect a literal string `{"ping": timestamp}` as heartbeat message. If not received within N seconds, issue an error or reconnect.

3. The timestamp in the pong message you reply should use the timestamp in the received ping message.

<aside>
PING PONG EXAMPLE
</aside>
<a name="ping_pong_demo"></a>

> ping message example

```json

{
    "ping": 1635065532000
}

```
> pong message example

```json

{
    "pong": 1635065532000
}

```

## request error

<aside class="notice">
  <span style="color: blue;">
NOTE: This instruction currently only applies to the V2 release. </span>
</aside>

Regardless of the private channel or public channel, when the server fails to process the request you send, the server will return a unified error message, which is convenient for the client to process.

Error messages mainly consist of two parts: error code and message. Codes are generic, but messages may vary.

For error codes and messages, please refer to: [Status Code Comparison Table](#WSERR), [Other Error Status Code Comparison Table](#ERR2)

**Error Message Response Parameter Description**

| parameter name | type | description |
|:------|:-------|--------------------------|
| event | string | event name sent by user [event list](#events) |
| msg | string | error message |
| code | int | status code [status code comparison table](#WSERR) |


### Description of common error codes

1. **Error code `400`**: Usually you need to check whether the request parameters you provide are correct, or whether there are required parameters that are not filled.

2. **Error code `401`**: Usually you need to ensure that you have received a successful login response, and this error will occur when you subscribe to a private channel without logging in.

3. **Error code `500`**: It is usually an internal server error. It is recommended that you try again later.

<aside id="ws-error-ex-demo">
ERROR REQUEST EXAMPLE
</aside>

<a id="error_ws_request_response_demo" name="error_ws_request_response_demo"></a>

> Bad request example `1` The request structure used in this example is wrong, please replace it with your actual request parameters.


```json
{
    "event": "sub",
    "para": {
        "biz": "market",
        "type": "percent10",
        "product": "ETH_USDT"
    },
    "zip": true
}
```

> Bad request response example `1`

```json
{
    "event": "sub",
    "code": "400",
    "msg": "Invalid request: {\"event\":\"sub\",\"para\":{\"biz\":\"market\",\"type\":\"percent10\ ",\"pairCode\":\"ETH_USDT\"},\"zip\":true}"
}

```


> Bad request example `2` The access_key value used in this example is empty, please ensure that the required parameters are filled.

```json
{
  "event": "login",
  "params": {
    "type": "api",
    "access_key": "",
    "access_sign": "sign",
    "access_timestamp": 14000000000
  }
}

```

> Bad request response example `2`

```json
{
  "event": "login",
  "code": 40001,
  "msg": "ACCESS_KEY cannot be empty"
}
```

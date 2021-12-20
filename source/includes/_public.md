# 交易所公共接口
交易所公共接口

## 获取账单类型

<a id="opIdbillTypeUsingGET_1"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/public/billTypes");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```http
GET /example.com/openapi/exchange/public/billTypes HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/public/billTypes',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /openapi/exchange/public/billTypes`

> Example responses

> 200 Response

```json
[
  {
    "code": "BUY", //买入
    "name": "",
    "id": 7
  },
  {
    "code": "SELL", //卖出
    "name": "",
    "id": 8
  }
  }
]
```

<h3 id="获取账单类型-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="获取账单类型-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

## 获取币对信息

<a id="opIdcurrenciesUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/public/currencies");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```http
GET /example.com/openapi/exchange/public/currencies HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/public/currencies',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /openapi/exchange/public/currencies`

> Example responses

> 200 Response

```json
[
  {
    "baseIncrement": 0,
    "baseSymbol": "string",
    "id": 0,
    "lastPrice": 0,
    "makerFeesRate": 0,
    "maxPrice": 0,
    "maxVolume": 0,
    "minTrade": 0,
    "online": 0,
    "pairCode": "string",
    "quoteIncrement": 0,
    "quotePrecision": 0,
    "quoteSymbol": "string",
    "sort": 0,
    "tickerFeesRate": 0
  }
]
```

<h3 id="获取币对信息-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="获取币对信息-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[CurrencyPairDTO](#schemacurrencypairdto)]|false|none|[交易市场]|
|» CurrencyPairDTO|[CurrencyPairDTO](#schemacurrencypairdto)|false|none|交易市场|
|»» baseIncrement|number|false|none|交易数量最小交易变动单位|
|»» baseSymbol|string|false|none|交易货币 如:LTC/ETC|
|»» id|integer(int64)|false|none|none|
|»» lastPrice|number|false|none|最新价格|
|»» makerFeesRate|number|false|none|卖单方费率|
|»» maxPrice|integer(int32)|false|none|最高价格|
|»» maxVolume|integer(int32)|false|none|最大成交量|
|»» minTrade|number|false|none|最小委托|
|»» online|integer(int32)|false|none|是否上线|
|»» pairCode|string|false|none|交易对|
|»» quoteIncrement|number|false|none|最小交易单位|
|»» quotePrecision|integer(int32)|false|none|计价货币数量单位精度|
|»» quoteSymbol|string|false|none|计价货币 例人民币/美元/BTC|
|»» sort|integer(int32)|false|none|none|
|»» tickerFeesRate|number|false|none|买单方费率|

<aside class="success">
This operation does not require authentication
</aside>

## 获取所有档位深度

<a id="opIdgetMergeTypesUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/public/pairDepth");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```http
GET /example.com/openapi/exchange/public/pairDepth HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/public/pairDepth',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /openapi/exchange/public/pairDepth`

> Example responses

> 200 Response

```json
[
  {
    "createOn": "2019-08-24T14:15:22Z",
    "depthLevel": "string",
    "id": 0,
    "legalCoin": "string",
    "pairCode": "string",
    "updateOn": "2019-08-24T14:15:22Z"
  }
]
```

<h3 id="获取所有档位深度-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="获取所有档位深度-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[CurrencyPairDepth](#schemacurrencypairdepth)]|false|none|none|
|» CurrencyPairDepth|[CurrencyPairDepth](#schemacurrencypairdepth)|false|none|none|
|»» createOn|string(date-time)|false|none|none|
|»» depthLevel|string|false|none|none|
|»» id|integer(int64)|false|none|none|
|»» legalCoin|string|false|none|none|
|»» pairCode|string|false|none|none|
|»» updateOn|string(date-time)|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## 获取币种信息

<a id="opIdsymbolUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/public/symbol");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```http
GET /example.com/openapi/exchange/public/symbol HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/public/symbol',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /openapi/exchange/public/symbol`

> Example responses

> 200 Response

```json
[
  "BTC",
  "USDT",
  "ETH"
]
```

<h3 id="获取币种信息-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="获取币种信息-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

## 获取系统时间

<a id="opIdgetTimeUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/public/time");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```http
GET /example.com/openapi/exchange/public/time HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/public/time',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /openapi/exchange/public/time`

> Example responses

> 200 Response

```json
{
  "epoch": "1629971589.471",
  "iso": "2021-08-26T09:53:09.471Z",
  "timestamp": 1629971589471
}
```

<h3 id="获取系统时间-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[ServerTimeDTO](#schemaservertimedto)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="success">
This operation does not require authentication
</aside>

## 获取交易对K线图信息

<a id="opIdcandlesUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/public/{pairCode}/candles?interval=string");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```http
GET /example.com/openapi/exchange/public/{pairCode}/candles?interval=string HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/public/{pairCode}/candles?interval=string',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /openapi/exchange/public/{pairCode}/candles`

<h3 id="获取交易对k线图信息-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|end|query|string|false|结束时间|
|interval|query|string|true|interval|
|pairCode|path|string|true|交易对|
|start|query|string|false|开始时间|

> Example responses

> 200 Response

```json
[
  [
    1629971700000, //时间戳
    "3332.0400", //最低价
    "3332.0400", //最高价
    "3332.0400", //开盘价
    "3332.0400", //收盘价
    "0" //成交量
  ],
  [
    1629971400000,
    "3332.0400",
    "3332.0400",
    "3332.0400",
    "3332.0400",
    "0"
  ]
]
```

<h3 id="获取交易对k线图信息-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="获取交易对k线图信息-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

## 获取交易对风险准备金

<a id="opIdfillsUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/public/{pairCode}/fills");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```http
GET /example.com/openapi/exchange/public/{pairCode}/fills HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/public/{pairCode}/fills',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /openapi/exchange/public/{pairCode}/fills`

<h3 id="获取交易对风险准备金-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|limit|query|integer(int32)|false|limit|
|pairCode|path|string|true|pairCode|

> Example responses

> 200 Response

```json
[
  [
    {}
  ]
]
```

<h3 id="获取交易对风险准备金-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="获取交易对风险准备金-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

## 获取交易对深度信息

<a id="opIdorderBookUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/public/{pairCode}/orderBook");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```http
GET /example.com/openapi/exchange/public/{pairCode}/orderBook HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/public/{pairCode}/orderBook',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /openapi/exchange/public/{pairCode}/orderBook`

<h3 id="获取交易对深度信息-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pairCode|path|string|true|pairCode|
|size|query|integer(int32)|false|size|

> Example responses

> 200 Response

```json
{
  "asks": [
    [
      "3335.0000", //价格
      "1.0000" //数量
    ],
    [
      "3336.0000",
      "1.0000"
    ]
  ],
  "bids": [
    [
      "2712.0000",
      "0.0100"
    ],
    [
      "2710.0000",
      "91.6706"
    ],
    [
      "2700.0000",
      "84.6012"
    ],
    [
      "2685.0000",
      "100.0000"
    ]
  ]
}
```

<h3 id="获取交易对深度信息-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[OrderBookDTO](#schemaorderbookdto)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="success">
This operation does not require authentication
</aside>

## 获取交易对深度信息机器人

<a id="opIdorderBookSelfUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/public/{pairCode}/orderBook-robot");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```http
GET /example.com/openapi/exchange/public/{pairCode}/orderBook-robot HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/public/{pairCode}/orderBook-robot',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /openapi/exchange/public/{pairCode}/orderBook-robot`

<h3 id="获取交易对深度信息机器人-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pairCode|path|string|true|pairCode|
|size|query|integer(int32)|false|size|

> Example responses

> 200 Response

```json
{
  "asks": [
    [
      "string"
    ]
  ],
  "bids": [
    [
      "string"
    ]
  ]
}
```

<h3 id="获取交易对深度信息机器人-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[OrderBookDTO](#schemaorderbookdto)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="success">
This operation does not require authentication
</aside>

## 获取交易对档位深度

<a id="opIdgetMergeTypeListUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/public/{pairCode}/pairDepth");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```http
GET /example.com/openapi/exchange/public/{pairCode}/pairDepth HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/public/{pairCode}/pairDepth',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /openapi/exchange/public/{pairCode}/pairDepth`

<h3 id="获取交易对档位深度-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pairCode|path|string|true|pairCode|
|size|query|integer(int32)|false|size|

> Example responses

> 200 Response

```json
[
  {
    "createOn": "2019-08-24T14:15:22Z",
    "depthLevel": "string",
    "id": 0,
    "legalCoin": "string",
    "pairCode": "string",
    "updateOn": "2019-08-24T14:15:22Z"
  }
]
```

<h3 id="获取交易对档位深度-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="获取交易对档位深度-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[CurrencyPairDepthDTO](#schemacurrencypairdepthdto)]|false|none|[币种与法币对应关系]|
|» CurrencyPairDepthDTO|[CurrencyPairDepthDTO](#schemacurrencypairdepthdto)|false|none|币种与法币对应关系|
|»» createOn|string(date-time)|false|none|none|
|»» depthLevel|string|false|none|档位，保存 JSON 对象 [0.001, 0.01]'|
|»» id|integer(int64)|false|none|none|
|»» legalCoin|string|false|none|对应计价法币名称，USD、CNY、USDT|
|»» pairCode|string|false|none|交易对|
|»» updateOn|string(date-time)|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## 获取交易对最新成交信息

<a id="opIdtickerUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/public/{pairCode}/ticker");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```http
GET /example.com/openapi/exchange/public/{pairCode}/ticker HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/public/{pairCode}/ticker',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`GET /openapi/exchange/public/{pairCode}/ticker`

<h3 id="获取交易对最新成交信息-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pairCode|path|string|true|pairCode|

> Example responses

> 200 Response

```json
{
  "buy": "string",
  "change24": "string",
  "changePercentage": "string",
  "changeRate24": "string",
  "close": "string",
  "createOn": "2019-08-24T14:15:22Z",
  "high": "string",
  "high24": "string",
  "last": "string",
  "low": "string",
  "low24": "string",
  "open": "string",
  "pairCode": "string",
  "quoteVolume": "string",
  "sell": "string",
  "volume": "string"
}
```

<h3 id="获取交易对最新成交信息-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[TickerDTO](#schematickerdto)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="success">
This operation does not require authentication
</aside>

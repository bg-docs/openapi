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

`GET /openapi/exchange/public/products/{pairCode}/candles`

<h3 id="获取交易对k线图信息-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|end|query|string|false|结束时间|
|interval|query|string|true|interval["1min", "5min", "15min", "30min", "60min", "4hour", "1day", "1week", "1mon"]|
|pairCode|path|string|true|交易对|
|start|query|string|true|开始时间|
|size|query|string|true|[1,2000]|

> Example responses

> 200 Response

```json
{
	"code": 200,
	"data": [{
		"close": 11.9,
		"count": 0,
		"high": 11.9,
		"id": 1640932860,
		"low": 11.9,
		"open": 11.9,
		"turnOver": 0,
		"vol": 0
	}, {
		"close": 11.9,
		"count": 0,
		"high": 11.9,
		"id": 1640932920,
		"low": 11.9,
		"open": 11.9,
		"turnOver": 0,
		"vol": 0
	}, {
		"close": 11.9,
		"count": 0,
		"high": 11.9,
		"id": 1640932980,
		"low": 11.9,
		"open": 11.9,
		"turnOver": 0,
		"vol": 0
	}, {
		"close": 11.9,
		"count": 0,
		"high": 11.9,
		"id": 1640933040,
		"low": 11.9,
		"open": 11.9,
		"turnOver": 0,
		"vol": 0
	}],
	"interval": "1min",
	"msg": "success",
	"productId": "ETH_USDT",
	"ts": 1640933046424
}
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
GET /example.com/openapi/exchange/public/products/{pairCode}/orderBook HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/public/products/{pairCode}/orderBook',
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
|interval|query|string|false|step[`5`,`10`,`15`,`30`]|

> Example responses

> 200 Response

```json
{
	"interval": "step5",
	"status": "ok",
	"ts": 1640932627885,
	"type": "orderBook",
	"tick": {
		"seqId": 2875,
		"id": 1640932627,
		"bids": [
			[12, 0.10124]
		],
		"ts": 1640932627020,
		"version": 1640932627,
		"type": "orderBook",
		"pairCode": "ETH_USDT",
		"interval": "5"
	}
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
URL obj = new URL("/example.com/openapi/exchange/public/products/{pairCode}/trade");
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
GET /example.com/openapi/exchange/public/products/{pairCode}/trade HTTP/1.1

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
	"status": "ok",
	"tick": {
		"data": [{
			"direction": "sell",
			"id": 28730000,
			"price": "11.9",
			"ts": 1639585820376,
			"vol": "1"
		}],
		"id": 1640933236175,
		"ts": 1640933236175
	},
	"ts": 1640933236175
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


## 获取交易对24小时交易信息

<a id="opIdtickerUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/public/products/{pairCode}/ticker");
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
GET /example.com/openapi/exchange/public/products/{pairCode}/ticker HTTP/1.1

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

<h3 id="获取交易对获取交易对24小时交易信息-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pairCode|path|string|true|pairCode|

> Example responses

> 200 Response

```json
{
	"ch": "market.ETH_USDT.detail",
	"status": "ok",
	"tick": {
		"open": "11.9",
		"close": "11.9",
		"low": "11.9",
		"high": "11.9",
		"turnOver": "0",
		"count": 0,
		"vol": "0",
		"pairCode": "ETH_USDT",
		"change": "0",
		"changePercent": "0"
	},
	"ts": 1640933141753
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






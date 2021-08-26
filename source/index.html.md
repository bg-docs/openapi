---
title: 启航星辰交易所OpenApi接口说明 v1.0
language_tabs:
  - java: Java
  - http: HTTP
  - javascript: JavaScript
language_clients:
  - java: ""
  - http: ""
  - javascript: ""
toc_footers: []
includes: []
search: false
highlight_theme: darkula
headingLevel: 2

---

<!-- Generator: Widdershins v4.0.1 -->

<h1 id="-openapi-">启航星辰交易所OpenApi接口说明 v1.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

接口文档

Base URLs:

* <a href="//example.com/">//example.com/</a>

Email: <a href="mailto:help@qihangxingchen.com">help@qihangxingchen.com</a> 

<h1 id="-openapi--assets-controller">用户资产相关接口</h1>

用户资产相关接口

## 获取资产信息

<a id="opIdgetUserAllCurrencyAssetUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/assets");
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
GET /example.com/openapi/exchange/assets HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/assets',
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

`GET /openapi/exchange/assets`

获取所有的资产信息

> Example responses

> 200 Response

```json
[
  {
    "available": 0,
    "baseBTC": 0,
    "brokerId": 0,
    "hold": 0,
    "sort": 0,
    "symbol": "string",
    "transfer": true,
    "userId": 0,
    "withdrawLimit": 0
  }
]
```

<h3 id="获取资产信息-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="获取资产信息-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[UserAssetsDTO](#schemauserassetsdto)]|false|none|[交易资产]|
|» UserAssetsDTO|[UserAssetsDTO](#schemauserassetsdto)|false|none|交易资产|
|»» available|number|false|none|余额|
|»» baseBTC|number|false|none|none|
|»» brokerId|integer(int32)|false|none|业务方ID|
|»» hold|number|false|none|冻结|
|»» sort|integer(int32)|false|none|none|
|»» symbol|string|false|none|币种|
|»» transfer|boolean|false|none|none|
|»» userId|integer(int64)|false|none|none|
|»» withdrawLimit|number|false|none|提币限额|

<aside class="success">
This operation does not require authentication
</aside>

## 获取币种下资产信息

<a id="opIdgetUserCurrencyAssetUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/{symbol}/assets");
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
GET /example.com/openapi/exchange/{symbol}/assets HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/{symbol}/assets',
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

`GET /openapi/exchange/{symbol}/assets`

获取币种下的资产信息

<h3 id="获取币种下资产信息-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|symbol|path|string|true|币种|

> Example responses

> 200 Response

```json
{
  "available": 0, 
  "baseBTC": 0,
  "brokerId": 0,
  "hold": 0,
  "sort": 0,
  "symbol": "string",
  "transfer": true,
  "userId": 0,
  "withdrawLimit": 0
}
```

<h3 id="获取币种下资产信息-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[UserAssetsDTO](#schemauserassetsdto)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="获取资产信息-responseschema">Response Schema</h3>
Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[UserAssetsDTO](#schemauserassetsdto)]|false|none|[交易资产]|
|» UserAssetsDTO|[UserAssetsDTO](#schemauserassetsdto)|false|none|交易资产|
|»» available|number|false|none|余额|
|»» baseBTC|number|false|none|none|
|»» brokerId|integer(int32)|false|none|业务方ID|
|»» hold|number|false|none|冻结|
|»» sort|integer(int32)|false|none|none|
|»» symbol|string|false|none|币种|
|»» transfer|boolean|false|none|none|
|»» userId|integer(int64)|false|none|none|
|»» withdrawLimit|number|false|none|提币限额|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="-openapi--bill-controller">账单相关接口</h1>

账单相关接口

## 获取账单类型

<a id="opIdbillTypeUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/billTypes");
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
GET /example.com/openapi/exchange/billTypes HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/billTypes',
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

`GET /openapi/exchange/billTypes`

> Example responses

> 200 Response

```json
[
  {
    "code": "BUY",//买入
    "name": "",
    "id": 7
  },
  {
    "code": "SELL",//卖出
    "name": "",
    "id": 8
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

## 获取账单信息

<a id="opIdbillListUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/bills");
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
GET /example.com/openapi/exchange/bills HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/bills',
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

`GET /openapi/exchange/bills`

<h3 id="获取账单信息-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|endDate|query|string|false|结束时间|
|isHistory|query|string|false|是否查看历史订单|
|page|query|integer(int32)|false|page|
|pageSize|query|integer(int32)|false|pageSize|
|startDate|query|string|false|开始时间|
|symbol|query|string|false|币种|
|type|query|string|false|账单类型|

> Example responses

> 200 Response

```json
{
  "bills": [
    {
      "afterAssets": 0,
      "amount": 0,
      "assets": 0,
      "beforeAssets": 0,
      "brokerId": 0,
      "createOn": 0,
      "fee": 0,
      "id": 0,
      "makerTaker": "string",
      "pairCode": "string",
      "price": 0,
      "referId": 0,
      "symbol": "string",
      "tradeNo": "string",
      "type": 0,
      "updateOn": 0,
      "userId": 0
    }
  ],
  "paginate": {
    "page": 0,
    "pageSize": 0,
    "total": 0
  }
}
```
|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[BillResult](#schemabillresult)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="获取账单信息-responses">Responses</h3>

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|afterAssets|number|false|none|事后余额|
|amount|number|false|none|变换金额  +增加 -减少|
|assets|number|false|none|余额|
|beforeAssets|number|false|none|事前余额|
|brokerId|integer(int32)|false|none|业务方ID|
|createOn|integer(int64)|false|none|none|
|fee|number|false|none|手续费|
|id|integer(int64)|false|none|none|
|makerTaker|string|false|none|成交类型|
|pairCode|string|false|none|交易对|
|price|number|false|none|成交价|
|referId|integer(int64)|false|none|关联id|
|symbol|string|false|none|币种|
|tradeNo|string|false|none|订单号|
|type|integer(int32)|false|none|账单类型 1:充值 2:提现 3:由借款账户转入 4:转入借款账户 5:由放款账户转入 6:转入放款账户|
|updateOn|integer(int64)|false|none|none|
|userId|integer(int64)|false|none|none|



<aside class="success">
This operation does not require authentication
</aside>

<h1 id="-openapi--order-controller">订单相关接口</h1>

订单相关接口

## 获取订单

<a id="opIdorderAllUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/orders");
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
GET /example.com/openapi/exchange/orders HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/orders',
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

`GET /openapi/exchange/orders`

可指定搜索条件

<h3 id="获取订单-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|amount|query|string|false|数量|
|endDate|query|string|false|结束时间|
|page|query|integer(int32)|false|page|
|pageSize|query|integer(int32)|false|pageSize|
|pairCode|query|string|false|交易对|
|price|query|string|false|价格|
|source|query|string|false|下单来源|
|startDate|query|string|false|开始时间|
|systemOrderType|query|string|false|下单类型|

> Example responses

> 200 Response

```json
[
  {
    "amount": "string",
    "averagePrice": "string",
    "brokerId": 0,
    "createOn": 0,
    "dealAmount": "string",
    "dealQuoteAmount": "string",
    "entrustPrice": "string",
    "id": 0,
    "notStrike": "string",
    "openAmount": "string",
    "pairCode": "string",
    "quoteAmount": "string",
    "side": "string",
    "sourceInfo": "string",
    "status": 0,
    "symbol": "string",
    "systemOrderType": 0,
    "trunOver": "string",
    "updateOn": 0,
    "userId": 0
  }
]
```

<h3 id="获取订单-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="获取订单-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[OrdersDTO](#schemaordersdto)]|false|none|[订单]|
|» OrdersDTO|[OrdersDTO](#schemaordersdto)|false|none|订单|
|»» amount|string|false|none|委托数量|
|»» averagePrice|string|false|none|均价|
|»» brokerId|integer(int32)|false|none|业务方ID|
|»» createOn|integer(int64)|false|none|none|
|»» dealAmount|string|false|none|已成交数量|
|»» dealQuoteAmount|string|false|none|基准币已成交数量|
|»» entrustPrice|string|false|none|用户订单委托价格|
|»» id|integer(int64)|false|none|none|
|»» notStrike|string|false|none|none|
|»» openAmount|string|false|none|none|
|»» pairCode|string|false|none|交易对|
|»» quoteAmount|string|false|none|基准币数量|
|»» side|string|false|none|仓位类型，buy买，sell卖|
|»» sourceInfo|string|false|none|下单来源|
|»» status|integer(int32)|false|none|0:未成交 1:部分成交 2:完全成交 3:撤单中 -1:已撤单'|
|»» symbol|string|false|none|币种|
|»» systemOrderType|integer(int32)|false|none|10:限价 11:市价|
|»» trunOver|string|false|none|none|
|»» updateOn|integer(int64)|false|none|none|
|»» userId|integer(int64)|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## 批量下单

<a id="opIdbulkOrdersUsingPOST"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/{pairCode}/bulkOrders");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
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
POST /example.com/openapi/exchange/{pairCode}/bulkOrders HTTP/1.1

Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '[
  {
    "price": 0,
    "quoteVolume": 0,
    "side": "string",
    "source": "string",
    "systemOrderType": "string",
    "volume": 0
  }
]';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/{pairCode}/bulkOrders',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /openapi/exchange/{pairCode}/bulkOrders`

> Body parameter

```json
[
  {
    "price": 0,
    "quoteVolume": 0,
    "side": "string",
    "source": "string",
    "systemOrderType": "string",
    "volume": 0
  }
]
```

<h3 id="批量下单-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pairCode|path|string|true|pairCode|
|body|body|[OrdersParamDTO](#schemaordersparamdto)|true|ordersList|

> Example responses

> 200 Response

```json
[
  {
    "amount": "string",
    "averagePrice": "string",
    "brokerId": 0,
    "createOn": 0,
    "dealAmount": "string",
    "dealQuoteAmount": "string",
    "entrustPrice": "string",
    "id": 0,
    "notStrike": "string",
    "openAmount": "string",
    "pairCode": "string",
    "quoteAmount": "string",
    "side": "string",
    "sourceInfo": "string",
    "status": 0,
    "symbol": "string",
    "systemOrderType": 0,
    "trunOver": "string",
    "updateOn": 0,
    "userId": 0
  }
]
```

<h3 id="批量下单-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="批量下单-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[OrdersDTO](#schemaordersdto)]|false|none|[订单]|
|» OrdersDTO|[OrdersDTO](#schemaordersdto)|false|none|订单|
|»» amount|string|false|none|委托数量|
|»» averagePrice|string|false|none|均价|
|»» brokerId|integer(int32)|false|none|业务方ID|
|»» createOn|integer(int64)|false|none|none|
|»» dealAmount|string|false|none|已成交数量|
|»» dealQuoteAmount|string|false|none|基准币已成交数量|
|»» entrustPrice|string|false|none|用户订单委托价格|
|»» id|integer(int64)|false|none|none|
|»» notStrike|string|false|none|none|
|»» openAmount|string|false|none|none|
|»» pairCode|string|false|none|交易对|
|»» quoteAmount|string|false|none|基准币数量|
|»» side|string|false|none|仓位类型，buy买，sell卖|
|»» sourceInfo|string|false|none|下单来源|
|»» status|integer(int32)|false|none|0:未成交 1:部分成交 2:完全成交 3:撤单中 -1:已撤单'|
|»» symbol|string|false|none|币种|
|»» systemOrderType|integer(int32)|false|none|10:限价 11:市价|
|»» trunOver|string|false|none|none|
|»» updateOn|integer(int64)|false|none|none|
|»» userId|integer(int64)|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## 撤销指定交易对的全部订单

<a id="opIdcancelAllUsingDELETE"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/{pairCode}/cancel-all");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
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
DELETE /example.com/openapi/exchange/{pairCode}/cancel-all HTTP/1.1

```

```javascript

fetch('/example.com/openapi/exchange/{pairCode}/cancel-all',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /openapi/exchange/{pairCode}/cancel-all`

<h3 id="撤销指定交易对的全部订单-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pairCode|path|string|true|pairCode|

<h3 id="撤销指定交易对的全部订单-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<aside class="success">
This operation does not require authentication
</aside>

## 批量撤销指定交易对订单

<a id="opIdcancelPriceUsingDELETE"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/{pairCode}/cancel-price");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
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
DELETE /example.com/openapi/exchange/{pairCode}/cancel-price HTTP/1.1

```

```javascript

fetch('/example.com/openapi/exchange/{pairCode}/cancel-price',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /openapi/exchange/{pairCode}/cancel-price`

指定价格区间

<h3 id="批量撤销指定交易对订单-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|maxPrice|query|string|false|最高价|
|minPrice|query|string|false|最低价|
|pairCode|path|string|true|交易对|
|side|query|string|false|side|

<h3 id="批量撤销指定交易对订单-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<aside class="success">
This operation does not require authentication
</aside>

## 批量撤销指定交易对下的订单

<a id="opIdcancelByIdsUsingDELETE"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/{pairCode}/cancelByIds?ids=0");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
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
DELETE /example.com/openapi/exchange/{pairCode}/cancelByIds?ids=0 HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/{pairCode}/cancelByIds?ids=0',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /openapi/exchange/{pairCode}/cancelByIds`

指定券商

<h3 id="批量撤销指定交易对下的订单-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|ids|query|array[integer]|true|ids|
|pairCode|path|string|true|pairCode|

> Example responses

> 200 Response

```json
{
  "property1": [
    0
  ],
  "property2": [
    0
  ]
}
```

<h3 id="批量撤销指定交易对下的订单-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="批量撤销指定交易对下的订单-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» **additionalProperties**|[integer]|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## 获取指定交易对下的完成订单

<a id="opIdorderFinishUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/{pairCode}/fulfillment");
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
GET /example.com/openapi/exchange/{pairCode}/fulfillment HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/{pairCode}/fulfillment',
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

`GET /openapi/exchange/{pairCode}/fulfillment`

可设置搜索条件

<h3 id="获取指定交易对下的完成订单-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|amount|query|string|false|数量|
|endDate|query|string|false|结束时间|
|isHistory|query|boolean|false|isHistory|
|page|query|integer(int32)|false|page|
|pageSize|query|integer(int32)|false|pageSize|
|pairCode|path|string|true|交易对|
|price|query|string|false|价格|
|source|query|string|false|下单来源|
|startDate|query|string|false|开始时间|
|systemOrderType|query|string|false|下单类型|

> Example responses

> 200 Response

```json
[
  {
    "amount": "string",
    "averagePrice": "string",
    "brokerId": 0,
    "createOn": 0,
    "dealAmount": "string",
    "dealQuoteAmount": "string",
    "entrustPrice": "string",
    "id": 0,
    "notStrike": "string",
    "openAmount": "string",
    "pairCode": "string",
    "quoteAmount": "string",
    "side": "string",
    "sourceInfo": "string",
    "status": 0,
    "symbol": "string",
    "systemOrderType": 0,
    "trunOver": "string",
    "updateOn": 0,
    "userId": 0
  }
]
```

<h3 id="获取指定交易对下的完成订单-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="获取指定交易对下的完成订单-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[OrdersDTO](#schemaordersdto)]|false|none|[订单]|
|» OrdersDTO|[OrdersDTO](#schemaordersdto)|false|none|订单|
|»» amount|string|false|none|委托数量|
|»» averagePrice|string|false|none|均价|
|»» brokerId|integer(int32)|false|none|业务方ID|
|»» createOn|integer(int64)|false|none|none|
|»» dealAmount|string|false|none|已成交数量|
|»» dealQuoteAmount|string|false|none|基准币已成交数量|
|»» entrustPrice|string|false|none|用户订单委托价格|
|»» id|integer(int64)|false|none|none|
|»» notStrike|string|false|none|none|
|»» openAmount|string|false|none|none|
|»» pairCode|string|false|none|交易对|
|»» quoteAmount|string|false|none|基准币数量|
|»» side|string|false|none|仓位类型，buy买，sell卖|
|»» sourceInfo|string|false|none|下单来源|
|»» status|integer(int32)|false|none|0:未成交 1:部分成交 2:完全成交 3:撤单中 -1:已撤单'|
|»» symbol|string|false|none|币种|
|»» systemOrderType|integer(int32)|false|none|10:限价 11:市价|
|»» trunOver|string|false|none|none|
|»» updateOn|integer(int64)|false|none|none|
|»» userId|integer(int64)|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## 添加交易对订单

<a id="opIdaddUsingPOST"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/{pairCode}/orders");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
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
POST /example.com/openapi/exchange/{pairCode}/orders HTTP/1.1

Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "price": 0,
  "quoteVolume": 0,
  "side": "string",
  "source": "string",
  "systemOrderType": "string",
  "volume": 0
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/{pairCode}/orders',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`POST /openapi/exchange/{pairCode}/orders`

> Body parameter

```json
{
  "price": 0,
  "quoteVolume": 0,
  "side": "string",
  "source": "string",
  "systemOrderType": "string",
  "volume": 0
}
```

<h3 id="添加交易对订单-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pairCode|path|string|true|交易对|
|body|body|[OrdersParamDTO](#schemaordersparamdto)|true|orderParam|

> Example responses

> 200 Response

```json
118001244083232 //订单号
```

<h3 id="添加交易对订单-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|integer|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Created|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="success">
This operation does not require authentication
</aside>

## 批量撤销指定交易对的订单

<a id="opIdbatchCancelUsingDELETE"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/{pairCode}/orders");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
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
DELETE /example.com/openapi/exchange/{pairCode}/orders HTTP/1.1

Content-Type: application/json

```

```javascript
const inputBody = '[
  0
]';
const headers = {
  'Content-Type':'application/json'
};

fetch('/example.com/openapi/exchange/{pairCode}/orders',
{
  method: 'DELETE',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /openapi/exchange/{pairCode}/orders`

> Body parameter

```json
[
  0
]
```

<h3 id="批量撤销指定交易对的订单-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pairCode|path|string|true|pairCode|
|body|body|array[integer]|true|ids|

<h3 id="批量撤销指定交易对的订单-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<aside class="success">
This operation does not require authentication
</aside>

## 获取指定交易对下指定订单号的订单

<a id="opIdorderByIdUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/{pairCode}/orders/{id}");
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
GET /example.com/openapi/exchange/{pairCode}/orders/{id} HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/{pairCode}/orders/{id}',
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

`GET /openapi/exchange/{pairCode}/orders/{id}`

<h3 id="获取指定交易对下指定订单号的订单-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|id|
|pairCode|path|string|true|pairCode|

> Example responses

> 200 Response

```json
{
  "amount": "string",
  "averagePrice": "string",
  "brokerId": 0,
  "createOn": 0,
  "dealAmount": "string",
  "dealQuoteAmount": "string",
  "entrustPrice": "string",
  "id": 0,
  "notStrike": "string",
  "openAmount": "string",
  "pairCode": "string",
  "quoteAmount": "string",
  "side": "string",
  "sourceInfo": "string",
  "status": 0,
  "symbol": "string",
  "systemOrderType": 0,
  "trunOver": "string",
  "updateOn": 0,
  "userId": 0
}
```

<h3 id="获取指定交易对下指定订单号的订单-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[OrdersDTO](#schemaordersdto)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="success">
This operation does not require authentication
</aside>

## 撤销指定交易对下指定ID的订单

<a id="opIdcancelUsingDELETE"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/{pairCode}/orders/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
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
DELETE /example.com/openapi/exchange/{pairCode}/orders/{id} HTTP/1.1

```

```javascript

fetch('/example.com/openapi/exchange/{pairCode}/orders/{id}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

`DELETE /openapi/exchange/{pairCode}/orders/{id}`

<h3 id="撤销指定交易对下指定id的订单-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|用户id|
|pairCode|path|string|true|交易对|

<h3 id="撤销指定交易对下指定id的订单-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="-openapi--public-controller">交易所公共接口</h1>

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

# Schemas

<h2 id="tocS_BillDTO">BillDTO</h2>
<!-- backwards compatibility -->
<a id="schemabilldto"></a>
<a id="schema_BillDTO"></a>
<a id="tocSbilldto"></a>
<a id="tocsbilldto"></a>

```json
{
  "afterAssets": 0,
  "amount": 0,
  "assets": 0,
  "beforeAssets": 0,
  "brokerId": 0,
  "createOn": 0,
  "fee": 0,
  "id": 0,
  "makerTaker": "string",
  "pairCode": "string",
  "price": 0,
  "referId": 0,
  "symbol": "string",
  "tradeNo": "string",
  "type": 0,
  "updateOn": 0,
  "userId": 0
}

```

BillDTO

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|afterAssets|number|false|none|事后余额|
|amount|number|false|none|变换金额  +增加 -减少|
|assets|number|false|none|余额|
|beforeAssets|number|false|none|事前余额|
|brokerId|integer(int32)|false|none|业务方ID|
|createOn|integer(int64)|false|none|none|
|fee|number|false|none|手续费|
|id|integer(int64)|false|none|none|
|makerTaker|string|false|none|成交类型|
|pairCode|string|false|none|交易对|
|price|number|false|none|成交价|
|referId|integer(int64)|false|none|关联id|
|symbol|string|false|none|币种|
|tradeNo|string|false|none|订单号|
|type|integer(int32)|false|none|账单类型 1:充值 2:提现 3:由借款账户转入 4:转入借款账户 5:由放款账户转入 6:转入放款账户|
|updateOn|integer(int64)|false|none|none|
|userId|integer(int64)|false|none|none|

<h2 id="tocS_BillResult">BillResult</h2>
<!-- backwards compatibility -->
<a id="schemabillresult"></a>
<a id="schema_BillResult"></a>
<a id="tocSbillresult"></a>
<a id="tocsbillresult"></a>

```json
{
  "bills": [
    {
      "afterAssets": 0,
      "amount": 0,
      "assets": 0,
      "beforeAssets": 0,
      "brokerId": 0,
      "createOn": 0,
      "fee": 0,
      "id": 0,
      "makerTaker": "string",
      "pairCode": "string",
      "price": 0,
      "referId": 0,
      "symbol": "string",
      "tradeNo": "string",
      "type": 0,
      "updateOn": 0,
      "userId": 0
    }
  ],
  "paginate": {
    "page": 0,
    "pageSize": 0,
    "total": 0
  }
}

```

BillResult

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bills|[[BillDTO](#schemabilldto)]|false|none|[账单]|
|paginate|[ParamPageDTO](#schemaparampagedto)|false|none|none|

<h2 id="tocS_CurrencyPairDTO">CurrencyPairDTO</h2>
<!-- backwards compatibility -->
<a id="schemacurrencypairdto"></a>
<a id="schema_CurrencyPairDTO"></a>
<a id="tocScurrencypairdto"></a>
<a id="tocscurrencypairdto"></a>

```json
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

```

CurrencyPairDTO

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|baseIncrement|number|false|none|交易数量最小交易变动单位|
|baseSymbol|string|false|none|交易货币 如:LTC/ETC|
|id|integer(int64)|false|none|none|
|lastPrice|number|false|none|最新价格|
|makerFeesRate|number|false|none|卖单方费率|
|maxPrice|integer(int32)|false|none|最高价格|
|maxVolume|integer(int32)|false|none|最大成交量|
|minTrade|number|false|none|最小委托|
|online|integer(int32)|false|none|是否上线|
|pairCode|string|false|none|交易对|
|quoteIncrement|number|false|none|最小交易单位|
|quotePrecision|integer(int32)|false|none|计价货币数量单位精度|
|quoteSymbol|string|false|none|计价货币 例人民币/美元/BTC|
|sort|integer(int32)|false|none|none|
|tickerFeesRate|number|false|none|买单方费率|

<h2 id="tocS_CurrencyPairDepth">CurrencyPairDepth</h2>
<!-- backwards compatibility -->
<a id="schemacurrencypairdepth"></a>
<a id="schema_CurrencyPairDepth"></a>
<a id="tocScurrencypairdepth"></a>
<a id="tocscurrencypairdepth"></a>

```json
{
  "createOn": "2019-08-24T14:15:22Z",
  "depthLevel": "string",
  "id": 0,
  "legalCoin": "string",
  "pairCode": "string",
  "updateOn": "2019-08-24T14:15:22Z"
}

```

CurrencyPairDepth

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|createOn|string(date-time)|false|none|none|
|depthLevel|string|false|none|none|
|id|integer(int64)|false|none|none|
|legalCoin|string|false|none|none|
|pairCode|string|false|none|none|
|updateOn|string(date-time)|false|none|none|

<h2 id="tocS_CurrencyPairDepthDTO">CurrencyPairDepthDTO</h2>
<!-- backwards compatibility -->
<a id="schemacurrencypairdepthdto"></a>
<a id="schema_CurrencyPairDepthDTO"></a>
<a id="tocScurrencypairdepthdto"></a>
<a id="tocscurrencypairdepthdto"></a>

```json
{
  "createOn": "2019-08-24T14:15:22Z",
  "depthLevel": "string",
  "id": 0,
  "legalCoin": "string",
  "pairCode": "string",
  "updateOn": "2019-08-24T14:15:22Z"
}

```

CurrencyPairDepthDTO

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|createOn|string(date-time)|false|none|none|
|depthLevel|string|false|none|档位，保存 JSON 对象 [0.001, 0.01]'|
|id|integer(int64)|false|none|none|
|legalCoin|string|false|none|对应计价法币名称，USD、CNY、USDT|
|pairCode|string|false|none|交易对|
|updateOn|string(date-time)|false|none|none|

<h2 id="tocS_OrderBookDTO">OrderBookDTO</h2>
<!-- backwards compatibility -->
<a id="schemaorderbookdto"></a>
<a id="schema_OrderBookDTO"></a>
<a id="tocSorderbookdto"></a>
<a id="tocsorderbookdto"></a>

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

OrderBookDTO

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|asks|[array]|false|none|none|
|bids|[array]|false|none|none|

<h2 id="tocS_OrdersDTO">OrdersDTO</h2>
<!-- backwards compatibility -->
<a id="schemaordersdto"></a>
<a id="schema_OrdersDTO"></a>
<a id="tocSordersdto"></a>
<a id="tocsordersdto"></a>

```json
{
  "amount": "string",
  "averagePrice": "string",
  "brokerId": 0,
  "createOn": 0,
  "dealAmount": "string",
  "dealQuoteAmount": "string",
  "entrustPrice": "string",
  "id": 0,
  "notStrike": "string",
  "openAmount": "string",
  "pairCode": "string",
  "quoteAmount": "string",
  "side": "string",
  "sourceInfo": "string",
  "status": 0,
  "symbol": "string",
  "systemOrderType": 0,
  "trunOver": "string",
  "updateOn": 0,
  "userId": 0
}

```

OrdersDTO

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|amount|string|false|none|委托数量|
|averagePrice|string|false|none|均价|
|brokerId|integer(int32)|false|none|业务方ID|
|createOn|integer(int64)|false|none|none|
|dealAmount|string|false|none|已成交数量|
|dealQuoteAmount|string|false|none|基准币已成交数量|
|entrustPrice|string|false|none|用户订单委托价格|
|id|integer(int64)|false|none|none|
|notStrike|string|false|none|none|
|openAmount|string|false|none|none|
|pairCode|string|false|none|交易对|
|quoteAmount|string|false|none|基准币数量|
|side|string|false|none|仓位类型，buy买，sell卖|
|sourceInfo|string|false|none|下单来源|
|status|integer(int32)|false|none|0:未成交 1:部分成交 2:完全成交 3:撤单中 -1:已撤单'|
|symbol|string|false|none|币种|
|systemOrderType|integer(int32)|false|none|10:限价 11:市价|
|trunOver|string|false|none|none|
|updateOn|integer(int64)|false|none|none|
|userId|integer(int64)|false|none|none|

<h2 id="tocS_OrdersParamDTO">OrdersParamDTO</h2>
<!-- backwards compatibility -->
<a id="schemaordersparamdto"></a>
<a id="schema_OrdersParamDTO"></a>
<a id="tocSordersparamdto"></a>
<a id="tocsordersparamdto"></a>

```json
{
  "price": 0,
  "quoteVolume": 0,
  "side": "string",
  "source": "string",
  "systemOrderType": "string",
  "volume": 0
}

```

OrdersParamDTO

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|price|number|false|none|价格|
|quoteVolume|number|false|none|计价币成交量|
|side|string|false|none|仓位类型，buy买，sell卖|
|source|string|false|none|none|
|systemOrderType|string|false|none|10:限价 11:市价|
|volume|number|false|none|成交量|

<h2 id="tocS_ParamPageDTO">ParamPageDTO</h2>
<!-- backwards compatibility -->
<a id="schemaparampagedto"></a>
<a id="schema_ParamPageDTO"></a>
<a id="tocSparampagedto"></a>
<a id="tocsparampagedto"></a>

```json
{
  "page": 0,
  "pageSize": 0,
  "total": 0
}

```

ParamPageDTO

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|page|integer(int32)|false|none|none|
|pageSize|integer(int32)|false|none|none|
|total|integer(int32)|false|none|none|

<h2 id="tocS_ServerTimeDTO">ServerTimeDTO</h2>
<!-- backwards compatibility -->
<a id="schemaservertimedto"></a>
<a id="schema_ServerTimeDTO"></a>
<a id="tocSservertimedto"></a>
<a id="tocsservertimedto"></a>

```json
{
  "epoch": "string",
  "iso": "string",
  "timestamp": 0
}

```

ServerTimeDTO

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|epoch|string|false|none|none|
|iso|string|false|none|none|
|timestamp|integer(int64)|false|none|none|

<h2 id="tocS_TickerDTO">TickerDTO</h2>
<!-- backwards compatibility -->
<a id="schematickerdto"></a>
<a id="schema_TickerDTO"></a>
<a id="tocStickerdto"></a>
<a id="tocstickerdto"></a>

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

TickerDTO

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|buy|string|false|none|none|
|change24|string|false|none|24小时变化值|
|changePercentage|string|false|none|none|
|changeRate24|string|false|none|24小时涨跌比例|
|close|string|false|none|none|
|createOn|string(date-time)|false|none|none|
|high|string|false|none|none|
|high24|string|false|none|none|
|last|string|false|none|none|
|low|string|false|none|none|
|low24|string|false|none|none|
|open|string|false|none|none|
|pairCode|string|false|none|交易对|
|quoteVolume|string|false|none|计价币成交量|
|sell|string|false|none|none|
|volume|string|false|none|成交量|

<h2 id="tocS_Type">Type</h2>
<!-- backwards compatibility -->
<a id="schematype"></a>
<a id="schema_Type"></a>
<a id="tocStype"></a>
<a id="tocstype"></a>

```json
{
  "typeName": "string"
}

```

Type

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|typeName|string|false|none|none|

<h2 id="tocS_UserAssetsDTO">UserAssetsDTO</h2>
<!-- backwards compatibility -->
<a id="schemauserassetsdto"></a>
<a id="schema_UserAssetsDTO"></a>
<a id="tocSuserassetsdto"></a>
<a id="tocsuserassetsdto"></a>

```json
{
  "available": 0,
  "baseBTC": 0,
  "brokerId": 0,
  "hold": 0,
  "sort": 0,
  "symbol": "string",
  "transfer": true,
  "userId": 0,
  "withdrawLimit": 0
}

```

UserAssetsDTO

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|available|number|false|none|余额|
|baseBTC|number|false|none|none|
|brokerId|integer(int32)|false|none|业务方ID|
|hold|number|false|none|冻结|
|sort|integer(int32)|false|none|none|
|symbol|string|false|none|币种|
|transfer|boolean|false|none|none|
|userId|integer(int64)|false|none|none|
|withdrawLimit|number|false|none|提币限额|



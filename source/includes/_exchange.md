# 订单相关接口
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
    "currency": "string",
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
|»» currency|string|false|none|币种|
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
    "currency": "string",
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
|»» currency|string|false|none|币种|
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
    "currency": "string",
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
|»» currency|string|false|none|币种|
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

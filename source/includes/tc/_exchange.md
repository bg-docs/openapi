# 訂單相關接口
訂單相關接口

## 獲取訂單

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

可指定搜索條件

<h3 id="獲取訂單-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|amount|query|string|false|數量|
|endDate|query|string|false|結束時間|
|page|query|integer(int32)|false|page|
|pageSize|query|integer(int32)|false|pageSize|
|pairCode|query|string|false|交易對|
|price|query|string|false|價格|
|source|query|string|false|下單來源|
|startDate|query|string|false|開始時間|
|systemOrderType|query|string|false|下單類型|

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

<h3 id="獲取訂單-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[OrdersDTO](#schemaordersdto)]|false|none|[訂單]|
|» OrdersDTO|[OrdersDTO](#schemaordersdto)|false|none|訂單|
|»» amount|string|false|none|委託數量|
|»» averagePrice|string|false|none|均價|
|»» brokerId|integer(int32)|false|none|業務方ID|
|»» createOn|integer(int64)|false|none|none|
|»» dealAmount|string|false|none|已成交數量|
|»» dealQuoteAmount|string|false|none|基準幣已成交數量|
|»» entrustPrice|string|false|none|用戶訂單委託價格|
|»» id|integer(int64)|false|none|none|
|»» notStrike|string|false|none|none|
|»» openAmount|string|false|none|none|
|»» pairCode|string|false|none|交易對|
|»» quoteAmount|string|false|none|基準幣數量|
|»» side|string|false|none|倉位類型，buy買，sell賣|
|»» sourceInfo|string|false|none|下單來源|
|»» status|integer(int32)|false|none|0:未成交 1:部分成交 2:完全成交 3:撤單中 -1:已撤單'|
|»» currency|string|false|none|幣種|
|»» systemOrderType|integer(int32)|false|none|10:限價 11:市價|
|»» trunOver|string|false|none|none|
|»» updateOn|integer(int64)|false|none|none|
|»» userId|integer(int64)|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## 批量下單

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

<h3 id="批量下單-parameters">Parameters</h3>

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

<h3 id="批量下單-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[OrdersDTO](#schemaordersdto)]|false|none|[訂單]|
|» OrdersDTO|[OrdersDTO](#schemaordersdto)|false|none|訂單|
|»» amount|string|false|none|委託數量|
|»» averagePrice|string|false|none|均價|
|»» brokerId|integer(int32)|false|none|業務方ID|
|»» createOn|integer(int64)|false|none|none|
|»» dealAmount|string|false|none|已成交數量|
|»» dealQuoteAmount|string|false|none|基準幣已成交數量|
|»» entrustPrice|string|false|none|用戶訂單委託價格|
|»» id|integer(int64)|false|none|none|
|»» notStrike|string|false|none|none|
|»» openAmount|string|false|none|none|
|»» pairCode|string|false|none|交易對|
|»» quoteAmount|string|false|none|基準幣數量|
|»» side|string|false|none|倉位類型，buy買，sell賣|
|»» sourceInfo|string|false|none|下單來源|
|»» status|integer(int32)|false|none|0:未成交 1:部分成交 2:完全成交 3:撤單中 -1:已撤單'|
|»» currency|string|false|none|幣種|
|»» systemOrderType|integer(int32)|false|none|10:限價 11:市價|
|»» trunOver|string|false|none|none|
|»» updateOn|integer(int64)|false|none|none|
|»» userId|integer(int64)|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## 撤銷指定交易對的全部訂單

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

<h3 id="撤銷指定交易對的全部訂單-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pairCode|path|string|true|pairCode|

<h3 id="撤銷指定交易對的全部訂單-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<aside class="success">
This operation does not require authentication
</aside>

## 批量撤銷指定交易對訂單

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

指定價格區間

<h3 id="批量撤銷指定交易對訂單-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|maxPrice|query|string|false|最高價|
|minPrice|query|string|false|最低價|
|pairCode|path|string|true|交易對|
|side|query|string|false|side|

<h3 id="批量撤銷指定交易對訂單-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<aside class="success">
This operation does not require authentication
</aside>

## 批量撤銷指定交易對下的訂單

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

<h3 id="批量撤銷指定交易對下的訂單-parameters">Parameters</h3>

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

<h3 id="批量撤銷指定交易對下的訂單-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<h3 id="批量撤銷指定交易對下的訂單-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» **additionalProperties**|[integer]|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## 獲取指定交易對下的完成訂單

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

可設置搜索條件

<h3 id="獲取指定交易對下的完成訂單-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|amount|query|string|false|數量|
|endDate|query|string|false|結束時間|
|isHistory|query|boolean|false|isHistory|
|page|query|integer(int32)|false|page|
|pageSize|query|integer(int32)|false|pageSize|
|pairCode|path|string|true|交易對|
|price|query|string|false|價格|
|source|query|string|false|下單來源|
|startDate|query|string|false|開始時間|
|systemOrderType|query|string|false|下單類型|

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

<h3 id="獲取指定交易對下的完成訂單-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="獲取指定交易對下的完成訂單-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[OrdersDTO](#schemaordersdto)]|false|none|[訂單]|
|» OrdersDTO|[OrdersDTO](#schemaordersdto)|false|none|訂單|
|»» amount|string|false|none|委託數量|
|»» averagePrice|string|false|none|均價|
|»» brokerId|integer(int32)|false|none|業務方ID|
|»» createOn|integer(int64)|false|none|none|
|»» dealAmount|string|false|none|已成交數量|
|»» dealQuoteAmount|string|false|none|基準幣已成交數量|
|»» entrustPrice|string|false|none|用戶訂單委託價格|
|»» id|integer(int64)|false|none|none|
|»» notStrike|string|false|none|none|
|»» openAmount|string|false|none|none|
|»» pairCode|string|false|none|交易對|
|»» quoteAmount|string|false|none|基準幣數量|
|»» side|string|false|none|倉位類型，buy買，sell賣|
|»» sourceInfo|string|false|none|下單來源|
|»» status|integer(int32)|false|none|0:未成交 1:部分成交 2:完全成交 3:撤單中 -1:已撤單'|
|»» currency|string|false|none|幣種|
|»» systemOrderType|integer(int32)|false|none|10:限價 11:市價|
|»» trunOver|string|false|none|none|
|»» updateOn|integer(int64)|false|none|none|
|»» userId|integer(int64)|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## 添加交易對訂單

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

<h3 id="添加交易對訂單-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pairCode|path|string|true|交易對|
|body|body|[OrdersParamDTO](#schemaordersparamdto)|true|orderParam|

> Example responses

> 200 Response

```json
118001244083232 //訂單號
```

<h3 id="添加交易對訂單-responses">Responses</h3>

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

## 批量撤銷指定交易對的訂單

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

<h3 id="批量撤銷指定交易對的訂單-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|pairCode|path|string|true|pairCode|
|body|body|array[integer]|true|ids|

<h3id="批量撤銷指定交易對的訂單-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<aside class="success">
This operation does not require authentication
</aside>

## 獲取指定交易對下指定訂單號的訂單

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

<h3 id="獲取指定交易對下指定訂單號的訂單-parameters">Parameters</h3>

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

<h3 id="獲取指定交易對下指定訂單號的訂單-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[OrdersDTO](#schemaordersdto)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<aside class="success">
This operation does not require authentication
</aside>

## 撤銷指定交易對下指定ID的訂單

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

<h3 id="撤銷指定交易對下指定id的訂單-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|string|true|用戶id|
|pairCode|path|string|true|交易對|

<h3 id="撤銷指定交易對下指定id的訂單-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|

<aside class="success">
This operation does not require authentication
</aside>

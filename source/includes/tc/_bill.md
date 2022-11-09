# 賬單相關接口

## 獲取賬單類型

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
    "code": "BUY",//買入
    "name": "",
    "id": 7
  },
  {
    "code": "SELL",//賣出
    "name": "",
    "id": 8
  }
]
```

<h3 id="獲取賬單類型-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="獲取賬單類型-responseschema">Response Schema</h3>

<aside class="success">
This operation does not require authentication
</aside>

## 獲取賬單信息

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

<h3 id="獲取賬單信息-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|endDate|query|string|false|結束時間|
|isHistory|query|string|false|是否查看歷史訂單|
|page|query|integer(int32)|false|page|
|pageSize|query|integer(int32)|false|pageSize|
|startDate|query|string|false|開始時間|
|currency|query|string|false|幣種|
|type|query|string|false|賬單類型|

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
      "currency": "string",
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

<h3 id="獲取賬單信息-responses">Responses</h3>

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|afterAssets|number|false|none|事後餘額|
|amount|number|false|none|變換金額  +增加 -減少|
|assets|number|false|none|餘額|
|beforeAssets|number|false|none|事前餘額|
|brokerId|integer(int32)|false|none|業務方ID|
|createOn|integer(int64)|false|none|none|
|fee|number|false|none|手續費|
|id|integer(int64)|false|none|none|
|makerTaker|string|false|none|成交類型|
|pairCode|string|false|none|交易對|
|price|number|false|none|成交價|
|referId|integer(int64)|false|none|關聯id|
|currency|string|false|none|幣種|
|tradeNo|string|false|none|訂單號|
|type|integer(int32)|false|none|賬單類型 1:充值 2:提現 3:由借款賬戶轉入 4:轉入借款賬戶 5:由放款賬戶轉入 6:轉入放款賬戶|
|updateOn|integer(int64)|false|none|none|
|userId|integer(int64)|false|none|none|



<aside class="success">
This operation does not require authentication
</aside>

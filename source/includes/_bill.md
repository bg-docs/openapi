# 账单相关接口

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
|isHistory|query|string|false|Y否查看历史订单|
|page|query|integer(int32)|false|page|
|pageSize|query|integer(int32)|false|pageSize|
|startDate|query|string|false|开始时间|
|currency|query|string|false|币种|
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
|currency|string|false|none|币种|
|tradeNo|string|false|none|订单号|
|type|integer(int32)|false|none|账单类型 1:充值 2:提现 3:由借款账户转入 4:转入借款账户 5:由放款账户转入 6:转入放款账户|
|updateOn|integer(int64)|false|none|none|
|userId|integer(int64)|false|none|none|



<aside class="success">
This operation does not require authentication
</aside>

# 用戶資產相關接口

用戶資產相關接口

## 獲取資產信息

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

獲取所有的資產信息

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
    "currency": "string",
    "transfer": true,
    "userId": 0,
    "withdrawLimit": 0
  }
]
```


<h3 id="獲取資產信息-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="獲取資產信息-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[UserAssetsDTO](#schemauserassetsdto)]|false|none|[交易資產]|
|» UserAssetsDTO|[UserAssetsDTO](#schemauserassetsdto)|false|none|交易資產|
|»» available|number|false|none|餘額|
|»» baseBTC|number|false|none|none|
|»» brokerId|integer(int32)|false|none|業務方ID|
|»» hold|number|false|none|凍結|
|»» sort|integer(int32)|false|none|none|
|»» currency|string|false|none|幣種|
|»» transfer|boolean|false|none|none|
|»» userId|integer(int64)|false|none|none|
|»» withdrawLimit|number|false|none|提幣限額|

<aside class="success">
This operation does not require authentication
</aside>

## 獲取幣種下資產信息

<a id="opIdgetUserCurrencyAssetUsingGET"></a>

> Code samples

```java
URL obj = new URL("/example.com/openapi/exchange/{currency}/assets");
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
GET /example.com/openapi/exchange/{currency}/assets HTTP/1.1

Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json'
};

fetch('/example.com/openapi/exchange/{currency}/assets',
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

`GET /openapi/exchange/{currency}/assets`

獲取幣種下的資產信息

<h3 id="獲取幣種下資產信息-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|currency|path|string|true|幣種|

> Example responses

> 200 Response

```json
{
  "available": 0, 
  "baseBTC": 0,
  "brokerId": 0,
  "hold": 0,
  "sort": 0,
  "currency": "string",
  "transfer": true,
  "userId": 0,
  "withdrawLimit": 0
}
```

<h3 id="獲取幣種下資產信息-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[UserAssetsDTO](#schemauserassetsdto)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|Unauthorized|None|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|Forbidden|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None|

<h3 id="獲取資產信息-responseschema">Response Schema</h3>
Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[UserAssetsDTO](#schemauserassetsdto)]|false|none|[交易資產]|
|» UserAssetsDTO|[UserAssetsDTO](#schemauserassetsdto)|false|none|交易資產|
|»» available|number|false|none|餘額|
|»» baseBTC|number|false|none|none|
|»» brokerId|integer(int32)|false|none|業務方ID|
|»» hold|number|false|none|凍結|
|»» sort|integer(int32)|false|none|none|
|»» currency|string|false|none|幣種|
|»» transfer|boolean|false|none|none|
|»» userId|integer(int64)|false|none|none|
|»» withdrawLimit|number|false|none|提幣限額|

<aside class="success">
This operation does not require authentication
</aside>

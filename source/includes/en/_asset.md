# 用户资产相关接口

用户资产相关接口

## 获取资产信息

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
    "currency": "string",
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
|»» currency|string|false|none|币种|
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

获取币种下的资产信息

<h3 id="获取币种下资产信息-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|currency|path|string|true|币种|

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
|»» currency|string|false|none|币种|
|»» transfer|boolean|false|none|none|
|»» userId|integer(int64)|false|none|none|
|»» withdrawLimit|number|false|none|提币限额|

<aside class="success">
This operation does not require authentication
</aside>

# Authentication information

<a id="auth"></a>

Each user can create up to 50 APIKeys;

Do not disclose your APIKey to anyone else to avoid loss of assets. It is recommended to bind the APIKey to an IP address for better security of your account. Multiple IP addresses are separated in English, and a maximum of 10 IP addresses are supported. API not bound to an IP address is only valid for 180 days;

Please note that binding an APIKey to a third-party platform may pose security risks that you should act with caution;

To access the private information interface, the following request headers will have to be added


Header Name | Meaning
---------- | -------
ACCESS-KEY | API KEY created by the user on the BGE platform
ACCESS-SIGN | Signature for the request, which is generated based on the user-created API KEY to authenticate the request’s legitimacy  [ACCESS-SING generation algorithm](#access-sign-gen)
ACCESS-TIMESTAMP | Request time, usually the current timestamp Example:`2022-01-08T07:19:56.339Z`,or a millisecond timestamp

<a name="access-sign-gen">ACCESS-SING generation algorithm</a>

<aside> 
Generate signatures using OpenAPiUtils.createSign
</aside>

`requestPath`: Consistent with the path in the documentation, e.g. `/v1/products`

`queryString`: List of request parameters. Note: Parameters needs to be orderly arranged. See [remarks](#sign_query_warning)

`params`: When the request is `GET` or `DELETE` or WEBSOCKET channel for authentication, fill in ""

| Parameter Name|Parameter Type|Description| 
|----|----|----|
|method|string| GET or POST or DELETE；"" when calculating ws sign|
|secretKey|string| API KEY name created by the user on BGE|
|requestPath|string| Request path; "" for ws sign calculation|
|queryString|string| Request parameter; "" for ws sign calculation|
|params|string| Transfer data content; "" for ws sign calculation|
|timestamp|string| Current timestamp e.g.`2022-01-08T07:19:56.339Z`,or millisecond timestamp |

> Sign http request

```java
  String timestamp=OpenAPiUtils.createTimestamp();
  String sign=OpenAPiUtils.createSign(OpenAPiUtils.POST,
  "43767b4dec6e78e07c81f89af47018dc3ab57585721bf57a389f7637a9d0506b",
  "/v1/accounts",
  "",
  s,timestamp);
```

> Sign web socket request

```java
  String timestamp=OpenAPiUtils.createTimestamp();
  String sign=OpenAPiUtils.createSign("","43767b4dec6e78e07c81f89af47018dc3ab57585721bf57a389f7637a9d0506b","","","",timestamp);
```



> Generation algorithm tool class

```java
import org.apache.commons.codec.binary.Base64;
import org.apache.commons.codec.digest.HmacUtils;
  
public class OpenAPiUtils {
  public static final String GET = "GET";
  public static final String POST = "POST";
  public static final String DELETE = "DELETE";
  public static final Gson gson = new Gson();

  public static String createTimestamp() {
    return Instant.now().toString();
  }

  /**
   * 获取当前时间戳 例：2022-01-08T07:19:56.339Z
   * @return
   */
  public static String createTimestamp() {
    return Instant.now().toString();
  }

  /**
   * sign
   * @param method POST or GET or DELETE
   * @param secretKey for example：HKBGE-xxxxx
   * @param requestPath for example：/v1/orders
   * @param queryString Request parameters
   * @param body string empty when method is `GET`
   * @param timestamp  for example：2022-01-08T07:19:56.339Z
   * @return string
   */
  public static String createSign(String method, String secretKey, String requestPath, String queryString, String body, String timestamp) {
    String sign = "";
    method = method.toUpperCase();
    if (timestamp == null) {
      timestamp = Instant.now().toString();
    }
    if (method.equals("POST")) {
      sign = generate(timestamp, method, requestPath, queryString, body, secretKey, "HmacSHA256");
    }
    if (method.equals("GET") || method.equals("DELETE")) {
      sign = generate(timestamp, method, requestPath, queryString, "", secretKey, "HmacSHA256");
    }
    if ("".equalsIgnoreCase(method)) {
      sign = generate(timestamp, method, requestPath, queryString, "", secretKey, "HmacSHA256");
    }
    return sign;
  }

  public static String generate(final String timestamp, String method, final String requestPath,
                                String queryString, String body, final String secret, final String alg) {
    body = StringUtils.defaultIfBlank(body, StringUtils.EMPTY);
    queryString = StringUtils.isEmpty(queryString) ? "" : "?" + queryString;
    final String preHash = timestamp + method + requestPath + queryString + body;
    return encodeBase64(alg, secret, preHash);
  }

  public static String encodeBase64(final String alg, final String secret, final String data) {
    Validate.notNull(alg, "SignatureAlgorithm cannot be null.");
    Validate.notNull(data, "Signing Secret cannot be null.");
    switch (alg) {
      case "HmacMD5":
        return Base64.encodeBase64String(new HmacUtils("HmacMD5", secret).hmac(data));
      case "HmacSHA1":
        return Base64.encodeBase64String(new HmacUtils("HmacSHA1", secret).hmac(data));
      case "HmacSHA224":
        return Base64.encodeBase64String(new HmacUtils("HmacSHA224", secret).hmac(data));
      case "HmacSHA256":
        try {
          return Base64.encodeBase64String(new HmacUtils("HmacSHA256",
            secret.getBytes("UTF-8")).hmac(data.getBytes("UTF-8")));
        } catch (UnsupportedEncodingException e) {
          throw new RuntimeException(e.getMessage());
        }
      case "HmacSHA384":
        return Base64.encodeBase64String(new HmacUtils("HmacSHA384", secret).hmac(data));
      case "HmacSHA512":
        return Base64.encodeBase64String(new HmacUtils("HmacSHA512", secret).hmac(data));
      default:
        throw new IllegalArgumentException("The '" + alg.name() + "' algorithm cannot be used for signing.");
    }
  }

}
```
<aside class="warning">
Remarks
</aside>
<a name="sign_query_warning"></a>

When calculating data signatures, the parameters must be transmitted in the same order as the signature string, and the queryString must not start with “?” or end with “&” to avoid authentication failure. For example: 
when calculating the signature for `GET "http://api.bg.exchange/hk/v1/demo?a=2&b=3"`

- Correct: preHash = ... + "a=2&b=3" + ...;
- Incorrect: preHash = ... + "b=3&a=2" + ...;
- Incorrect: preHash = ... + "?b=3&a=2" + ...;
- Incorrect: preHash = ... + "b=3&a=2&" + ...;





<aside> 
Fill in the HTTP HEADERS in requests
</aside>

Add the api key, sign and timestamp generated by the user on BGE to the http request header.

> Fill in the HTTP HEADERS in requests

```java
RequestBuilders.post("/openapi/exchange/BTC_USDT/orders")
                        .header("ACCESS-KEY", "HKBGE-6fc437d24902cce8635806b6d79921f2")
                        .header("ACCESS-SIGN", sign)
                        .header("ACCESS-TIMESTAMP", timestamp)
                        .characterEncoding("UTF-8")
                        .content(s.getBytes(StandardCharsets.UTF_8))
                        .contentType(MediaType.APPLICATION_JSON_VALUE)
```

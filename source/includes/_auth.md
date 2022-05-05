# 鉴权信息

<a id="auth"></a>

每个用户最多可以创建50个APIKey；

请勿将您的APIKey透露给任何人，以免造成资产损失。建议为APIKey绑定IP地址，以提高您账户的安全性，多个IP地址用英文分割,最多支持10个IP地址,未绑定IP地址的API有效期只有180天；

请注意，将APIKey绑定在第三方平台，可能有安全隐患，请您谨慎操作；

访问私有信息接口，需要在加入如下请求头

Header Name | Meaning
---------- | -------
ACCESS-KEY | 用户在BGE平台创建的API KEY
ACCESS-SIGN | 根据用户创建的API KEY 对请求所作出的签名信息，以验证请求的合法性 [ACCESS-SING生成算法](#access-sign-gen)
ACCESS-TIMESTAMP | 请求时间，一般为当前时间戳 例：`2022-01-08T07:19:56.339Z`,或毫秒时间戳

<a name="access-sign-gen">ACCESS-SING生成算法</a>

<aside> 
使用OpenAPiUtils.createSign 生成 sign 
</aside>

`requestPath`: 与文档中给出的路径相一致,例如 `/v1/products`

`queryString`: 请求参数列表，注：参数顺序需要保持有序。见 [备注](#sign_query_warning)

`params`: 当请求为 `GET` 或者 `DELETE` 或者为WEBSOCKET channel 进行认证时，填 ""

| 参数名|参数类型|说明| 
|----|----|----|
|method|string| GET or POST or DELETE；计算ws sign时为""|
|secretKey|string| 用户在BGE创建的API KEY名称|
|requestPath|string| 请求路径 ；计算ws sign时为""|
|queryString|string| 请求参数 ；计算ws sign时为""|
|params|string| 传输数据内容 ；计算ws sign时为""|
|timestamp|string| 当前时间戳 例：`2022-01-08T07:19:56.339Z`,或毫秒时间戳 |

> 签名计算与使用

```java

public class AuthDemo {
  /**
   * 获取当前时间戳 例：2022-01-08T07:19:56.339Z
   *
   * @return
   */
  public static String createTimestamp() {
    return Instant.now().toString();
  }

  /**
   * 计算签名
   *
   * @param method      POST or GET or DELETE
   * @param secretKey   例：HKBGE-xxxxx
   * @param requestPath 例：/v1/orders
   * @param queryString 请求参数
   * @param body        string GET时为空
   * @param timestamp   当前时间戳 例：2022-01-08T07:19:56.339Z
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

  public static void main(String[] args) {
    // restapi 
    String timestamp = createTimestamp();
    String sign = createSign("POST", "43767b4dec6e78e07c81f89af47018dc3ab57585721bf57a389f7637a9d0506b", "/v1/accounts", "", s, timestamp);
    // 填充HTTP HEADERS
    RequestBuilders.post("/openapi/exchange/BTC_USDT/orders")
      .header("ACCESS-KEY", "HKBGE-6fc437d24902cce8635806b6d79921f2")
      .header("ACCESS-SIGN", sign)
      .header("ACCESS-TIMESTAMP", timestamp)
                ...

    // 如果使用 websocket，method，requestPath, queryString, body 均需要为空
    // String sign = createSign("", "43767b4dec6e78e07c81f89af47018dc3ab57585721bf57a389f7637a9d0506b", "", "", "", timestamp);

  }
}

```

```php
// 当前时间
$timestamp = gmdate("Y-m-d\TH:i:s\Z");
// 请求方法
$method = strtoupper("post");
$secret_key="YOUR_SECRET_KEY";
// 例子：https://api.hkbge-inc.com/v1/fills?order_id=11698140999351 
// requestPath:  "/v1/fills" 
// param_string: "?order_id=11698140999351" 
$requestPath = "/v1/fills";
$param_string="?order_id=11698140999351";
// 没有body 写 ""
$body="{\"pageSize\": 2,\"pageIndex\": 1}";
$preHash = utf8_encode($timestamp.$method.$requestPath.$param_string.$body);
$signature = hash_hmac('sha256', $preHash, $secret_key,true);
$signature = base64_encode($signature);
echo $signature;

// header:
// ACCESS-KEY: $secret_key
// ACCESS-SIGN: $signature
// ACCESS-TIMESTAMP: $timestamp
```

<aside class="warning">
备注
</aside>
<a name="sign_query_warning"></a>

计算数据签名时，参数的传递顺序需要与签名串顺序一致，且queryString不以`?`开头，不以`&`结尾  否则鉴权失败。例如：给 `GET "http://api.bg.exchange/hk/v1/demo?a=2&b=3"`
计算签名时，

- 正确使用: preHash = ... + "a=2&b=3" + ...;

- 错误使用: preHash = ... + "b=3&a=2" + ...;

- 错误使用: preHash = ... + "?b=3&a=2" + ...;

- 错误使用: preHash = ... + "b=3&a=2&" + ...;




<aside> 
请求时填充HTTP HEADERS
</aside>

将用户在BGE生成的api key 与 sign 与 时间戳加入到 http请求头中。

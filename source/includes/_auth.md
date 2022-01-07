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
ACCESS-TIMESTAMP | 请求时间，一般为当前的好描述

<a name="access-sign-gen">ACCESS-SING生成算法</a>

<aside> 
使用OpenAPiUtils.createSign 生成 sign 
</aside>

`requestPath`: 与文档中给出的路径相一致

`params`: 当请求为 <fout class="httpget>GET</font> 或者 <fout class="httpdelete>DELETE</font> 或者为WEBSOCKETchannel 进行认证时，填 ""

| 参数名|参数类型|说明| 
|----|----|----|
|method|string| GET or POST or DELETE|
|secretKey|string| 用户在BGE创建的API KEY名称|
|requestPath|string| 请求路径 |
|params|string| 传输数据内容 |
|timestamp|string| 当前的毫秒数时间戳 |

> 计算sign 

```java
  String timestamp=OpenAPiUtils.createTimestamp();
  String sign=OpenAPiUtils.createSign(OpenAPiUtils.POST,
  "HKBGE-97759b085d7cabd66fea599aeece95f9",
  "/openapi/exchange/BTC_USDT/orders",
  s,timestamp);
```

> sign 生成算法工具类

```java
public class OpenAPiUtils {
  public static final String GET = "GET";
  public static final String POST = "POST";
  public static final String DELETE = "DELETE";
  public static final Gson gson = new Gson();

  public static String createTimestamp() {
    return Instant.now().toString();
  }

  public static String createSign(String method, String secretKey, String requestPath, String params, String timestamp) {
    String sign = "";
    method = method.toUpperCase();
    if (timestamp == null) {
      timestamp = Instant.now().toString();
    }
    if (method.equals("POST")) {
      final String preHash = timestamp + method + requestPath + params;

      sign = generate(timestamp, method, requestPath, null, params, secretKey, HmacAlgorithmEnum.HMAC_SHA_256);
    }
    if (method.equals("GET") || method.equals("DELETE")) {
      if (params != null) {
        String queryString = "";
        Map<String, Object> jsonObject = GsonUtils.parseMap(params);
        requestPath += "?";
        for (final Map.Entry<String, Object> entry : jsonObject.entrySet()) {
          queryString += entry.getKey() + "=" + entry.getValue() + "&";
        }
        queryString = queryString.substring(0, queryString.length() - 1);
        requestPath += queryString;

      }
      final String preHash = timestamp + method + requestPath;
      sign = generate(timestamp, method, requestPath, null, null, secretKey, HmacAlgorithmEnum.HMAC_SHA_256);
    }

    return sign;

  }

  public static String generate(final String timestamp, String method, final String requestPath,
                                String queryString, String body, final String secret, final HmacAlgorithmEnum alg) {
    body = StringUtils.defaultIfBlank(body, StringUtils.EMPTY);
    queryString = StringUtils.isEmpty(queryString) ? "" : "?" + queryString;
    final String preHash = timestamp + method + requestPath + queryString + body;
    return encodeBase64(alg, secret, preHash);
  }

  public static String encodeBase64(final HmacAlgorithmEnum alg, final String secret, final String data) {
    Validate.notNull(alg, "SignatureAlgorithm cannot be null.");
    Validate.notNull(data, "Signing Secret cannot be null.");
    switch (alg) {
      case HMAC_MD5:
        return Base64.encodeBase64String(new HmacUtils(HmacAlgorithms.HMAC_MD5, secret).hmac(data));
      case HMAC_SHA_1:
        return Base64.encodeBase64String(new HmacUtils(HmacAlgorithms.HMAC_SHA_1, secret).hmac(data));
      case HMAC_SHA_224:
        return Base64.encodeBase64String(new HmacUtils(HmacAlgorithms.HMAC_SHA_224, secret).hmac(data));
      case HMAC_SHA_256:
        try {
          return Base64.encodeBase64String(new HmacUtils(HmacAlgorithms.HMAC_SHA_256,
            secret.getBytes("UTF-8")).hmac(data.getBytes("UTF-8")));
        } catch (UnsupportedEncodingException e) {
          throw new RuntimeException(e.getMessage());
        }
      case HMAC_SHA_384:
        return Base64.encodeBase64String(new HmacUtils(HmacAlgorithms.HMAC_SHA_384, secret).hmac(data));
      case HMAC_SHA_512:
        return Base64.encodeBase64String(new HmacUtils(HmacAlgorithms.HMAC_SHA_512, secret).hmac(data));
      default:
        throw new IllegalArgumentException("The '" + alg.name() + "' algorithm cannot be used for signing.");
    }
  }

}
```

<aside> 
请求时填充HTTP HEADERS
</aside>

将用户在BGE生成的api key 与 sign 与 时间戳加入到 http请求头中。

> 填充HTTP HEADERS

```java
RequestBuilders.post("/openapi/exchange/BTC_USDT/orders")
                        .header("ACCESS-KEY", "HKBGE-6fc437d24902cce8635806b6d79921f2")
                        .header("ACCESS-SIGN", sign)
                        .header("ACCESS-TIMESTAMP", timestamp)
                        .characterEncoding("UTF-8")
                        .content(s.getBytes(StandardCharsets.UTF_8))
                        .contentType(MediaType.APPLICATION_JSON_VALUE)
```

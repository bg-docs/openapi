# 鑑權信息

<a id="auth"></a>

每個用戶最多可以創建50個APIKey；

請勿將您的APIKey透露給任何人，以免造成資產損失。建議為APIKey綁定IP地址，以提高您賬戶的安全性，多個IP地址用英文分割,最多支持10個IP地址,未綁定IP地址的API有效期只有180天；

請注意，將APIKey綁定在第三方平台，可能有安全隱患，請您謹慎操作；

訪問私有信息接口，需要在加入如下請求頭

Header Name | Meaning
---------- | -------
ACCESS-KEY | 用戶在BGE平台創建的API KEY
ACCESS-SIGN | 根據用戶創建的API KEY 對請求所作出的簽名信息，以驗證請求的合法性 [ACCESS-SING生成算法](#access-sign-gen)
ACCESS-TIMESTAMP | 請求時間，一般為當前時間戳 例：`2022-01-08T07:19:56.339Z`,或毫秒時間戳

<a name="access-sign-gen">ACCESS-SING生成算法</a>

<aside> 
使用OpenAPiUtils.createSign 生成 sign 
</aside>

`requestPath`: 與文檔中給出的路徑相一致,例如 `/v1/products`

`queryString`: 請求參數列表，注：參數順序需要保持有序。見 [備註](#sign_query_warning)

`params`: 當請求為 `GET` 或者 `DELETE` 或者為WEBSOCKET channel 進行認證時，填 ""

| 參數名|參數類型|說明| 
|----|----|----|
|method|string| GET or POST or DELETE；計算ws sign時為""|
|secretKey|string| 用戶在BGE創建的API KEY名稱|
|requestPath|string| 請求路徑 ；計算ws sign時為""|
|queryString|string| 請求參數 ；計算ws sign時為""|
|params|string| 傳輸數據內容 ；計算ws sign時為""|
|timestamp|string| 當前時間戳 例：`2022-01-08T07:19:56.339Z`,或毫秒時間戳 |

> 計算http請求 sign

```java
  String timestamp=OpenAPiUtils.createTimestamp();
  String sign=OpenAPiUtils.createSign(OpenAPiUtils.POST,
  "43767b4dec6e78e07c81f89af47018dc3ab57585721bf57a389f7637a9d0506b",
  "/v1/accounts",
  "",
  s,timestamp);
```

> 計算web socket 請求 sign

```java
  String timestamp=OpenAPiUtils.createTimestamp();
  String sign=OpenAPiUtils.createSign("","43767b4dec6e78e07c81f89af47018dc3ab57585721bf57a389f7637a9d0506b","","","",timestamp);
```



> sign 生成算法工具類

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
   * 獲取當前時間戳 例：2022-01-08T07:19:56.339Z
   * @return
   */
  public static String createTimestamp() {
    return Instant.now().toString();
  }

  /**
   * 計算簽名
   * @param method POST or GET or DELETE
   * @param secretKey 例：HKBGE-xxxxx
   * @param requestPath 例：/v1/orders
   * @param queryString 請求參數
   * @param body string GET時為空
   * @param timestamp 當前時間戳 例：2022-01-08T07:19:56.339Z
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
備註
</aside>
<a name="sign_query_warning"></a>

計算數據簽名時，參數的傳遞順序需要與簽名串順序一致，且queryString不以`?`開頭，不以`&`結尾  否則鑑權失敗。例如：給 `GET "http://api.bg.exchange/hk/v1/demo?a=2&b=3"`
計算簽名時，

- 正確使用: preHash = ... + "a=2&b=3" + ...;

- 錯誤使用: preHash = ... + "b=3&a=2" + ...;

- 錯誤使用: preHash = ... + "?b=3&a=2" + ...;

- 錯誤使用: preHash = ... + "b=3&a=2&" + ...;




<aside> 
請求時填充HTTP HEADERS
</aside>

將用戶在BGE生成的api key 與 sign 與 時間戳加入到 http請求頭中。

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

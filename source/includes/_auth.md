# 鉴权信息
<a id="auth"></a>

访问私有信息接口，需要在加入如下请求头

Header Name | Meaning
---------- | -------
ACCESS-KEY | Bad Request -- Your request is invalid.
ACCESS-SIGN | Unauthorized -- Your API key is wrong.
ACCESS-TIMESTAMP | Forbidden -- The kitten requested is hidden for administrators only.


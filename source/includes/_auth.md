# 鉴权信息
<a id="auth"></a>

访问私有信息接口，需要在加入如下请求头

Header Name | Meaning
---------- | -------
ACCESS-KEY | Bad Request -- Your request is invalid.
ACCESS-SIGN | Unauthorized -- Your API key is wrong.
ACCESS-TIMESTAMP | Forbidden -- The kitten requested is hidden for administrators only.

每个用户最多可以创建50个APIKey；

请勿将您的APIKey透露给任何人，以免造成资产损失。建议为APIKey绑定IP地址，以提高您账户的安全性，多个IP地址用英文分割,最多支持10个IP地址,未绑定IP地址的API有效期只有180天；

请注意，将APIKey绑定在第三方平台，可能有安全隐患，请您谨慎操作；

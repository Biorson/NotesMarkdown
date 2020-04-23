# 公众号服务

名词解释：

OpenID:

```mark
加密后的微信号，每个用户对每个公众号的OpenID是唯一的
```

[OpenID参考文档](https://developers.weixin.qq.com/doc/offiaccount/User_Management/Getting_a_User_List.html)

UnionID:

```markdown
只要是同一个微信开放平台帐号下的移动应用、网站应用和公众帐号（包括小程序），用户的 UnionID 是唯一的
```

[UuionID参考文档](https://developers.weixin.qq.com/minigame/dev/guide/open-ability/union-id.html)

Access token:

```markdown
access_token是公众号的全局唯一接口调用凭据，公众号调用各接口时都需使用access_token。开发者需要进行妥善保存。access_token的存储至少要保留512个字符空间。access_token的有效期目前为2个小时，需定时刷新，重复获取将导致上次获取的access_token失效。
```

[access_token文档](https://developers.weixin.qq.com/doc/offiaccount/Basic_Information/Get_access_token.html)



## 账号体系

### 1.建立开发者账号、多应用体系、多业务系统关系维护

每个业务系统可能存在多公众号、多小程序

每个开发者账号可以绑定多个应用（公众号、小程序等）；

每个公众号/小程序都有对应的一组appid和secret

### 2.缓存access_token

每组appid+secret都可以获取access_token

同组appid+secret不同时间段获取的access_token也不一样

公众平台所有接口的调用需要先获取access_token，access_token在2小时内有效，过期需要重新获取，但1天内获取次数有限，开发者需自行存储

有效期内，刷新access_token，在刷新后的5分钟内，新老access_token都可以继续使用，保证业务平滑过渡

## 消息管理

### 1.模板消息模块


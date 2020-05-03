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

[UuionID参考文档](https://developers.weixin.qq.com/doc/offiaccount/User_Management/Get_users_basic_information_UnionID.html#UinonId)

Access token:

```markdown
access_token是公众号的全局唯一接口调用凭据，公众号调用各接口时都需使用access_token。开发者需要进行妥善保存。access_token的存储至少要保留512个字符空间。access_token的有效期目前为2个小时，需定时刷新，重复获取将导致上次获取的access_token失效。
```

[access_token文档](https://developers.weixin.qq.com/doc/offiaccount/Basic_Information/Get_access_token.html)



## 用户与公众号体系

### 1.建立开发者账号、多应用体系、多业务系统关系维护

每个业务系统可能存在多公众号、多小程序

每个开发者账号可以绑定多个应用（公众号、小程序等）；

每个公众号/小程序都有对应的一组appid和secret

### 2.缓存access_token

每组appid+secret都可以获取access_token

同组appid+secret每次获取的access_token也不一样

公众平台所有接口的调用需要先获取access_token，access_token在2小时内有效，过期需要重新获取，但1天内获取次数有限，开发者需自行存储

有效期内，刷新access_token，在刷新后的5分钟内，新老access_token都可以继续使用，保证业务平滑过渡

### 3.用户、公众号、openid、unionid关系维护

每个用户对每个公众号的OpenID是唯一的

同一个微信开放平台帐号下的移动应用、网站应用和公众帐号（包括小程序），用户的 UnionID 是唯一的

一个用户跟一个开发者账号是一对一关系（一个用户对应一个unionid）

一个用户对同一开发者账号下的公众号是一对多的关系（一个用户对应多个openid）

用户的openid,只能通过微信接口（轮询）拉取

用户的unionid,也是需要通过接口获取（依赖openid参数）

## 消息管理

### 1.模板消息模块

[开发参考](https://developers.weixin.qq.com/doc/offiaccount/Message_Management/Template_Message_Interface.html#6)

新增消息模板：微信暂无接口提供，需登录公众号平台手动增加，然后审核

获取模板列表：有接口提供

删除模板：有接口提供

发送模板消息：有接口提供

事件推送：模版消息发送任务完成后，微信服务器会将是否送达成功作为通知，发送到开发者中心中填写的服务器配置地址，存在三种情况：送达成功、送达由于用户拒收（用户设置拒绝接收公众号消息）而失败、送达由于其他原因失败；可用于记录模板消息发送记录




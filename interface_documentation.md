## 1.  图书馆系统接口
### 1. 用户登录
* 基本信息
> 请求路径 ：/login
> 请求方式 ：POST
> 接口描述 ：用于已注册的用户登录 

* 请求参数
| 参数名 | 类型 | 是否必须 | 备注 |
| ---- | ---- | ---- | ----|
| username| string |  是 | 用户名 |
| password | string | 是 | 用户密码 |

参数说明：
以上参数均放置于header中上传

* 响应参数
| 名称 | 类型 | 备注 |
| ---- | ---- | ---- |
| code | number | 响应码 1为成功 2为失败|
| msg | string | 返回提示信息|
| token | string | 后续验证身份均使用token|

* 响应数据样例
``` json
{
	"code" : 1,
	"msg" : 成功,
	"token" : hdkasjfhkjhkjshsadfkjhfiuyhioyhkfda4217897fhdcjskadasfhcjkl;sdajhnhfkljhdslkahjncloiuhkljpsdqapydrtrft98237ru4hjxslkahc984237ryfhnd333
}
```


### 2.用户注册
* 基本信息
> 请求路径 ：/register
> 请求方式 ：POST
> 接口描述 ：用于注册用户信息

* 请求参数
| 参数名 | 类型 | 是否必须 | 备注 |
| ---- | ---- | ---- | ----|
| username | string |  是 | 用户名 |
| password | string | 是 | 用户密码 |
| studentid | string | 是 | 学号 |

参数说明：
以上参数均放置于header中上传

* 响应参数
| 名称 | 类型 | 备注 |
| ---- | ---- | ---- |
| code | number | 响应码 1为成功 2为失败|
| msg | string | 返回提示信息|

* 响应数据样例
``` json
{
	"code" : 1,
	"msg" : 成功,
}
```

### 3.增加书籍
* 基本信息
> 请求路径 ：/book/add
> 请求方式 ：GET
> 接口描述 ：用于添加书籍

* 请求参数
| 参数名 | 类型 | 是否必须 | 备注 |
| ---- | ---- | ---- | ----|
| token | string |  是 |  |
| name | string | 是 | 书名 |
| sum | string | 是 | 添加书目数量 |
| type | string | 是 | 类别 |
| writer | string | 否 | 作者 |
| date | date | 否 | 出版日期 |

请求样例
GET http://xxx/book/add/?token=xxx&name=高等数学&sun=3&type=数学&writer=高斯


* 相应参数
| 名称 | 类型 | 备注 |
| ---- | ---- | ---- |
| code | number | 响应码 0为无权限 1为成功 2为失败|
| msg | string | 返回提示信息|

* 响应数据样例
``` json
{
	"code" : 2,
	"msg" : 失败,
}
```

### 4. 删除书籍
* 基本信息
> 请求路径 ：/book/add
> 请求方式 ：GET
> 接口描述 ：用于添加书籍

* 请求参数
| 参数名 | 类型 | 是否必须 | 备注 |
| ---- | ---- | ---- | ----|
| token | string |  是 |  |
| bookid | string | 是 | 书籍编号 |

请求样例
GET http://xxx/book/add/?token=xxx&bookid=114514


* 相应参数
| 名称 | 类型 | 备注 |
| ---- | ---- | ---- |
| code | number | 响应码 0为无权限 1为成功 2为失败|
| msg | string | 返回提示信息|

* 响应数据样例
``` json
{
	"code" : 0,
	"msg" : 无权限,
}
```


## 1.  图书馆系统接口
### 1. 用户登录
* 基本信息
> 请求路径 ：/user/login
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
> 请求路径 ：/user/register
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
> 请求方式 ：PUT
> 接口描述 ：用于添加书籍

* 请求参数
| 参数名 | 类型 | 是否必须 | 备注 |
| ---- | ---- | ---- | ----|
| token | string |  是 |  |
| name | string | 是 | 书名 |
| type | string | 是 | 类别 |
| writer | string | 否 | 作者 |
| date | date | 否 | 出版日期 |

参数说明：
以上参数均放置于header中上传


* 响应参数
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
> 请求路径 ：/book/delete
> 请求方式 ：PUT
> 接口描述 ：用于删除书籍

* 请求参数
| 参数名 | 类型 | 是否必须 | 备注 |
| ---- | ---- | ---- | ----|
| token | string |  是 |  |
| bookid | Integer | 是 | 书籍编号 |

参数说明：
以上参数均放置于header中上传


* 响应参数
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

### 5. 查询书籍
* 基本信息
> 请求路径 ：/book/find
> 请求方式 ：GET
> 接口描述 ：用于查询书籍

* 请求参数
| 参数名 | 类型 | 是否必须 | 备注 |
| ---- | ---- | ---- | ----|
| token | string |  是 |  |
| name | string | 否 | 书籍名称 |
| typename | string | 否 | 类型名称 | 
| press | string | 否 | 出版社名称 |

//注 三者均可为空，但不能全空
请求参数举例: http://http://112.124.10.96/book/find?token=xxx&name=高等代数&press=哈维出版社


* 响应参数
| 名称 | 类型 | 备注 |
| ---- | ---- | ---- |
| code | number | 响应码 0为无权限 1为成功 2为失败|
| msg | string | 返回提示信息|
| data | List | 书籍信息列表|

* data返回值
| 名称 | 类型 | 备注 |
| ---- | ---- | ---- |
| bookName | string | 书名 |
| bookId | Integer | 书籍编号 |
| bookAuthor | string | 作者 |
| bookPress | string | 出版社 |
| type | string | 类型 |
| bookPublicationDate | date | 出版时间 |
| alive | Integer | 是否在馆: 0为不在，1为在 |


* 响应数据样例
``` json
{
	"code" : 1,
	"msg" : 成功,
	"data" : [["bookName" : "高等代数","type" : "数学","bookAuthor" : "张华"......],["bookName" : "高等代数","type" : "数学","bookAuthor" : "张华"......]......]
}
```

### 6. 修改书籍
* 基本信息
> 请求路径 ：/book/change
> 请求方式 ：PUT
> 接口描述 ：用于修改书籍信息

* 请求参数
| 参数名 | 类型 | 是否必须 | 备注 |
| ---- | ---- | ---- | ----|
| token | string |  是 |  |
| bookid | Integer | 是 | 书籍编号 |
| name | string | 否 | 书名 |
| type | string | 否 | 类别 |
| writer | string | 否 | 作者 |
| date | date | 否 | 出版日期 |

参数说明：
以上参数均放置于header中上传
//注 若添加参数则更改该参数信息


* 响应参数
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

### 7.增加图书类别
* 基本信息
> 请求路径 ：/book/addtype
> 请求方式 ：POST
> 接口描述 ：用于添加图书类别

* 请求参数
| 参数名 | 类型 | 是否必须 | 备注 |
| ---- | ---- | ---- | ----|
| token | string |  是 |  |
| typename | string | 是 | 类别名称 |

参数说明：
以上参数均放置于header中上传


* 响应参数
| 名称 | 类型 | 备注 |
| ---- | ---- | ---- |
| code | number | 响应码 0为无权限 1为成功 2为失败|
| msg | string | 返回提示信息|

* 响应数据样例
``` json
{
	"code" : 1,
	"msg" : 成功,
}
```

### 8. 修改书籍类别
* 基本信息
> 请求路径 ：/book/changetype
> 请求方式 ：PUT
> 接口描述 ：用于修改书籍类别信息

* 请求参数
| 参数名 | 类型 | 是否必须 | 备注 |
| ---- | ---- | ---- | ----|
| token | string |  是 |  |
| oldtypename | string | 是 | 旧书籍类别信息 |
| newtypename | string | 是 | 新书籍类别信息 |

参数说明：
以上参数均放置于header中上传


* 响应参数
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

### 9. 借书/还书
* 基本信息
> 请求路径 ：/book/lend
> 请求方式 ：POST
> 接口描述 ：用于用户借/还书

* 请求参数
| 参数名 | 类型 | 是否必须 | 备注 |
| ---- | ---- | ---- | ----|
| token | string |  是 |  |
| bookid | Integer | 是 |

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
	"code" : 2,
	"msg" : 你没有借过这本书,无法还书,
}
```


### 10. 查询书籍借用记录
* 基本信息
> 请求路径 ：/book/bookhistory
> 请求方式 ：GET
> 接口描述 ：用于查询书籍借用记录

* 请求参数
| 参数名 | 类型 | 是否必须 | 备注 |
| ---- | ---- | ---- | ----|
| token | string |  是 |  |
| bookid | Integer | 是 | 书籍ID |

请求参数举例: http://http://112.124.10.96/book/bookhistory?token=xxx&bookid=114514



* 响应参数
| 名称 | 类型 | 备注 |
| ---- | ---- | ---- |
| code | number | 响应码 0为无权限 1为成功 2为失败|
| msg | string | 返回提示信息|
| data | List | 书籍借用记录列表|

* data返回值
| 名称 | 类型 | 备注 |
| ---- | ---- | ---- |
| logDate | date | 借用/还书时间 |
| userId | Integer | 用户ID |
| userName | string | 用户名称 |
| type | Integer | 类型:1为借出,2为还书 |




* 响应数据样例
``` json
{
	"code" : 1,
	"msg" : 成功,
	"data" : [["logDate" : "2023/11/03","type" : "1","userId" : "121561","userName" : "小红"],["logDate" : "2023/11/05","type" : "2","userId" : "121561","userName" : "小红"] ......]
}
```

### 11. 查询用户借用记录
* 基本信息
> 请求路径 ：/book/userhistory
> 请求方式 ：GET
> 接口描述 ：用于查询书籍借用记录

* 请求参数
| 参数名 | 类型 | 是否必须 | 备注 |
| ---- | ---- | ---- | ----|
| token | string |  是 |  |
| userid | Integer | 否 | 用户ID |

//注: 若为管理员，则查询优先查询userid对应的用户的借用记录，为空或不为管理员权限则查询自己借用记录

请求参数举例: http://http://112.124.10.96/book/userhistory?token=xxx&userid=114514



* 响应参数
| 名称 | 类型 | 备注 |
| ---- | ---- | ---- |
| code | number | 响应码 0为无权限 1为成功 2为失败|
| msg | string | 返回提示信息|
| data | List | 书籍借用记录列表|

* data返回值
| 名称 | 类型 | 备注 |
| ---- | ---- | ---- |
| logDate | date | 借用/还书时间 |
| bookId | Integer | 书籍ID |
| bookName | string | 书籍名称 |
| type | Integer | 类型:1为借出,2为还书 |




* 响应数据样例
``` json
{
	"code" : 1,
	"msg" : 成功,
	"data" : [["logDate" : "2023/11/03","type" : "1","bookId" : "121561","bookName" : "沙丘"],["logDate" : "2023/11/05","type" : "2","bookId" : "121561","bookName" : "沙丘"] ......]
}
```
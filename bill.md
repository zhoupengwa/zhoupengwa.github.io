### API说明：

参数响应格式：
```
{
    "status":,
    "msg": "",
    "data":
}
```
status说明：

    0: 业务处理成功
    1: 业务处理失败
    2: 用户未登录
    888: 请求参数错误
    999: 服务器内部错误



### 一、用户登录

请求地址：

    /api/user/login.do

请求方式：

    POST  

请求参数：JSON


参数名 | 参数类型 | 示例 | 是否必须 |描述| 备注
---|---|---|---|---|---
phone|string|18480000000|是|手机号|len <= 11
password|string|123456987|是|密码|len <= 32

请求示例：

```json
{
	"phone":"18480000000",
	"password":"123456"
}
```

返回示例：
```json
{
    "status": 0,
    "data": {
        "id": 24000605,     
        "phone": "18480000000",    
        "email": null,      
        "password": null,       
        "username": "大脸猫",       
        "gender": 0,        
        "introduce": "hi, guys!",       
        "roleType": 0       
    }
}
```

返回值说明：

id--用户ID

phone--手机号

email--邮箱

username--用户名

gender--性别（0-隐藏，1-男，2-女）

introduce--个性签名

roleType--角色类型（0-普通用户）

### 二、注销登录

请求地址：

    /api/user/logout.do

请求方式：

    POST  

### 三、用户注册

请求地址：

    /api/user/register.do


请求方式：

    POST  

请求参数：JSON


参数名 | 参数类型 | 示例 | 是否必须 |描述| 备注
---|---|---|---|---|---
phone|string|18480000000|是|手机号|len <= 11
password|string|123456987|是|密码|len <= 32
email|string|409044500@qq.com|否|邮箱| len <= 32
username|string|大脸猫|否|用户名|len <= 64
gender|integer|0|否|性别|0-隐藏、1-男、2-女
introduce|string|天苍苍，野茫茫|否|个性签名|len <= 128

请求示例：

```json
{
    "phone": 18480000000,
    "email": "409044500@qq.com",
    "password": "123456",
    "username": "大脸猫",
    "gender": 1,
    "introduce": "hi, guys!"
}
```

返回示例：
```json
{
    "status": 0,
    "msg": "注册成功"
}
```
```json
{
    "status": 1,
    "msg": "该手机号已经注册"
}
```

### 四、查询个人信息(验证登录cookie)

请求地址：

    /api/user/query_info.do


请求方式：

    GET  

返回示例：

```json
{
    "status": 0,
    "data": {
        "id": 24000605,
        "phone": "18480000000",
        "email": null,
        "password": null,
        "username": "大脸猫",
        "gender": 0,
        "introduce": "hi, guys!",
        "roleType": 0
    }
}
```

```json
{
    "status": 2,
    "msg": "用户未登录"
}
```


### 五、更新个人信息(验证登录cookie)

请求地址：

    /api/user/update_info.do


请求方式：

    POST  

请求参数：JSON

参数名 | 参数类型 | 示例 | 是否必须 |描述| 备注
---|---|---|---|---|---
email|string|409044500@qq.com|否|邮箱| len <= 32
username|string|大脸猫|否|用户名|len <= 64
gender|integer|0|否|性别|0-隐藏、1-男、2-女
introduce|string|天苍苍，野茫茫|否|个性签名|len <= 128

请求示例：
```json
{
    "username": "大脸猫2",
    "gender": 1,
    "introduce": "hi, boy!"
}
```

返回示例：

```json
{
    "status": 0,
    "msg": "修改用户信息成功"
}
```

```json
{
    "status": 2,
    "msg": "用户未登录"
}
```

### 六、更改密码(验证登录cookie)

请求地址：

    /api/user/update_password.do


请求方式：

    POST  

请求参数：JSON

参数名 | 参数类型 | 示例 | 是否必须 |描述| 备注
---|---|---|---|---|---
newPassword|string|123456|是|新密码| len <= 32
originPassword|string|123456|是|原密码| len <= 32

请求示例：
```json
{
    "originPassword": "123456",
    "newPassword": "123456"
}
```

返回示例：

```json
{
    "status": 0,
    "msg": "修改密码成功"
}
```

```json
{
    "status": 1,
    "msg": "原密码错误"
}
```

```json
{
    "status": 2,
    "msg": "用户未登录"
}
```




# ecmo老数据库接口文档

1\. 用户相关接口

---

#### **1\. 用户登录**
###### 接口功能
> 登录

###### URL
> POST /user/login/

###### 接口示例
> 地址：[http://localhost:9091/ecmo_admin/user/login/]()
``` javascript
// post请求体
{
  "account": "admin",
  "password": "123456"
}
//返回结果:
{
  "data": {
    "id": 1,
    "account": "admin",
    "name": "123123",
    "role": 0,
    "sex": 1,
    "phone": "13241234234",
    "email": null
  },
  "status": 200,
  "info": "success",
  "pageInfo": null
}
```
#### **2\. 新建/修改用户**
###### 接口功能
> 新建和修改用户

###### URL
> POST /user/save/

###### 请求参数
 
|参数|必选|类型|说明|
|:-----  |:-------|:-----|-----                               |
|id    |false    |int|用户id， 新建时不传或传null|
|role    |true    |int   |用户角色。 0：管理员， 1：录入员。|
|account    |true    |string   |用户名|
|name    |true    |string   |姓名|
|sex    |true    |int   |性别。1：男；2：女。|
|email    |fale    |string   |邮箱|
|phone    |fale    |string   |手机|

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。200：正常；-1：错误。   |
|data  |string | 成功时为用户id， 失败时为null                    |
|info  |string | 成功或错误提示信息                  |

###### 接口示例
> 地址：[http://localhost:9091/ecmo_admin/user/save/]()
``` javascript
// 请求体
{
  "id": 0,  // 创建时不用传id
  "role": 0,
  "account": "string",
  "name": "name",
  "phone": "13200000000",
  "email": "abc@126.com"
}
//返回结果:
{
    "data": null,
    "status": -1,
    "info": "用户ID不存在",
    "myPage": null
}
```

#### **3\. 用户列表**
###### 接口功能
> 获取所有用户

###### URL
> GET /user/list/{role}/{pageNum}/{pageSize}/

###### 请求参数
|参数|必选|类型|说明|
|:-----  |:-------|:-----|----- |
|role  |ture    |int|请求的用户角色类型， -1返回全部角色 0：管理员， 1：录入员。 |
|pageNum  |ture    |int|当前请求页数|
|pageSize  |ture    |int|页大小|

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|totalCount  |int | 总数                  |

###### 接口示例
> 地址：[http://localhost:9091/ecmo_admin/user/list/-1/1/10/]()
``` javascript
//返回结果:
{
  "data": [
    {
      "id": 1,
      "account": "admin",
      "name": "123123",
      "role": 0,
      "sex": 1,
      "phone": "13241234234",
      "email": null
    }
  ],
  "status": 200,
  "info": "success",
  "pageInfo": {
    "pageSize": 10,
    "pageNum": 1,
    "totalCount": 2
  }
}
```

#### **4\. 删除用户**
###### 接口功能
> 根据用户id删除用户

###### URL
> GET /user/delete/{userId}/

###### 请求参数
|参数|必选|类型|说明|
|:-----  |:-------|:-----|-----                               |
|userId  |ture    |int|要删除的用户ID                          |

###### 接口示例
> 地址：[http://localhost:9091/ecmo_admin/user/delete/111/]()
``` javascript
//返回结果:
{
    "data": null,
    "status": -1,
    "info": "用户ID不存在",
    "myPage": null
}
```


#### **5\. 查询用户**
###### 接口功能
> 根据id获取用户信息

###### URL
> GET /user/get/{userId}/
###### 接口示例
> 地址：[http://localhost:9091/ecmo_admin/user/get/1/]()
``` javascript
//返回结果:
{
  "data": {
    "id": 1,
    "account": "admin",
    "name": "123123",
    "role": 0,
    "sex": 1,
    "phone": "13241234234",
    "email": null,
  },
  "status": 200,
  "info": "success"
}
```


#### **6\. 重置密码**
###### 接口功能
> 根据id重置用户密码为123456

###### URL
> GET /user/reset/{userId}/
###### 接口示例
> 地址：[http://localhost:9091/ecmo_admin/user/reset/1/]()
``` javascript
//返回结果:
{
  "data": 0,
  "status": 200,
  "info": "success"
}
```
// 新建病人
{
  "name": "张三",
  "sex": 1,
  "hospNumber": "13242134",
  "visitDate": "2019-11-08",
  "birthday": "2019-11-08"
}


# ecmo老数据库接口文档

## 1\. 用户相关接口

---

#### **1\.1\. 用户登录**
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
#### **1\.2\. 新建/修改用户**
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

#### **1\.3\. 用户列表**
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

#### **1\.4\. 删除用户**
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


#### **1\.5\. 查询用户**
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


#### **1\.6\. 重置密码**
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

## 2\. 病人相关接口

---


#### **2\.1\. 新建/修改病人**
###### 接口功能
> 新建/修改病人

###### URL
> 创建 POST /patient/create/{user_id}/ \
> 修改 POST /patient/modify/{user_id}/

###### 请求参数

|参数|必选|类型|说明|
|:-----  |:-------|:-----|:-----|
|user_id |true    |int|上传用户ID|
|id    |true    |int|病人id, 新建时不传|
|name    |true    |string|病人姓名|
|sex    |true    |int |性别。1：男；2：女。|
|hospNumber    |true    |string |住院号|
|birthday    |true    |string |出生日期，例：1955-11-08|
|visitDate    |true    |string |入选时间，例：2019-08-01|

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|status   |int    |返回结果状态。200：正常；-1：错误。   |
|info  |string | 成功或错误提示信息                  |

###### 接口示例
> 创建地址：[http://localhost:9091/ecmo_admin/patient/create/1/]() \
 修改地址：[http://localhost:9091/ecmo_admin/patient/modify/1/]()
``` javascript
// 请求体
{
  "name": "张三",
  "sex": 1,
  "hospNumber": "13242134",
  "visitDate": "2019-11-08",
  "birthday": "2019-11-08"
}
//返回结果:
{
  "status": -1,
  "info": "未找到id为1的用户。"
}
```

#### **2\.2\. 病人搜索**
###### 接口功能
> 根据一系列搜索条件对病人进行检索

###### URL
> POST /patient/search/{pageNum}/{pageSize}/

###### 请求参数

|参数|必选|类型|说明|
|:-----  |:-------|:-----|:-----|
|pageNum  |ture    |int|当前请求页数|
|pageSize  |ture    |int|页大小|
|name  |false    |string|姓名|
|code  |false    |string|住院号|
|sex  |false    |int|性别，1男,2女,-1全部|
|ageBegin  |false    |int|年龄段起点|
|ageEnd  |false    |int|年龄段终点|
|inTimeBegin  |false    |string|入选时间起点|
|inTimeEnd  |false    |string|入选时间终点|
|crfUpdateTimeBegin  |false    |string|表单更新时间起点|
|crfUpdateTimeEnd  |false    |string|表单更新时间终点|
|crfId  |false    |int|表单ID， 全部 -1|

###### 返回字段
|返回字段|字段类型|说明                              |
|:-----   |:------|:-----------------------------   |
|data  |array | 病人列表                  |
|status   |int    |返回结果状态。200：正常；-1：错误。   |
|info  |string | 成功或错误提示信息                  |

###### 接口示例
> 地址：[http://localhost:9091/ecmo_admin/patient/search/1/10/]()
``` javascript
// 请求体
{
  "name": "张三",
  "code": "0119001",
  "sex": -1,
  "ageBegin": 0,
  "ageEnd": 50,
  "crfUpdateTimeBegin": "2019-11-21",
  "crfUpdateTimeEnd": "2019-11-21",
  "inTimeBegin": "2019-11-21",
  "inTimeEnd": "2019-11-21",
  "crfId": -1
}
//返回结果:
{
  "data": [
    {
      "id": 1,
      "name": "张三",
      "sex": 1,
      "age": 0,
      "hospNumber": "13242134",
      "birthday": "2019-11-08",
      "visitDate": "2019-11-08",
      "patientNumber": "0119001",
      "updateDate": "2019-11-21 16:35:56",
      "createDate": "2019-11-21 16:35:56",
      "updateUser": "name",
      "crfTime": null,
      "status": "I"
    }
  ],
  "status": 200,
  "info": "success",
  "pageInfo": {
    "pageSize": 10,
    "pageNum": 1,
    "totalCount": 1
  }
}
```

#### **2\.3\. 获取单个病人信息**
###### 接口功能
> 根据用户id获取单个病人信息

###### URL
> GET /patient/get/{paId}/

###### 请求参数
|参数|必选|类型|说明|
|:-----  |:-------|:-----|-----                               |
|paId  |ture    |int|要获取的病人ID                          |

###### 接口示例
> 地址：[http://localhost:9091/ecmo_admin/patient/get/1/]()
``` javascript
//返回结果:
{
  "data": {
    "id": 1,
    "name": "张三",
    "sex": 1,
    "age": 0,
    "hospNumber": "13242134",
    "birthday": "2019-11-08",
    "visitDate": "2019-11-08",
    "patientNumber": "0119001",
    "updateDate": "2019-11-21 16:35:56",
    "createDate": "2019-11-21 16:35:56",
    "updateUser": "name",
    "crfTime": null,
    "status": "I"
  },
  "status": 200,
  "info": "success"
}
```

{
	"answers": {
		"111": {
			"answer": "421"
		}
	},
	"crfId": 1,
	"paId": 3,
	"type": 2,
	"userId": 1
}

-[中控服务端API说明](#中控服务端API说明)  
-[API返回格式说明](#API返回格式说明)  
-[API返回代码说明](#API返回代码说明)  
-[参考交易所类API](#参考交易所类API)  
-[参考交易所API](#参考交易所API)  
-[做市交易所API](#做市交易所API)  
-[策略类API](#策略类API)  
-[策略实例API](#策略实例API)  
-[客户端API](#客户端API)
-[策略操作API](#策略操作API)    
-[用户API](#用户API)  
-[登陆API](#登陆API)  
-[权限API](#权限API)  
-[用户权限API](#用户权限API)  
-[策略组API](#策略组API)  
#中控服务端API说明

### BASE_URL=http://47.240.44.22:8090

### API返回格式说明

```json
{
  "code": "返回代码",
  "data": "数据",
  "msg": "信息提醒"
}
```

### API返回代码说明

| Code | Type | Description |
| ---- | ---- | ----------- |
| 20000 | STRING | 正常 |
| 30000 | STRING | 数据库错误 |
| 30001 | STRING | 数据查询错误 |
| 40001 | STRING | 未经授权的错误 |
| 40002 | STRING | TOKEN错误 |
| 40003 | STRING | TOKEN过期 |
| 40004 | STRING | 密码错误 |
| 50000 | STRING | 参数错误 |
| 50001 | STRING | 上传错误 |
| 50003 | STRING | 推送错误 |
| 50004 | STRING | WEBSOCKET错误 |

## 参考交易所类API
### 1.更新或添加参考交易所类
Parameters:

| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| name | STRING | okex | 参考交易所名|
| params_description | STRING | {...} | 参数描述 |
```
POST /refer-exchange-class
```
Response:
```json
{
	"code": 20000,
	"msg": "存储成功",
	"data": {}
}
```

### 2.删除参考交易所类
```
DELETE /refer-exchange-class/{refer_exchange_class_id}
```
Response:
```json
{
	"code": 20000,
	"msg": "删除成功",
	"data": {}
}
```

### 3.获取所有参考交易所类
```
GET /refer-exchange-classes
```
Response:
```json
{
	"code": 20000,
	"msg": "查询成功",
	"data": [
                    {
                        "CreatedAt": "2020-07-02T15:43:03+08:00",
                        "UpdatedAt": "2020-07-02T15:43:03+08:00",
                        "DeletedAt": null,
                        "ID": 4,
                        "name": "okex_v3",
                        "params_description": "[{\"name\":\"apiKey\",\"nick_name\":\"apiKey\",\"default\":\"\",\"show_condition\":\"\",\"type\":\"STRING\",\"sub_type\":\"\",\"sub_params\":\"\",\"description\":\"交易所申请的apiKey\"},{\"name\":\"secret\",\"nick_name\":\"secret\",\"default\":\"\",\"show_condition\":\"\",\"type\":\"STRING\",\"sub_type\":\"\",\"sub_params\":\"\",\"description\":\"交易所申请的secret\"},{\"name\":\"password\",\"nick_name\":\"password\",\"default\":\"\",\"show_condition\":\"\",\"type\":\"STRING\",\"sub_type\":\"\",\"sub_params\":\"\",\"description\":\"交易所申请的password\"}]"
                    },
                    {
                        "CreatedAt": "2020-07-02T15:43:23+08:00",
                        "UpdatedAt": "2020-07-02T15:43:23+08:00",
                        "DeletedAt": null,
                        "ID": 5,
                        "name": "okex_v1",
                        "params_description": "[{\"name\":\"apiKey\",\"nick_name\":\"apiKey\",\"default\":\"\",\"show_condition\":\"\",\"type\":\"STRING\",\"sub_type\":\"\",\"sub_params\":\"\",\"description\":\"交易所申请的apiKey\"},{\"name\":\"secret\",\"nick_name\":\"secret\",\"default\":\"\",\"show_condition\":\"\",\"type\":\"STRING\",\"sub_type\":\"\",\"sub_params\":\"\",\"description\":\"交易所申请的secret\"}]"
                    }
                ]
}
```

## 参考交易所API
### 1.更新或添加参考交易所
Parameters:

| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| name | STRING | okex | 参考交易所名|
| params | STRING | {...} | 参数|
| class_id | STRING | 1 | 参考交易所类id |
```
POST /refer-exchange
```
Response:
```json
{
	"code": 20000,
	"msg": "存储成功",
	"data": {}
}
```

### 2.删除参考交易所
```
DELETE /refer-exchange/{refer_exchange_id}
```
Response:
```json
{
	"code": 20000,
	"msg": "删除成功",
	"data": {}
}
```

### 3.获取所有参考交易所
```
GET /refer-exchanges
```
Response:
```json
{
    "code": 20000,
    "data": [
        {
            "CreatedAt": "2020-07-02T15:52:44+08:00",
            "UpdatedAt": "2020-07-02T15:52:44+08:00",
            "DeletedAt": null,
            "ID": 4,
            "name": "okex_v1_object",
            "class_id": 5,
            "params": "{\"apiKey\": \"hoo6666\",\"secret\": \"hoo9999\"}"
        }
    ],
    "msg": "查询成功"
}
```

## 做市交易所API
### 1.更新或添加做市交易所
Parameters:

| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| name | STRING | hoo | 名称 |
| symbol | STRING | BTC-USDT | 交易对 |
| api_key | STRING | hoo6666666 | api_key |
| secret | STRING | hoo9999999 | secret |
| price_precision | STRING | 4 | 价格精度 |
| volume_precision | STRING | 4 | 数量精度 |

```
POST /exchange
```
Response:
```json
{
	"code": 20000,
	"msg": "存储成功",
	"data": {}
}
```

### 2.删除做市交易所
```
DELETE /exchange/{id}
```
Response:
```json
{
	"code": 20000,
	"msg": "删除成功",
	"data": {}
}
```

### 3.获取所有做市交易所
```
GET /exchanges
```
Response:
```json
{
    "code": 20000,
    "data": [
        {
            "CreatedAt": "2020-06-19T16:24:28+08:00",
            "UpdatedAt": "2020-06-19T16:24:28+08:00",
            "DeletedAt": null,
            "ID": 2,
            "name": "测试交易所账户2",
            "symbol": "BTC-USDT",
            "api_key": "dsgdsge9349tu9",
            "secret": "kvsdvso88888",
            "price_precision": 8,
            "volume_precision": 8
        }
    ],
    "msg": "查询成功"
}
```

## 策略类API
###1.更新或添加策略类
Parameters:
| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| name | STRING | 测试策略类 | 名称 |
| application_name | STRING | testStrategyClass | 应用程序名 |
| params_description | STRING | {...} | 参数描述 |
```
POST /strategt-class
```
Response:
```json
{
	"code": 20000,
	"msg": "存储成功",
	"data": {}
}
```
###2.删除策略类
```
DElETE /strategt-class/{class_id}
```
Response:
```json
{
	"code": 20000,
	"msg": "删除成功",
	"data": {}
}
```
###3.获取所有策略类
```
GET /strategt-classes
```
Response:
```json
{
	"code": 20000,
	"msg": "查询成功",
	"data": {}
}
```

## 策略实例API  
###1.更新或添加策略实例
Parameters:

| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| name | STRING | 测试策略 | 名称 |
| group_id | STRING | 1 | 策略组id |
| class_id | STRING | 1 | 策略类id |
| client_id | STRING | 1 | 客户端id |
| status | STRING | 0 | 状态 |
| params | STRING | {...} | 参数 |
```
POST /strategy-object
```
Response:
```json
{
	"code": 20000,
	"msg": "存储成功",
	"data": {}
}
```
###2.删除策略实例
```
DELETE /strategy-object/{strategy_id}
```
Response:
```json
{
	"code": 20000,
	"msg": "删除成功",
	"data": {}
}
```
###3.获取单个策略实例
```
GET /strategy-object/{strategy_id}
```
Response:
```json
{
    "code": 20000,
    "data": {
        "CreatedAt": "2020-07-02T15:36:11+08:00",
        "UpdatedAt": "2020-07-02T15:36:11+08:00",
        "DeletedAt": null,
        "ID": 11,
        "name": "BTC-USDT基础铺单策略6",
        "class_id": 5,
        "client_id": 2,
        "params": "{\"buyCount\":100,\"buyPrice\":9300,\"sellCount\":100,\"sellPrice\":9300}"
    },
    "msg": "查询成功"
}
```
###4.获取所有策略实例
```
GET /strategy-objects
```
Response:
```json
{
    "code": 20000,
    "data": [
        {
            "CreatedAt": "2020-07-02T15:32:43+08:00",
            "UpdatedAt": "2020-07-02T15:32:43+08:00",
            "DeletedAt": null,
            "ID": 6,
            "name": "BTC-USDT基础铺单策略",
            "class_id": 5,
            "client_id": 1,
            "params": "{\"buyCount\":100,\"buyPrice\":9300,\"sellCount\":100,\"sellPrice\":9300}"
        }
    ],
    "msg": "查询成功"
}
```
###5.获取单个客户端策略实例
```
GET /strategy-objects/{client_id}
```
Response:
```json
{
    "code": 20000,
    "data": [
        {
            "CreatedAt": "2020-07-02T15:32:43+08:00",
            "UpdatedAt": "2020-07-02T15:32:43+08:00",
            "DeletedAt": null,
            "ID": 6,
            "name": "BTC-USDT基础铺单策略",
            "class_id": 5,
            "client_id": 1,
            "params": "{\"buyCount\":100,\"buyPrice\":9300,\"sellCount\":100,\"sellPrice\":9300}"
        }
    ],
    "msg": "查询成功"
}
```
##客户端API
###1.更新或添加客户端
Parameters:

| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| name | STRING | 测试客户端 | 名称 |
| public_host | STRING | 1 | 公网ip |
| private_host | STRING | 1 | 内网ip |
| port | STRING |6666 | 端口 |
```
POST /client
```
Response:
```json
{
	"code": 20000,
	"msg": "查询成功",
	"data": {}
}
```
###2.删除客户端
```
DELETE /client/{client_id}
```
Response:
```json
{
	"code": 20000,
	"msg": "删除成功",
	"data": {}
}
```
###3.通过公网ip和内网ip获取客户端id
Parameters:

| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| public_host | STRING | 34.423.423.99 | 公网ip |
| private_host | STRING | 127.0.0.1 | 内网ip |
```
GET /client
```
Response:
```json
{
    "code": 20000,
    "data": "{id:1}",
    "msg": "查询成功"
}
```
###4.获取所有客户端
```
GET /clients
```
Response:
```json
{
    "code": 20000,
    "data": [
        {
            "CreatedAt": "2020-07-02T16:09:19+08:00",
            "UpdatedAt": "2020-07-02T16:09:19+08:00",
            "DeletedAt": null,
            "ID": 2,
            "name": "测试客户端2",
            "public_host": "434.343.222",
            "private_host": "127.0.0.1",
            "port": "8090",
            "strategy_group_number": 0,
            "cpu_usage": 0,
            "mem_usage": 0,
            "disk_usage": 0
        }
    ],
    "msg": "查询成功"
}
```

## 策略操作API
###1. 操作策略
Parameters:

| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| id | STRING | 1 | 策略id |
| operation | STRING | start | 操作(start/stop) |

```
PUT /strategy-object-control
```
Response:
```json
{
    "code": 20000,
    "data": {},
    "msg": "策略操作成功"
}
```

## 用户API
###1. 更新或添加用户
Parameters:

| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| id | STRING | 1 | 用户id(如果为空则新建) |
| name | STRING | test | 用户名 |
| email | STRING | 2222@qq.com | 邮箱 |
| phone | STRING | 110 | 手机 |
| password | STRING | dfsdfsdgfs | 密码 |
```
POST /user
```
Response:
```json
{
    "code": 20000,
    "data": {
        "id": 2,
        "name": "liangjiefei2",
        "email": "22222",
        "phone": "edeeeeeee",
        "password": "123456",
        "token": null
    },
    "msg": "存储成功"
}
```
###2. 删除用户
```
DELETE /user/{user_id}
```
Response:
```json
{
    "code": 20000,
    "data": "{id:2}",
    "msg": "删除成功"
}
```
###3. 获取所有用户    
```
GET /users
```
Response:
```json
{
    "code": 20000,
    "data": [
        {
            "id": 1,
            "name": "liangjiefei",
            "email": "22222",
            "phone": "r23235325",
            "password": "*****",
            "token": null,
            "CreatedAt": "2020-08-18T15:02:35+08:00",
            "UpdatedAt": "2020-08-18T15:03:15+08:00",
            "DeletedAt": null
        }
    ],
    "msg": "查询成功"
}
```
## 登陆API
###1. 登陆(返回的token需要带在headers内,其他所有的接口都需要验证token,目前还没做)
Parameters:

| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| name | STRING | liangjiefei | 用户名 |
| password | STRING | 123456 | 密码 |
```
POST /login
```
Response:
```json
{
    "code": 20000,
    "data": {
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwibmFtZSI6ImxpYW5namllZmVpIiwiZXhwIjoxNTk3NzY0NDQ0fQ.-4C_0eM-BLdKhnmNbuua7VFoBNyvcNc4KGt73K8uBL4"
    },
    "msg": "登陆成功"
}
```
## 权限API
###1.更新或添加权限
Parameters:

| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| id | STRING | 1 | 为空则为创建 |
| name | STRING | 创建用户权限 | 权限名称 |
| path | STRING | /user | 请求路径 |
| method | STRING | POST | 请求方法 |
```
POST /power
```
Response:
```json
{
    "code": 20000,
    "data": {
        "id": 2,
        "name": "删除用户权限",
        "path": "/user/:id",
        "method": "DELETE"
    },
    "msg": "存储成功"
}
```
###2.删除权限
```
DELETE /power/{power_id}
```
Response:
```json
{
    "code": 20000,
    "data": "{id:2}",
    "msg": "删除成功"
}
```
###3.获取所有权限
```
GET /powers
```
Response:
```json
{
    "code": 20000,
    "data": [
        {
            "id": 1,
            "name": "创建用户权限",
            "path": "/user",
            "method": "POST",
            "CreatedAt": "2020-08-18T15:38:48+08:00",
            "UpdatedAt": "2020-08-18T15:38:48+08:00",
            "DeletedAt": null
        }
    ],
    "msg": "查询成功"
}
```
## 用户权限API
###1.增加用户权限
Parameters:

| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| user_id | STRING | 1 | 用户id |
| power_id | STRING | /1 | 权限id |
```
POST /user-power
```
Response:
```json
{
    "code": 20000,
    "data": {
        "id": 1,
        "user_id": 1,
        "power_id": 1
    },
    "msg": "存储成功"
}
```
###2.删除用户权限
```
DELETE /user-power/{user_power_id}
```
Response:
```json
{
    "code": 20000,
    "data": "{id:2}",
    "msg": "删除成功"
}
```
###3.获取所有用户权限
```
GET /user-powers
```
Response:
```json
{
    "code": 20000,
    "data": [
        {
            "id": 1,
            "user_id": 1,
            "power_id": 1,
            "CreatedAt": "2020-08-18T15:52:34+08:00",
            "UpdatedAt": "2020-08-18T15:52:34+08:00",
            "DeletedAt": null
        }
    ],
    "msg": "查询成功"
}
```
###4.获取某个用户权限
```
GET /user-powers/{user_id}
```
Response:
```json
{
    "code": 20000,
    "data": [
        {
            "id": 1,
            "user_id": 1,
            "power_id": 1,
            "CreatedAt": "2020-08-18T15:52:34+08:00",
            "UpdatedAt": "2020-08-18T15:52:34+08:00",
            "DeletedAt": null
        }
    ],
    "msg": "查询成功"
}
```
## 策略组API
###1.更新或添加策略组
| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| id | INT | 1 | 策略组id(如果为空则为新建) |
| name | STRING | 测试 | 策略组名称 |
| client_id | INT | /1 | 客户端id |
| strategy_objects | LIST | [{"strategy_object_id","strategy_class_id": 1, "strategy_status": 0}] | strategy_object_id为空是则表示新建 |
```
POST /strategy-group
```
Response:
```json
{
    "code": 20000,
    "data": [
                {
                    "id": 13,
                    "name": "liangjiefei2",
                    "client_id": 1,
                    "strategy_objects": [
                        {
                            "strategy_object_id": 14,
                            "strategy_class_id": 13,
                            "strategy_status": 0
                        }
                    ],
                    "CreatedAt": "2020-08-19T10:33:04+08:00",
                    "UpdatedAt": "2020-08-19T10:33:04+08:00",
                    "DeletedAt": null
                }
    ],
    "msg": "查询成功"
}
```
###2.查询所有策略组
```
GET /strategy-groups
```
Response:
```json
{
    "code": 20000,
    "data": [
                {
                    "id": 13,
                    "name": "liangjiefei2",
                    "client_id": 1,
                    "strategy_objects": [
                        {
                            "strategy_object_id": 14,
                            "strategy_class_id": 13,
                            "strategy_status": 0
                        }
                    ],
                    "CreatedAt": "2020-08-19T10:33:04+08:00",
                    "UpdatedAt": "2020-08-19T10:33:04+08:00",
                    "DeletedAt": null
                }
    ],
    "msg": "查询成功"
}
```
###3.删除策略组
```
DELETE /strategy-group/{group_id}
```
Response:
```json
{
    "code": 20000,
    "data": "{id:1}",
    "msg": "删除成功"
}
```

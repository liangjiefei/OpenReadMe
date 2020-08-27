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
-[注册API](#注册API)    
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
| id | INT | 1 | 无id为新增，有id为更新 |
| name | STRING | okex | 参考交易所名|
| params | STRING | {...} | 参数|
| class_id | INT | 1 | 参考交易所类id |
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
| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| page | INT | 1 | 页数 |
| page_size | INT | 1 | 每页数量 |
```
GET /refer-exchanges
```
Response:
```json
{
    "code": 20000,
    "data": {
        "results": [
            {
                "CreatedAt": "2020-08-18T19:03:30+08:00",
                "UpdatedAt": "2020-08-18T19:03:30+08:00",
                "DeletedAt": null,
                "ID": 8,
                "name": "2",
                "class_id": 4,
                "params": "{\"apiKey\":\"1\",\"secret\":\"1\",\"password\":\"1\"}"
            },
            {
                "CreatedAt": "2020-08-18T20:09:33+08:00",
                "UpdatedAt": "2020-08-18T20:09:33+08:00",
                "DeletedAt": null,
                "ID": 9,
                "name": "aaa",
                "class_id": 4,
                "params": "{\"apiKey\":\"111\",\"secret\":\"111\",\"password\":\"111\"}"
            }
        ],
        "count": 4
    },
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
| price_precision | float | 0.001 | 价格最小变动单位 |
| volume_precision | float | 0.001 | 数量最小变动单位 |

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
| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| page | INT | 1 | 页数 |
| page_size | INT | 1 | 每页数量 |
```
GET /exchanges
```
Response:
```json
{
    "code": 20000,
    "data": {
        "results": [
            {
                "CreatedAt": "2020-08-20T17:42:10+08:00",
                "UpdatedAt": "2020-08-20T17:58:49+08:00",
                "DeletedAt": null,
                "ID": 11,
                "name": "111",
                "symbol": "111",
                "api_key": "111",
                "secret": "111",
                "price_precision": 0,
                "volume_precision": 0
            }
        ],
        "count": 6
    },
    "msg": "查询成功"
}
```
### 4.通过做市交易所名搜索做市交易所
```
GET /exchanges/{exchange_name}
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
### 1.更新或添加策略类
Parameters:
| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| id | INT | 1 | 策略类id(如果为空则为新建) |
| name | STRING | 测试策略类 | 名称 |
| application_name | STRING | testStrategyClass | 应用程序名 |
| params_description | STRING | {...} | 参数描述 |
| strategy_class_description | STRING | 这是一个测试策略类 | 策略类描述 |
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
### 2.删除策略类
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
### 3.获取所有策略类
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
### 1.更新或添加策略实例
Parameters:

| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| id | INT | 1 | 策略id |
| group_id | STRING | 1 | 策略组id |
| class_id | STRING | 1 | 策略类id |
| client_id | STRING | 1 | 客户端id |
| params | STRING | {...} | 参数 |
| status | STRING | 0 | 状态 |
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
### 2.删除策略实例
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
### 3.获取单个策略实例
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
### 4.获取所有策略实例
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
### 5.获取单个客户端策略实例
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
### 1.更新或添加客户端
Parameters:
| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| id | INT | 1 | id(有则更新没有则新建) |
| name | STRING | 测试客户端 | 名称 |
| public_host | STRING | 1 | 公网ip |
| port | STRING | 6666 | 端口 |
| cpu_usage | float | 0.1 | cpu使用率 |
| mem_usage | float | 0.2 | 内存使用率 |
| disk_usage | float | 0.3 | 硬盘使用率 |
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
### 2.删除客户端
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
### 3.通过公网ip获取客户端id
Parameters:

| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| public_host | STRING | 34.423.423.99 | 公网ip |
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
### 4.获取所有客户端
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
### 5.编辑客户端备注
Parameters:
| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| id | INT | 1 | 客户端id |
| remark | STRING | 1 |  备注 |
```
POST /client/remark
```
Response:
```json
{
    "code": 20000,
    "data": {
        "CreatedAt": "2020-07-02T16:09:19+08:00",
        "UpdatedAt": "2020-08-19T15:49:04.816883+08:00",
        "DeletedAt": null,
        "ID": 2,
        "name": "测试客户端2",
        "public_host": "434.343.222",
        "private_host": "127.0.0.1",
        "port": "8090",
        "strategy_group_number": 0,
        "cpu_usage": 0,
        "mem_usage": 0,
        "disk_usage": 0,
        "remark": "dsdfsdf"
    },
    "msg": "更新客户端备注成功"
}
```

## 策略操作API
### 1. 操作策略
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
### 1. 更新或添加用户
Parameters:

| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| id | STRING | 1 | 用户id(如果为空则新建) |
| name | STRING | 1111 | 用户名 |
| email | STRING | 2222@qq.com | 邮箱 |
| phone | STRING | 110 | 手机 |
| password | STRING | 1111 | 密码 |
| powers | LIST | ["StrategyParamsPower","StrategyGroupsPower","ReferExchangeParamsPower","ReferExchangesPower","ExchangesPower","ClientsPower","UsersPower"] | 权限 |
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
### 2. 删除用户
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
### 3. 获取所有用户    
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
### 1. 登陆(返回的token需要带在headers内，字段为Authorization)
Parameters:

| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| name | STRING | admin | 用户名 |
| password | STRING | admin | 密码 |
```
POST /login
```
Response:
```json
{
    "code": 20000,
    "data": {
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwibmFtZSI6ImFkbWluIiwiZXhwIjoxNTk4MzA0NTkxfQ.JZLV4EmDN8YuP8qweAXd6KL6TLggWWuL_0xtFWD9qtA",
        "powers": [
            "StrategyParamsPower",
            "StrategyGroupsPower",
            "ReferExchangeParamsPower",
            "ReferExchangesPower",
            "ExchangesPower",
            "ClientsPower",
            "UsersPower"
        ]
    },
    "msg": "登陆成功"
}
```
## 策略组API
### 1.更新或添加策略组
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
### 2.查询所有策略组
| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| page | INT | 1 | 页数 |
| page_size | INT | 1 | 每页数量 |
```
GET /strategy-groups
```
Response:
```json
{
    "code": 20000,
    "data": {
        "results": [
            {
                "id": 22,
                "name": "测试",
                "client_id": 2,
                "client_ip": "434.343.222",
                "strategy_objects": [
                    {
                        "strategy_object_id": 28,
                        "strategy_client_id": 2,
                        "strategy_class_id": 13,
                        "strategy_class_name": "测试select类参数",
                        "strategy_client_ip": "434.343.222",
                        "strategy_status": 0
                    },
                    {
                        "strategy_object_id": 43,
                        "strategy_client_id": 2,
                        "strategy_class_id": 1,
                        "strategy_class_name": "",
                        "strategy_client_ip": "434.343.222",
                        "strategy_status": 0
                    }
                ]
            }
        ],
        "count": 7
    },
    "msg": "查询成功"
}
```
### 3.删除策略组
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
### 4.通过策略组名搜索策略组
```
GET /strategy-groups/{strategy_group_name}
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
# 注册API
### 1. 注册用户
Parameters:
| Name | Type | Example | Description  |
| ---- | ---- | -------- | ------------ |
| name | STRING | 1111 | 用户名 |
| email | STRING | 2222@qq.com | 邮箱 |
| phone | STRING | 110 | 手机 |
| password | STRING | 1111 | 密码 |
```
POST /register
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
        "password": "123456"
    },
    "msg": "注册成功"
}
```
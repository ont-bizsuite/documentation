# Api Documentation


<a name="overview"></a>
## 概览
Api Documentation


### 版本信息
*版本* : 1.0


### 许可信息
*许可证* : Apache 2.0  
*许可网址* : http://www.apache.org/licenses/LICENSE-2.0  
*服务条款* : urn:tos


### URI scheme
*域名* : localhost:10334  
*基础路径* : /


### 标签

* 回调接口 : Common Controller
* 数据接口 : Data Controller
* 订单接口 : Order Controller




<a name="paths"></a>
## 资源

<a name="78544609b1597609795a047e77d94f9e"></a>
### 回调接口
Common Controller


<a name="invokeusingpost"></a>
#### 通用回调
```
POST /back/invoke
```


##### 说明
通用回调


##### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Body**|**req**  <br>*必填*|req|[TransactionDto](#transactiondto)|


##### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[Result](#result)|


##### 消耗

* `application/json`


##### 生成

* `*/*`


##### HTTP请求示例

###### 请求 path
```
/back/invoke
```


###### 请求 body
```
json :
{
  "action" : "string",
  "id" : "string",
  "params" : "object",
  "version" : "string"
}
```


##### HTTP响应示例

###### 响应 200
```
json :
{
  "action" : "string",
  "desc" : "string",
  "error" : 0,
  "result" : "object",
  "version" : "string"
}
```


<a name="invokeresultusingget"></a>
#### 查询结果
```
GET /back/result/{id}
```


##### 说明
查询结果


##### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Path**|**id**  <br>*必填*|id|string|


##### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[Result](#result)|


##### 生成

* `*/*`


##### HTTP请求示例

###### 请求 path
```
/back/result/string
```


##### HTTP响应示例

###### 响应 200
```
json :
{
  "action" : "string",
  "desc" : "string",
  "error" : 0,
  "result" : "object",
  "version" : "string"
}
```


<a name="f0e5dcfd47ec5454a1ba051b8e2fa9f4"></a>
### 数据接口
Data Controller


<a name="registerdataidusingpost"></a>
#### 构造注册dataId的交易
```
POST /api/v1/data/dataId
```


##### 说明
构造注册dataId的交易


##### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Body**|**req**  <br>*必填*|req|[DataIdDto](#dataiddto)|


##### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[Result](#result)|


##### 消耗

* `application/json`


##### 生成

* `*/*`


##### HTTP请求示例

###### 请求 path
```
/api/v1/data/dataId
```


###### 请求 body
```
json :
{
  "dataId" : "string",
  "ontid" : "string"
}
```


##### HTTP响应示例

###### 响应 200
```
json :
{
  "action" : "string",
  "desc" : "string",
  "error" : 0,
  "result" : "object",
  "version" : "string"
}
```


<a name="33be1f1e9f5622971ec234e687e3229a"></a>
### 订单接口
Order Controller


<a name="applyusingpost"></a>
#### 申请仲裁
```
POST /api/v1/order/apply
```


##### 说明
申请仲裁


##### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Body**|**req**  <br>*必填*|req|[OrderDto](#orderdto)|


##### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[Result](#result)|


##### 消耗

* `application/json`


##### 生成

* `*/*`


##### HTTP请求示例

###### 请求 path
```
/api/v1/order/apply
```


###### 请求 body
```
json :
{
  "orderId" : "string"
}
```


##### HTTP响应示例

###### 响应 200
```
json :
{
  "action" : "string",
  "desc" : "string",
  "error" : 0,
  "result" : "object",
  "version" : "string"
}
```


<a name="arbitrationusingpost"></a>
#### 仲裁判定
```
POST /api/v1/order/arbitration
```


##### 说明
仲裁判定


##### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Body**|**req**  <br>*必填*|req|[ArbitrationDto](#arbitrationdto)|


##### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[Result](#result)|


##### 消耗

* `application/json`


##### 生成

* `*/*`


##### HTTP请求示例

###### 请求 path
```
/api/v1/order/arbitration
```


###### 请求 body
```
json :
{
  "isWin" : false,
  "makerReceiveAmount" : 0,
  "orderId" : "string",
  "takerReceiveAmount" : 0
}
```


##### HTTP响应示例

###### 响应 200
```
json :
{
  "action" : "string",
  "desc" : "string",
  "error" : 0,
  "result" : "object",
  "version" : "string"
}
```


<a name="authorderusingpost"></a>
#### 上架授权
```
POST /api/v1/order/auth
```


##### 说明
上架授权


##### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Body**|**req**  <br>*必填*|req|[AuthDto](#authdto)|


##### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[Result](#result)|


##### 消耗

* `application/json`


##### 生成

* `*/*`


##### HTTP请求示例

###### 请求 path
```
/api/v1/order/auth
```


###### 请求 body
```
json :
{
  "accessCount" : 0,
  "amount" : 0,
  "dataId" : "string",
  "expireTime" : 0,
  "makerReceiveAddress" : "string",
  "mpReceiveAddress" : "string",
  "name" : "string",
  "ojList" : [ "string" ],
  "price" : 0,
  "symbol" : "string",
  "transferCount" : 0
}
```


##### HTTP响应示例

###### 响应 200
```
json :
{
  "action" : "string",
  "desc" : "string",
  "error" : 0,
  "result" : "object",
  "version" : "string"
}
```


<a name="confirmusingpost"></a>
#### 确认订单
```
POST /api/v1/order/confirm
```


##### 说明
确认订单


##### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Body**|**req**  <br>*必填*|req|[OrderDto](#orderdto)|


##### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[Result](#result)|


##### 消耗

* `application/json`


##### 生成

* `*/*`


##### HTTP请求示例

###### 请求 path
```
/api/v1/order/confirm
```


###### 请求 body
```
json :
{
  "orderId" : "string"
}
```


##### HTTP响应示例

###### 响应 200
```
json :
{
  "action" : "string",
  "desc" : "string",
  "error" : 0,
  "result" : "object",
  "version" : "string"
}
```


<a name="takeorderusingpost"></a>
#### 购买下单
```
POST /api/v1/order/take
```


##### 说明
购买下单


##### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Body**|**req**  <br>*必填*|req|[PurchaseDto](#purchasedto)|


##### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[Result](#result)|


##### 消耗

* `application/json`


##### 生成

* `*/*`


##### HTTP请求示例

###### 请求 path
```
/api/v1/order/take
```


###### 请求 body
```
json :
{
  "authId" : "string",
  "oj" : "string",
  "takerReceiveAddress" : "string",
  "tokenAmount" : "string"
}
```


##### HTTP响应示例

###### 响应 200
```
json :
{
  "action" : "string",
  "desc" : "string",
  "error" : 0,
  "result" : "object",
  "version" : "string"
}
```


<a name="gettokenbalanceusingget"></a>
#### 查询token剩余流转次数和访问次数
```
GET /api/v1/order/token/balance/{tokenId}
```


##### 说明
查询token剩余流转次数和访问次数


##### 参数

|类型|名称|说明|类型|
|---|---|---|---|
|**Query**|**tokenId**  <br>*必填*|token号|string|


##### 响应

|HTTP代码|说明|类型|
|---|---|---|
|**200**|OK|[Result](#result)|


##### 生成

* `*/*`


##### HTTP请求示例

###### 请求 path
```
/api/v1/order/token/balance/{tokenId}
```


###### 请求 query
```
json :
{
  "tokenId" : "string"
}
```


##### HTTP响应示例

###### 响应 200
```
json :
{
  "action" : "string",
  "desc" : "string",
  "error" : 0,
  "result" : "object",
  "version" : "string"
}
```




<a name="definitions"></a>
## 定义

<a name="arbitrationdto"></a>
### ArbitrationDto

|名称|说明|类型|
|---|---|---|
|**isWin**  <br>*可选*|仲裁结果，买家胜利为true  <br>**样例** : `false`|boolean|
|**makerReceiveAmount**  <br>*可选*|卖家获取钱款  <br>**样例** : `0`|integer (int64)|
|**orderId**  <br>*可选*|orderId  <br>**样例** : `"string"`|string|
|**takerReceiveAmount**  <br>*可选*|买家获取钱款  <br>**样例** : `0`|integer (int64)|


<a name="authdto"></a>
### AuthDto

|名称|说明|类型|
|---|---|---|
|**accessCount**  <br>*可选*|token允许访问次数  <br>**样例** : `0`|integer (int32)|
|**amount**  <br>*可选*|上架授权数量  <br>**样例** : `0`|integer (int32)|
|**dataId**  <br>*可选*|dataId  <br>**样例** : `"string"`|string|
|**expireTime**  <br>*可选*|token的过期时间  <br>**样例** : `0`|integer (int64)|
|**makerReceiveAddress**  <br>*可选*|卖家收款地址  <br>**样例** : `"string"`|string|
|**mpReceiveAddress**  <br>*可选*|平台方收款地址  <br>**样例** : `"string"`|string|
|**name**  <br>*可选*|name  <br>**样例** : `"string"`|string|
|**ojList**  <br>*可选*|仲裁者地址列表  <br>**样例** : `[ "string" ]`|< string > array|
|**price**  <br>*可选*|单价  <br>**样例** : `0`|integer (int64)|
|**symbol**  <br>*可选*|symbol  <br>**样例** : `"string"`|string|
|**transferCount**  <br>*可选*|token允许流转次数  <br>**样例** : `0`|integer (int32)|


<a name="dataiddto"></a>
### DataIdDto

|名称|说明|类型|
|---|---|---|
|**dataId**  <br>*可选*|dataId  <br>**样例** : `"string"`|string|
|**ontid**  <br>*可选*|ontid  <br>**样例** : `"string"`|string|


<a name="orderdto"></a>
### OrderDto

|名称|说明|类型|
|---|---|---|
|**orderId**  <br>*必填*|订单id  <br>**样例** : `"string"`|string|


<a name="purchasedto"></a>
### PurchaseDto

|名称|说明|类型|
|---|---|---|
|**authId**  <br>*可选*|authId  <br>**样例** : `"string"`|string|
|**oj**  <br>*可选*|选取的仲裁方  <br>**样例** : `"string"`|string|
|**takerReceiveAddress**  <br>*可选*|买家收货地址  <br>**样例** : `"string"`|string|
|**tokenAmount**  <br>*可选*|购买数量  <br>**样例** : `"string"`|string|


<a name="result"></a>
### Result

|名称|说明|类型|
|---|---|---|
|**action**  <br>*可选*|**样例** : `"string"`|string|
|**desc**  <br>*可选*|**样例** : `"string"`|string|
|**error**  <br>*可选*|**样例** : `0`|integer (int32)|
|**result**  <br>*可选*|**样例** : `"object"`|object|
|**version**  <br>*可选*|**样例** : `"string"`|string|


<a name="transactiondto"></a>
### TransactionDto

|名称|说明|类型|
|---|---|---|
|**action**  <br>*可选*|action  <br>**样例** : `"string"`|string|
|**id**  <br>*可选*|id  <br>**样例** : `"string"`|string|
|**params**  <br>*可选*|params  <br>**样例** : `"object"`|object|
|**version**  <br>*可选*|version  <br>**样例** : `"string"`|string|




<a name="securityscheme"></a>
## 安全

<a name="jwt"></a>
### JWT
*类型* : apiKey  
*名称* : Authorization  
*在* : HEADER




# oscore-scan-server

## 接口文档

### 获取oscore二维码

```text
url：/scan/apply-oscore
method：POST
```

- 请求：
```json
{
  "apiId": 0,
  "credentialId": 0,
  "dataProviderId": 0
}
```

| Field_Name    | Type    | Description |
|:--------------|:--------|:------------|
| apiId         | int     | 算法Api id  |
| credentialId  | int     | oscore 发证方id  |
| dataProviderId| int     | 数据提供方id  |


- 响应：

```json
{
	"action": "applyOscore",
	"error": 0,
	"desc": "SUCCESS",
	"result": {
		"qrCode": {
			"ONTAuthScanProtocol": "https://xxx"
		},
		"id": "1234"
	},
	"version": "v1"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| action              | String | 动作标志                      |
| version             | String | 版本号                        |
| error               | int    | 错误码                        |
| desc                | String | 成功为SUCCESS，失败为错误描述 |
| result              | Map    | 成功返回二维码参数，失败返回""|
| qrCode              | Map    | 二维码参数|
| id                  | String | 二维码id|


### 获取oscore结果查询

```text
url：/scan/result/{id}
method：GET
```

- 请求：

| Field_Name    | Type    | Description |
|:--------------|:--------|:------------|
| id            | String  | 二维码id    |


- 响应：

```json
{
	"action": "queryResult",
	"error": 0,
	"desc": "SUCCESS",
	"result": {
		"state": 1,
		"errorInfo": "error",
		"ontId": "did:ont:Axxx",
		"addressCredential": "xxx.xxx.xxx",
		"oscoreId": "81e88980-266b-44c9-93b4-d4af42bae99e"
	},
	"version": "v1"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| action              | String | 动作标志                      |
| version             | String | 版本号                        |
| error               | int    | 错误码                        |
| desc                | String | 成功为SUCCESS，失败为错误描述 |
| result              | Map    | 成功返回获取oscore结果，失败返回""|
| state               | int    | null:无结果；1:成功；0:失败|
| errorInfo           | String | 错误信息，state为0返回|
| ontId               | String | 扫码ontId, state为1返回|
| addressCredential   | String | 钱包地址VC, state为1返回|
| oscoreId            | String | 查询oscore用id, state为1返回|


### 查询oscore

```text
url：/scan/query-oscore/{id}
method：GET
```

- 请求：
| Field_Name    | Type    | Description |
|:--------------|:--------|:------------|
| id            | String  | 查询oscore用id    |


- 响应：

```json
{
	"action": "queryOscore",
	"error": 0,
	"desc": "SUCCESS",
	"result": {
		"state": 2,
		"oscoreCredential": "xxx.xxx.xxx"
	},
	"version": "v1"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| action              | String | 动作标志                      |
| version             | String | 版本号                        |
| error               | int    | 错误码                        |
| desc                | String | 成功为SUCCESS，失败为错误描述 |
| result              | Map    | 成功返回获取oscore结果，失败返回""|
| state               | int    | 1:等待oscore结果；2:成功; 其它：失败|
| oscoreCredential    | String | oscore VC, state为2返回|

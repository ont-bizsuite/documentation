#algorithm-server

[接口规范](#接口规范)
	- [算法接口](#算法接口)
		- [计算oscore](#计算oscore)

## 算法接口

### 计算oscore

```text
url：/api/v1/algorithm/oscore/sign
method：POST
```

- 请求：

```json
{
	"provider_did": "did:ont:TR2xHwqKFd2UCpNauX2WTQfYHycpjBonzv",
	"data": {
		"user_did": "did:ont:Axxxxxx",
		"asset_infos": [{
			"token_name": "ONT",
			"sum_amount": "100000",
			"current_balance": "100",
			"days": 10
		}, {
			"token_name": "ETH",
			"current_balance": "1000",
			"sum_amount": "30000",
			"days": 30
		}]
	},
	"sig": "016fa3a6834c9679e2e138404166a2a6b4dca46040a3be068952d080fa1dca2f49467566ee6381230eb0de8658089f3145d15058293f5c315da1aec1c12256c2ef"
}
```

| Field_Name  | Type       | Description |
|:------------|:-----------|:------------|
| data        | Map        | 数据    |
| user_did    | String     | 资产拥有者ontId    |
| asset_infos | List       | 资产数据    |
| token_name  | String     | 资产token名称    |
| current_balance| String  | 该资产当前余额    |
| sum_amount  | String     | 该资产n天内总持有量    |
| days        | Integer    | n天    |
| sig         | String     | 对data转成json字符串(key按照字母排序)的签名    |


```
tokenName(Case insensitive)：
USDT
USDC
SUSD
WBTC
RENBTC
ONT
ONG
NEO
GAS
ETH
BTC
WING
DAI
OKB
UNI
KLAY
TRX
```


- 响应：

```json
{
	"user_did": "did:ont:Axxxxxxx",
	"provider_did": "did:ont:Axxxxxxxxx",
	"subject": {
		"did": "did:ont:Axxxxxxx",
		"score": 900
	},
	"sig": "016fa3a6834c9679e2e138404166a2a6b4dca46040a3be068952d080fa1dca2f49467566ee6381230eb0de8658089f3145d15058293f5c315da1aec1c12256c2ef"
}
```

| Field_Name | Type   | Description                   |
|:-----------|:-------|:------------------------------|
| user_did   | String | oScore对应的ontId             |
| provider_did | String| oScore算法提供方did          |
| subject    | Map    | 成功返回oScore，失败返回""    |
| did        | String | oScore对应的ontId             |
| score      | String | oScore计算分数               |
| sig        | String | 对data转成json字符串(key按照字母排序)的签名   |


# Oscore RestAPI Document


## 1. Introduction

This document is the introduction of Oscore backend restful API.

## 2. Restful Api List

| Method | URL | Description |
|:---| :---| :---|
| [btcbalance](#1-btcbalance)                     | POST  /api/v1/btcbalance            | QueryBtcBalance |
| [ethbalance](#2-ethbalance)                     | POST   /api/v1/ethbalance           | QueryEthBalance |
| [saveaddrs](#3-saveaddrs)                       | POST   /api/v1/saveaddrs            | Crypto Save Addrs|
| [getaddrs](#4-getaddrs)                         | POST    /api/v1/getaddrs            | Crypto Get Addrs |
| [deladdrs](#5-deladdrs)                         | DELETE  /api/v1/addrs               | Crypto Delete Addrs |
| [updateaddrs](#6-updateaddrs)                   | POST    /api/v1/updateaddrs         | Crypto Update Addrs |
| [saveexchangeinfo](#7-saveexchangeinfo)         | POST    /api/v1/saveexchangeinfo    | Exchange Save Data|
| [getexchangeinfos](#8-getexchangeinfos)         | POST    /api/v1/getexchangeinfos    | Exchange Get Data |
| [delexchangeinfo](#9-delexchangeinfo)           | DELETE  /api/v1/exchangeinfo        | Exchange Del Data |
| [updateexchange](#10-updateexchange)    | POST    /api/v1/updateexchange      | Exchange Update Data |
| [createcredential](#11-createcredential)    | POST    /api/v1/createcredential     | Create wallet address credential |
| [revokecredential](#12-revokecredential)    | POST    /api/v1/createcredential     | Revoke wallet address credential |
| [applyscorecredential](#13-applyscorecredential)    | POST    /api/v1/applyscorecredential     | Apply score credentail |
| [applyuuid](#14-applyuuid)    | POST    /api/v1/applyuuid     | Apply login uuid |
| [login](#15-login)    | POST    /api/v1/login     |  login  |
### 1 btcbalance
QueryBtcBalance

POST

```
http://172.168.3.45:8090/api/v1/btcbalance
```
Request body example:

```json

{
    "address": "16XCPAqAxeaaqrN59RAuYVDBJ6jVPG8ifb",
    "did": "",
    "didsign": ""
}

```

Response:

```json
{
    "code": 0,
    "data": {
        "balance": "0",
        "price": "11216.3480139145866529",
        "changepercent24hr": "-0.2736114879905756"
    }
}
```


### 2 ethbalance
QueryEthBalance

POST


```
http://172.168.3.45:8090/api/v1/ethbalance
```
Request body example:

```json

{
    "address": "0x689C56AEf474Df92D44A1B70850f808488F9769C",
    "did": "",
    "didsign": ""
}

```

Response:

```json
{
    "code": 0,
    "data": {
        "balance": "11401445641861179066452",
        "price": "388.5779596519034360",
        "changepercent24hr": "-0.3961781083794124"
    }
}
```

### 3 saveaddrs
Crypto save addrs

POST


```
http://172.168.3.45:8090/api/v1/saveaddrs
```
Request body example:

```json

{
	"did": "did:ont:TQFmfrbQboDUSeV989Zp867r6Dawb1MPSF",
	"didsing":"",
	"data": 
		{
			"name": "eth1",
			"address":"0x7fc74358983f7d70Bfb700C0289A205F2bB509D1",
			"cryptotype":"ethereum",
			"createtime":"1597309598",
			"toshow":"1"
		}
}

```

Response:

```json
{
    "code": 0,
    "data": {
        "uuid": "c2f479a8-cbae-41f8-b1f6-4fa5e36cc285"
    }
}
```

### 4 getaddrs
Crypto get addrs

POST


```
http://172.168.3.45:8090/api/v1/getaddrs
```
Request body example:

```json

{
	"did": "did:ont:TQFmfrbQboDUSeV989Zp867r6Dawb1MPSF",
	"didsign":""
}

```

Response:

```json
{
    "code": 0,
    "data": {
        "data": [
            {
                "name": "eth1",
                "address": "0x7fc74358983f7d70Bfb700C0289A205F2bB509D1",
                "cryptotype": "ethereum",
                "createtime": "1597309598",
                "toshow": "1",
                "uuid": "c2f479a8-cbae-41f8-b1f6-4fa5e36cc285",
                "balance": "2289.668558918720404068",
                "price":"397.3226048453480190"
            }
        ]
    }
}
```

### 5 deladdrs
Crypto delete addrs

DELETE


```
http://172.168.3.45:8090/api/v1/addrs
```
Request body example:

```json

{
	"did": "did:ont:TQFmfrbQboDUSeV989Zp867r6Dawb1MPSF",
	"didsign":"",
	"uuid":"2f04037a-7be8-429b-b0ae-acc86644be88"
}
```

Response:

```json
{
    "code": 0,
    "data": {
        "uuid": "2f04037a-7be8-429b-b0ae-acc86644be88"
    }
}
```


### 6 updateaddrs
Crypto update addrs

POST


```
http://172.168.3.45:8090/api/v1/updateaddrs
```
Request body example:

```json

{
	"did": "did:ont:TPKbGMLMkrXt2Ut9rmRzmf2x6KvtFx1JAS",
	"didsing": "",
	"uuid": "d48a0d38-7d5b-4f72-aa7e-b89d77f67e44",
	"name": "eth777",
	"toshow": "0"
}}
```

Response:

```json
{
    "code": 0,
    "data": {
        "uuid": "d48a0d38-7d5b-4f72-aa7e-b89d77f67e44"
    }
}
```


### 7 saveexchangeinfo
Exchange Save Data

POST


```
http://172.168.3.45:8090/api/v1/saveexchangeinfo
```
Request body example:

```json

{
	"did": "did:ont:TQFmfrbQboDUSeV989Zp867r6Dawb1MPSF",
	"didsign":"",
	"data": 
		{
			"name": "eth1",
			"exchange":"binance",
			"apikey":"abcd",
			"createtime":"1597309598",
			"toshow":"1"
		}
}

```

Response:

```json

{
    "code": 0,
    "data": {
        "uuid": "dc5d0a0c-be51-4c6a-bf71-fb1b88ebf472"
    }
}
```

### 8 getexchangeinfos 
 Exchange Get Data

POST


```
http://172.168.3.45:8090/api/v1/getexchangeinfos
```
Request body example:

```json

{
	"did": "did:ont:TQFmfrbQboDUSeV989Zp867r6Dawb1MPSF",
	"didsign":""
}

```

Response:

```json
{
    "code": 0,
    "data": {
        "data": [
            {
                "name": "1234",
                "exchange": "binance",
                "apikey": "abcd",
                "createtime": "1597309598",
                "toshow": "0",
                "uuid": "a80e8ae8-b5e1-4923-92b0-025188528f63"
            }
        ]
    }
}
```

### 9 delexchangeinfo
Exchange Del Data 

DELETE


```
http://172.168.3.45:8090/api/v1/exchangeinfo 
```
Request body example:

```json

{
	"did": "did:ont:TQFmfrbQboDUSeV989Zp867r6Dawb1MPSF",
	"didsign":"",
	"uuid":"dc5d0a0c-be51-4c6a-bf71-fb1b88ebf472"
}
```

Response:

```json
{
    "code": 0,
    "data": {
        "uuid": "dc5d0a0c-be51-4c6a-bf71-fb1b88ebf472"
    }
}
```

### 10 updateexchange
Exchange update Data 

POST


```
http://172.168.3.45:8090/api/v1/updateexchange
```
Request body example:

```json

{
	"did": "did:ont:TPKbGMLMkrXt2Ut9rmRzmf2x6KvtFx1JAS",
	"didsing": "",
	"uuid": "0ebd56e2-58a3-40e8-bdf2-221e0673df82",
	"name": "binance111",
	"toshow": "1"
}
```

Response:

```json
{
    "code": 0,
    "data": {
        "uuid": "0ebd56e2-58a3-40e8-bdf2-221e0673df82"
    }
}
```

### 11 createcredential

Create a wallet address credential

POST

```
http://172.168.3.45:8090/api/v1/createcredentail
```

Request body example:

```
{
	"Chain":"ETH",
	"DID":"did:ont:AWbv8ZQ3jYd45qUADrjhYBtshrfRPfwEsT",
	"Address":"0xf63348f9d3dd8f22f5cc05dc02eecea376a9d393",
	  "Sig":"0x3059fbc31d2ecc52453c93ed446bd7c9c5bec6734b343fecd1e3a16e5d56d5775a7d7a652bd9611de12736af02220ffcfd016cd55f7d7d89b53bf6c818bec1ca1b"
}
```

Response:

```
{
    "code": 0,
    "data": {
        "chain": "ETH",
        "did": "did:ont:AWbv8ZQ3jYd45qUADrjhYBtshrfRPfwEsT",
        "credential": "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDpvbnQ6VFIyeEh3cUtGZDJVQ3BOYXVYMldUUWZZSHljcGpCb256diNrZXlzLTEiLCJ0eXAiOiJKV1QifQ==.eyJpc3MiOiJkaWQ6b250OlRSMnhId3FLRmQyVUNwTmF1WDJXVFFmWUh5Y3BqQm9uenYiLCJleHAiOjE1OTkzODUyODMsIm5iZiI6MTU5ODUyMTI4NCwiaWF0IjoxNTk4NTIxMjg0LCJqdGkiOiJ1cm46dXVpZDozYWIyYmZhYi0yNDc2LTQ1NDQtOTdhYS00NzM2YTA3OTJhZjQiLCJ2YyI6eyJAY29udGV4dCI6WyJodHRwczovL3d3dy53My5vcmcvMjAxOC9jcmVkZW50aWFscy92MSIsImh0dHBzOi8vb250aWQub250LmlvL2NyZWRlbnRpYWxzL3YxIiwiY29udGV4dDEiLCJjb250ZXh0MiJdLCJ0eXBlIjpbIlZlcmlmaWFibGVDcmVkZW50aWFsIiwiT3Njb3JlQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJjaGFpbiI6IkVUSCIsImFkZHJlc3MiOiIweGY2MzM0OGY5ZDNkZDhmMjJmNWNjMDVkYzAyZWVjZWEzNzZhOWQzOTMiLCJvbnRfZGlkIjoiZGlkOm9udDpBV2J2OFpRM2pZZDQ1cVVBRHJqaFlCdHNocmZSUGZ3RXNUIiwic2lnIjoiMHgzMDU5ZmJjMzFkMmVjYzUyNDUzYzkzZWQ0NDZiZDdjOWM1YmVjNjczNGIzNDNmZWNkMWUzYTE2ZTVkNTZkNTc3NWE3ZDdhNjUyYmQ5NjExZGUxMjczNmFmMDIyMjBmZmNmZDAxNmNkNTVmN2Q3ZDg5YjUzYmY2YzgxOGJlYzFjYTFiIn0sImNyZWRlbnRpYWxTdGF0dXMiOnsiaWQiOiI0ZjdmMTU5YWM0Yjk5MTNiYjE4NWZkZjE4OTU3MDVmNjFiN2QwY2M2IiwidHlwZSI6IkF0dGVzdENvbnRyYWN0In0sInByb29mIjp7ImNyZWF0ZWQiOiIyMDIwLTA4LTI3VDA5OjQxOjI0WiIsInByb29mUHVycG9zZSI6ImFzc2VydGlvbk1ldGhvZCJ9fX0=.TI27LgYasAGYlb0rivqq/gw26PNnEp2L2r5nfSX0T/lCV0OWSEuhS8tN2cAKajkNNIQBAAkwHgDk0/+Jk0M7SQ=="
    }
}
```



### 12 revokecredential

Revoke a wallet address credential

POST

```
http://172.168.3.45:8090/api/v1/revokecredentail
```

Request body:

```
{
	"Chain":"ETH",
	"DID":"did:ont:AWbv8ZQ3jYd45qUADrjhYBtshrfRPfwEsT",
	"Address":"0xf63348f9d3dd8f22f5cc05dc02eecea376a9d393",
}
```



Response:

```
{
    "code": 0
}
```
### 13 applyscorecredential

Apply a asset score through a algorithm provider

Oscore service will call the provider url with the schema define parameters, and put the return score inside the credential payload.



POST

```
http://172.168.3.45:8090/api/v1/applyscorecredential
```

Request body:

```
{
    "DID":"did:ont:AWbv8ZQ3jYd45qUADrjhYBtshrfRPfwEsT",
    "ProviderURL":"172.168.3.45:9090/sampleprovider",
    "ProviderDataSchema":"TBD",
    "Assets":[
        {
            "chain":"ETH",
            "coinname":"ETH
        }
    ]
}
```

Response:

```
{
    "code": 0,
    "data":{
        "credential":"XXXXXX"
    }
}
```
### 14 applyuuid
Apply a uuid before login

POST

```
http://172.168.3.45:8090/api/v1/applyuuid
```
Request body:

```
{
    "did":"did:ont:AWbv8ZQ3jYd45qUADrjhYBtshrfRPfwEsT",
}
```

Response:

```
{
    "code": 0,
    "data":{
        "uuid":"XXXXXX"
    }
}
```
### 15 login
Login with uuid and uuid binded account signed uuid signature

POST

```
http://172.168.3.45:8090/api/v1/login
```
Request body:

```
{
    "did":"did:ont:AWbv8ZQ3jYd45qUADrjhYBtshrfRPfwEsT",
    "index":1,
    "sig":"xxxx"
}
```

Response:

```
{
    "code": 0,
    "message":"login succeed"
}
```



## 3、CryptoType 


```
enum {
  bitcoin
  ethereum
}
```

```
toshow {
    "1" : Show
    "0" : No show
}
```

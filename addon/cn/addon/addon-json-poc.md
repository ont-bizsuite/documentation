# Addon json poc

[TOC]

## Addon configuration and deployment

### 1. Configuration docker functions

```
getMeta()

setConfig(version, json)
getConfig()

generateConfig(version, json)

verifyConfig(version, json)

getSdk(version, config, lang)

verifyProtocol(uri)
```

### 2. Addon meta schema and sample

#### 2.1 Addon context

```json
{
    "@context": {
        "addon": "https://store.dev.ont.io/addon/v1/",
        "xsd": "http://www.w3.org/2001/XMLSchema#",
        "info": {
            "@id":"addon:info",
            "@type":"@id",
            "@context": {
                "icon32x32": {
                    "@id":"addon:info#icon32x32",
                    "@type":"xsd:anyURI"
                },
                "icon64x64": {
                    "@id":"addon:info#icon64x64",
                    "@type":"xsd:anyURI"
                },
                "icon128x128": {
                    "@id":"addon:info#icon128x128",
                    "@type":"xsd:anyURI"
                },
                "i18n": {
                    "@id":"addon:info/i18n",
                    "@type":"@id",
                    "@context": {
                        "lang": {
                            "@id":"addon:info/i18n#lang",
                            "@type":"xsd:string"
                        },
                        "name": {
                            "@id":"addon:info/i18n#name",
                            "@type":"xsd:string"
                        },
                        "description": {
                            "@id":"addon:info/i18n#description",
                            "@type":"xsd:string"
                        }
                    }
                },
                "extra": {
                    "@id":"addon:info#extra",
                    "@type":"xsd:anyURI"
                }
            }
        },
        "meta": {
            "@id":"addon:meta",
            "@type":"@id",
            "@context": {
                "version": {
                    "@id":"addon:meta#version",
                    "@type":"xsd:string"
                },
                "dependency": {
                    "@id":"addon:meta#dependency",
                    "@type":"xsd:string"
                },
                "extra": {
                    "@id":"addon:meta#extra",
                    "@type":"xsd:anyURI"
                },
                "config": {
                    "@id":"addon:meta/config",
                    "@type":"@id",
                    "@context": {
                        "step": {
                            "@id":"addon:step"
                        },
                        "migrate_step": {
                            "@id":"addon:migrate_step"
                        },
                        "generate_engine": {
                            "@id":"addon:meta/config/generate_engine",
                            "@type":"@id",
                            "@context": {
                                "method": {
                                    "@id":"addon:meta/config/generate_engine#method",
                                    "@type":"xsd:string"
                                },
                                "uri": {
                                    "@id":"addon:meta/config/generate_engine#uri",
                                    "@type":"xsd:anyURI"
                                }
                            }
                        }
                    }
                },
                "runtime": {
                    "@id":"addon:meta/runtime",
                    "@type":"@id",
                    "@context": {
                        "callback": {
                            "@id":"addon:meta/runtime#callback",
                            "@type":"xsd:anyURI"
                        },
                        "cron": {
                            "@id":"addon:meta/runtime#cron",
                            "@type":"xsd:string"
                        }
                    }
                },
                "sdk": {
                    "@id":"addon:meta/sdk",
                    "@type":"@id",
                    "@context": {
                        "lang": {
                            "@id":"addon:meta/sdk#lang",
                            "@type":"xsd:string"
                        },
                        "api_doc": {
                            "@id":"addon:meta/sdk#api_doc",
                            "@type":"xsd:anyURI"
                        },
                        "resource": {
                            "@id":"addon:meta/sdk#resource",
                            "@type":"xsd:anyURI"
                        }
                    }
                },
                "protocol": {
                    "@id":"addon:meta/protocol",
                    "@type":"@id",
                    "@context": {
                        "doc": {
                            "@id":"addon:meta/protocol#doc",
                            "@type":"xsd:anyURI"
                        },
                        "verifier": {
                            "@id":"addon:meta/protocol#verifier",
                            "@type":"xsd:anyURI"
                        }
                    }
                }
            }
        }
    }
}
```

#### 2.2 Addon configuration step context

多语言稍后扩展。[TBD]

```json
{
    "@context": {
        "addon": "https://store.dev.ont.io/addon/v1/",
        "addonid":"ons://addonid.addon.ont/v1/",
        "xsd": "http://www.w3.org/2001/XMLSchema#",
        "meta":"addon:meta",
        "config": "addon:meta/config",
        "step": {
            "@id":"addon:step",
            "@type":"@id",
            "@context": {
                "idx": {
                    "@id":"addon:step#idx",
                    "@type":"xsd:integer"
                },
                "callback": {
                    "@id":"addon:step/callback",
                    "@type":"xsd:anyURI"
                },
                "param": {
                    "@id":"addon:step/param",
                    "@type":"xsd:string"
                },
                "rollback_of": {
                    "@id":"addon:step/rollback_of",
                    "@type":"xsd:integer"
                },
                "rollbackable": {
                    "@id":"addon:step/rollbackable",
                    "@type":"xsd:boolean"
                },
                "status": {
                    "@id":"addon:step/status",
                    "@type":"xsd:string"
                },
                "description":{
                    "@id":"addon:step/description",
                    "@type":"xsd:string"
                },
                "conf_key1": {
                    "@id":"addonid:conf_key1",
                    "@type":"xsd:string"
                },
                "conf_key2": {
                    "@id":"addonid:conf_key2",
                    "@type":"xsd:string"
                }
            }
        }
    }
}
```

#### 2.3 Addon json

```json
{
    "@id":"ons://addonid.addon.ont",
    "info": {
        "icon32x32": "mime:png:/Axxxx==|url",
        "icon64x64": "mime:png:/Axxxx==|url",
        "icon128x128": "mime:png:/Axxxx==|url",
        "i18n":[
            {
                "lang":"en",
                "name": "name",
                "description": "description"
            },
            {
                "lang":"zh-CN",
                "name": "名字",
                "description": "描述"
            }],
        "extra": "url: 外部资源查看， 比如样例"
    },
    "meta": [
        {
            "version": "version",
            "extra": "url: 外部资源查看， 比如样例",
            "dependency": [
                "addonid:tag(semantic versioner)"],
            "config": {
                "step": [
                    {
                        "idx": 1,
                        "status": "done",
                        "conf_key1":"abc",
                        "conf_key2":"xyz"
                    },
                    {
                        "idx": 2,
                        "callback":"ons://addonid.addon.ont/callback/conf_key1/conf_key2"
                    }],
                "migrate_step": [
                    {
                        "idx": 1,
                        "callback":"ons://addonid.addon.ont/migrate/conf_key1/conf_key2"
                    }],
                "generate_engine": {
                    "uri": "uri",
                    "method": "POST"
                }: 可选。根据配置项生成配置文件，addon store自己有默认的。默认为addon store的。这个方法也可以由 docker 封装，封装的时候不要写
            },
            "runtime":[
                {
                    "callback":"ons://addonid.addon.ont/callback/notify/conf_key2/!$ADDON_HOST$!",
                    "cron":"0,15,30,45 18-06 * * *"
                }],
            "sdk": [
                {
                    "lang": "java",
                    "resource": "docker|url: 根据配置生成对应的sdk， 或者简单下载的sdk。 待扩展。 生成的过程尽量由docker封装， 封装的时候这个字段不需要",
                    "api_doc": "url"
                }]: 不同语种支持， 至少一种,
            "protocol": {
                "doc": "url",
                "verifier": "url: 校验的过程尽量由docker封装， 封装的时候这个字段不需要"
            }: 可选。 没有支持的sdk，根据协议自行开发，开发完成之后可以打开rpc接口去 verifier 校验是否符合协议
        }]
}
```

#### 2.4 Reserved keys

对应 reserved keys 的时候，为 addon store 约定值，协议标准，不得修改。

- 约定，reserved key 以 "!\$" 为开始，"\$!"为结束，界面不得输入；
- 约定，已有变量，以 "!\$" 为开始，"\$!"为结束，界面不得输入，变量值代入。

| Keys        | 备注            |
| ----------- | --------------- |
| RAND        | 随机值          |
| RAND_WALLET |                 |
| RAND_PUBKEY |                 |
| NAME        | 应用名称        |
| HOSTID      | 应用ONT ID      |
| ONS         | 应用绑定 ONS    |
| SESSION     | 当前session用户 |
| NOW         | 当前时间        |
| DAY         | 当前日          |
| ……          |                 |

#### 2.5 Reserved actions

Addon store 提供默认动作，为 addon 自由调用，协议标准，不得修改。

- 约定，reserved action 以 "!#" 为开始，"#!"为结束。

##### 测试网

| Actions|pattern | 备注 |
| ---------------- | ---- | ---------------- |
| qrtestsign      | qrsign/[sc]/[func]/[...param] |配合ONT Auth签名机调用，结果可能为链上交易，可能发生资产转移。交易完成之后允许一次链外应用callback回调|
| testpay | pay/[pattern]/[...param] |作为payer付钱，支持分期、订阅、流支付等模式，代扩展|
| testnotify | notify/[to]?[msg] |通知|
| …… |  ||

##### 主网

| Actions|pattern | 备注 |
| ---------------- | ---- | ---------------- |
| qrsign          | qrsign/[sc]/[func]/[...param] |配合ONT Auth签名机调用，结果可能为链上交易，可能发生资产转移。交易完成之后允许一次链外应用callback回调|
| pay | pay/[pattern]/[...param] |作为payer付钱，支持分期、订阅、流支付等模式，代扩展|
| notify | notify/[to]?[msg] |通知|
| …… |  ||

## 样例

以下 Addon context 略。仅为举例。

### 1. 节点代运营

```json
{
    "@context": {
        "addon": "https://store.dev.ont.io/addon/v1/",
        "triones":"ons://triones.addon.ont/v1/",
        "xsd": "http://www.w3.org/2001/XMLSchema#",
        "meta":"addon:meta",
        "config": "addon:meta/config",
        "step": {
            "@id":"addon:step",
            "@type":"@id",
            "@context": {
                "idx": {
                    "@id":"addon:step#idx",
                    "@type":"xsd:integer"
                },
                "callback": {
                    "@id":"addon:step/callback",
                    "@type":"xsd:anyURI"
                },
                "param": {
                    "@id":"addon:step/param",
                    "@type":"xsd:string"
                },
                "rollback_of": {
                    "@id":"addon:step/rollback_of",
                    "@type":"xsd:integer"
                },
                "rollbackable": {
                    "@id":"addon:step/rollbackable",
                    "@type":"xsd:boolean"
                },
                "status": {
                    "@id":"addon:step/status",
                    "@type":"xsd:string"
                },
                "description":{
                    "@id":"addon:step/description",
                    "@type":"xsd:string"
                },
                "Date":{
                    "@id":"triones:charge_day",
                    "@type":"xsd:integer"
                },
                "Delegate wallet":{
                    "@id":"triones:delegate_wallet",
                    "@type":"xsd:string"
                },
                "Ops pubkey":{
                    "@id":"triones:ops_pubkey",
                    "@type":"xsd:string"
                },
                "Init pos":{
                    "@id":"triones:init_pos",
                    "@type":"xsd:integer"
                }
            }
        },
        "runtime": {
            "@id":"addon:meta/runtime",
            "@type":"@id",
            "@context": {
                "callback": {
                    "@id":"addon:meta/runtime#callback",
                    "@type":"xsd:anyURI"
                },
                "cron": {
                    "@id":"addon:meta/runtime#cron",
                    "@type":"xsd:string"
                }
            }
        }    
    },
    "@id":"ons://triones.addon.ont",
    "info": {
        "icon64x64": "https://node.ont.io/static/img/logo.ba93ed20.png",
        "i18n":[
            {
                "lang":"en",
                "name": "Triones node delegation addon",
                "description": "Ontology Foundation enabled free access for node delegation, any wallet with >=10,000 ONT is able to delegate to Ontology Triones network. Node has to be started as an Ontology Triones node. Ontology Foundation provides maintenance and operating work for node delegation. This addon helps any community members to run a live node with low price (150 ONT per month)."
            }]
    },
    "meta": [
        {
            "version": "0.5.0",
            "extra": "https://node.ont.io",
            "config": {
                "step": [
                    {
                        "idx": 1,
                        "description":"Node delegation requires any \"Delegate Wallet\" with >=10,000 ONT, \"Init Pos\" will be used to delegate to Triones network, 500 ONG will be charged by then. \"Ops Pubkey\" is generated automatically, for common operating.",
                        "Delegate wallet":"Axxxxxx",
                        "Ops pubkey":"!$RAND_PUBKEY$!",
                        "Init pos":10000
                    },
                    {
                        "idx": 2,
                        "description":"This step will generate a transaction to delegate \"Init Pos\" to Triones network, will charge 500 ONG, the node operator is set to \"Ops Pubkey\", all node incentive will go to \"Delegate Wallet\". Please confirm.",
                        "callback":"!#qrsign#!/Axxx/delegate/!$Delegate wallet$!/!$Ops pubkey$!/!$Init pos$!",
                        "rollbackable":true
                    },
                    {
                        "rollback_of": 2,
                        "description":"This will quit node delegation from \"Delegate Wallet\". Please aware enough ONG in  \"Delegate Wallet\". Please confirm.",
                        "callback":"!#qrsign#!/Axxx/withdraw/!$Delegate wallet$!"
                    },
                    {
                        "idx": 3,
                        "description":"Ontology Foundation is about to start your node. The node operating fee is set to 150 ONT per month, and will charge every month. Please scan the qrcode and pay for the first month. Ontology Foundation will notify you every month at \"Date\". Thanks for your corperation.",
                        "Date":"!$DAY$!",
                        "callback":"https://node.ont.io/subscription/!$Delegate Wallet$!",
                        "param":"base64({\"unit\":\"ONT\",\"amount\":150})"
                    },
                    {
                        "idx": 4,
                        "description":"Ontology Foundation is starting your node. Please view the node status report at https://node.ont.io."
                    }]
            },
            "runtime":[
                {
                    "callback":"https://node.ont.io/notify/!$HOSTID$!",
                    "cron":"0 0 !$Date$! * *"
                }]
        }]
}
```



### 2. 存证

```json
{
    "@context": {
        "addon": "https://store.dev.ont.io/addon/v1/",
        "attestation":"ons://attestation.addon.ont/v1/",
        "xsd": "http://www.w3.org/2001/XMLSchema#",
        "meta":"addon:meta",
        "config": "addon:meta/config",
        "step": {
            "@id":"addon:step",
            "@type":"@id",
            "@context": {
                "idx": {
                    "@id":"addon:step#idx",
                    "@type":"xsd:integer"
                },
                "callback": {
                    "@id":"addon:step/callback",
                    "@type":"xsd:anyURI"
                },
                "param": {
                    "@id":"addon:step/param",
                    "@type":"xsd:string"
                },
                "rollback_of": {
                    "@id":"addon:step/rollback_of",
                    "@type":"xsd:integer"
                },
                "rollbackable": {
                    "@id":"addon:step/rollbackable",
                    "@type":"xsd:boolean"
                },
                "status": {
                    "@id":"addon:step/status",
                    "@type":"xsd:string"
                },
                "description":{
                    "@id":"addon:step/description",
                    "@type":"xsd:string"
                },
                "Auth Key":{
                    "@id":"attestation:authkey",
                    "@type":"xsd:string"
                },
                "Execution Id":{
                    "@id":"attestation:execution_id",
                    "@type":"xsd:string"
                },
                "Tenant Id":{
                    "@id":"attestation:tenant_id",
                    "@type":"xsd:string"
                }
            }
        },
        "migrate_step": {
            "@id":"addon:migrate_step",
            "@type":"@id",
            "@context": {
                "idx": {
                    "@id":"addon:step#idx",
                    "@type":"xsd:integer"
                },
                "callback": {
                    "@id":"addon:step/callback",
                    "@type":"xsd:anyURI"
                },
                "param": {
                    "@id":"addon:step/param",
                    "@type":"xsd:string"
                },
                "status": {
                    "@id":"addon:step/status",
                    "@type":"xsd:string"
                },
                "description":{
                    "@id":"addon:step/description",
                    "@type":"xsd:string"
                },
                "Date":{
                    "@id":"attestation:charge_day",
                    "@type":"xsd:integer"
                }            
            } 
        }
    },
    "@id":"ons://attestation.addon.ont",
    "info": {
        "icon64x64": "https://node.ont.io/static/img/logo.ba93ed20.png",
        "i18n":[
            {
                "lang":"en",
                "name": "Ontology attestation addon",
                "description": "This addon enables attestation for any hash (256), with algorithm of merkle tree, and provides full proof any hash added to the tree. This addon will charge upon live attestation gas fee (ONG) per month."
            }]
    },
    "meta": [
        {
            "version": "0.5.0",
            "extra": "https://attestation.ont.io",
            "config": {
                "step": [
                    {
                        "idx": 1,
                        "description":"\"Auth Key\" is a pre-defined auth key from end user (app host), which will be verified by attestation service for any actions, \"Auth Key\" stands for the customer of attestation service, \"Tenant Id\" stands for the attestation service, \"Execution Id\" takes the full responsibility to store attestation proof on-chain.",
                        "Auth Key":"abc",
                        "Execution Id":"!$RAND_WALLET$!",
                        "Tenant Id":"!$HOSTID$!"
                    },
                    {
                        "idx": 2,
                        "description":"Ontology Foundation is about to deploy smart contract for your attestation service.",
                        "callback":"https://attestation.ont.io/test/subscribe/!$Tenant Id$!/!$Execution Id$!",
                        "rollbackable":true
                    },
                    {
                        "rollback_of": 2,
                        "description":"This will cancel attestation service, and all record will be removed from service and Ontology network. Please confirm.",
                        "callback":"!#qrtestsign#!/Axxx/cancel/!$Execution Id$!",
                        "param":"base64({\"callback\":\"https://attestation.ont.io/test/cancel/!$Tenant Id$!\"})"
                    },
                    {
                        "idx": 3,
                        "description":"The attestation service is started. Please view the service at https://attestation.ont.io/test."
                    }],
                "migrate_step": [
                    {
                        "idx": 1,
                        "description":"Ontology Foundation is about to deploy smart contract for your attestation service. The operating fee will charge every month. Ontology Foundation will notify you every month at \"Date\". Thanks for your corperation.",
                        "Date":"!$DAY$!",
                        "callback":"https://attestation.ont.io/subscribe/!$Tenant Id$!/!$Execution Id$!",
                        "rollbackable":true
                    },
                    {
                        "rollback_of": 1,
                        "description":"This will cancel attestation service, and all record will be removed from service and Ontology network. Please confirm.",
                        "callback":"!#qrsign#!/Axxx/cancel/!$Execution Id$!",
                        "param":"base64({\"callback\":\"https://attestation.ont.io/cancel/!$Tenant Id$!\"})"
                    },
                    {
                        "idx": 3,
                        "description":"This step will ensure customer delegate the on-chain access to \"Execution Id\" for attestation. Please scan the qrcode with \"Auth Key\" to confirm.",
                        "callback":"!#qrsign#!/Axxx/assign/!$Auth Key$!/!$Execution Id$!"
                    },
                    {
                        "idx": 4,
                        "description":"The attestation service is started. Please view the service at https://attestation.ont.io."
                    }]
            },
            "runtime":[
                {
                    "callback":"https://attestation.ont.io/notify/!$HOSTID$!",
                    "cron":"0 0 !$Date$! * *"
                }],
            "sdk": [
                {
                    "lang": "java",
                    "resource": "ons://attestation.ont.io/sdk/java",
                    "api_doc": "ons://attestation.ont.io/api"
                }],
            "protocol": {
                "doc": "ons://attestation.ont.io/protocol/doc",
                "verifier": "ons://attestation.ont.io/qa/verify"
            }
        }]
}
```


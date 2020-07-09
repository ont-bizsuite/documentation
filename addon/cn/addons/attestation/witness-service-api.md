## 				Ontology Attestation/Witness Service

### Jsonrpc port

​	By default, `jsonrpc API` listens on `32339` port.

### Jsonrpc request definition

​	Ontology witness client side rpc  interface has been defined as follows：

| Field   | Type     | Description      |
| ------- | -------- | ---------------- |
| jsonrpc | string   | Jsonrpc version  |
| id      | string   | Any random value |
| method  | string   | Method name      |
| params  | rpcParam | Parameters       |

#### Method list

| Field    | Desc                |
| -------- | ------------------- |
| batchAdd | add hash  to server |
| verify   | verify hash         |

#### sample batchAdd request

```json
{
 	"jsonrpc": "2.0",
  "id": "1",
  "method": "batchAdd",
  "params": {
    "pubKey": "0360a7124f13c41896f9be38a44d13a523d4fb75a41bfcc998d7d046080cc04140",
    "signature": "38d2d7e2d8fade8d45a914a29a80f58748dfd911601eb9c5f433e0e924a935cae7424b0c48754f68736b850c6753632bbd67a270ba5e7f7b34abbf13dba5a0a3",
    "hashes": ["8855508aade16ec573d21e6a485dfd0a7624085c1a14b5ecdd6485de0c6839a4"]
  }
}
```

- pubKey:  the public key of users.
- hashes: the hash hex string  array ready to be added. 
- signature:  use the private key to sign the first element of hashes. that is sign the hashes[0] element.

#### sample batchAdd response

| Field  | Data type   | Description                                                  |
| ------ | ----------- | ------------------------------------------------------------ |
| id     | string      | Same id with request                                         |
| error  | integer     | Error code                                                   |
| desc   | string      | Response Description                                         |
| result | interface{} | if batchadd err is duplicate. it's array of hashes which is duplicate. then this is a string message. |

##### failed batchAdd response sample

```json
{
  "desc": "ADDHASH_FAILED: duplicate hash leafs.",
  "error": 41002,
  "id": "1",
  "jsonrpc": "2.0",
  "result":["8855508aade16ec573d21e6a485dfd0a7624085c1a14b5ecdd6485de0c6839a4","86f9649499b0080656c014aa244f654864bad4145c8513e9c8409f437d4a2b3b"]
}
```

##### success batchAdd response sample

```json
{
  "desc": "SUCCESS",
  "error": 0,
  "id": "1",
  "jsonrpc": "2.0",
  "result": "Cached Success"
}
```

#### sample of verify request

```json
{
  "jsonrpc": "2.0",
  "id": "1",
  "method": "verify",
  "params": {
    "pubKey": "0360a7124f13c41896f9be38a44d13a523d4fb75a41bfcc998d7d046080cc04140",
    "signature": "",
    "hashes": ["8855508aade16ec573d21e6a485dfd0a7624085c1a14b5ecdd6485de0c6839a4"]
  }
}
```

- pubKey:  the public key of users.
- hashes: the hash hex string to be veified.
- signature: ignore with empty string. 

##### verify response 

| Field  | Data type    | Description                  |
| ------ | ------------ | ---------------------------- |
| id     | string       | Same id with request         |
| error  | integer      | Error code                   |
| desc   | string       | Response Description         |
| result | VerifyResult | Execution Result Description |

##### failed verify respone

```json
{
  "desc": "VERIFY_FAILED",
  "error": 41003,
  "id": "505",
  "jsonrpc": "2.0",
  "result": null
}
```

##### success verify response

```json
{
  "desc": "SUCCESS",
  "error": 0,
  "id": "500",
  "jsonrpc": "2.0",
  "result": {
    "root": "5b83e9940639c9de53c656f64c6ef938be654c8bf0ac5d8601e3d5753ed79fe0",
    "size": 496,
    "blockheight": 2,
    "index": 4,
    "proof": ["aba27d4d5bc85e19d4e4a1f9c3fae9695a4af5b343c0d9ccf020f19010dc2504", "256b34c202dad7e5e59741ed4639aa22e720c02d07701be9467110728c987441", "23514df63f246deb32461ecf083da8f1af9ca194ec5184ee56e6ec41b585266c", "c27f92780d9aad92fc17dab715ae54d25e46dbe08b242ef3cf6a819a9051e75d", "1256c62c6c834d4001e97155eb65cfaa4342fe9e5fc9872ec97b99eef581ad8f", "0ba93e973d5f02b268a3474e566c23b995660978017b3cc8e7df712722376524", "83c68db78032f5604cb6683f4e2a0092f758a39733ed45b2b1040f239d49a822", "8892b436647f9ebbdf719c91eedd86a16db2ef52710685480652133ca90fb8d3"]
  }
}
```

#### Error codes

| Field | Data type | Description     |
| ----- | --------- | --------------- |
| 0     | int64     | SUCCESS         |
| 41001 | int64     | INVALID_PARAM   |
| 41002 | int64     | ADDHASH_FAILED  |
| 41003 | int64     | VERIFY_FAILED   |
| 41004 | int64     | NODE_OUTSERVICE |
| 41005 | int64     | NO_AUTH         |

#### Others

max hashes number 2^32
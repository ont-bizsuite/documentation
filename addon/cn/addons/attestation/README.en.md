## Overview

![overview](./res/overview.png)

|On chain contract | Attestation service | Addon client (source) | Client        |
| ----------------------------------------------- | -------------------------------- | -------------- | ------------------ |
| Contract                                 | Add attestation record and proof query | Record detail | Attestation and query |
| * batch add, hash only<br/>* State DB store merkle root | * Add attestation record | * data source | * Add record |
| * Verify merkle root        | * generate full proof path for certain record |                | * verify |
|                                                 | * verify based on data source |                |                    |

View [service api](./witness-service-api.md).

## Workflow

### 1. add record

``` flow
st=>start: Start
req=>operation: [client] add fingerprint record request
getsrc=>operation: [source] get data source
serial=>operation: [source] serialize data source and generate fingerprint
attestation=>operation: [service] add fingerprint attestation record
attestation-sc=>operation: [smart contract] add record on chain
res=>operation: [source] return on chain record and proof
e=>end
st->req->getsrc->serial->attestation->attestation-sc->res->e
```

### 2. verify

``` flow
st=>start: Start
req=>operation: [client] fingerprint verification request
getsrc=>operation: [source] get data source
serial=>operation: [source] serialize data source and generate fingerprint, compare
versource=>operation: [source] verify service is authorized
checkversource=>condition: authorized？
versmartcontract=>operation: [smartcontract] verify source and service is authorized
checkversmartcontract=>condition: authorized？
getproof=>operation: [service] get proof of full merkle root path 
checkproof=>condition: get the full path proof？
verpath=>operation: [service call/client api] merkle tree proof verification
checkpath=>condition: verification failed?
getchaininfo=>operation: [smartcontract] get merkle root, blockheight and transaction from smartcontract
checkchaininfo=>condition: verify merkle root is on chain, fingerprint is in transaction?
resyes=>operation: [client] verification succeed
resno=>operation: [client] verification failed
e=>end
st->req->getsrc->serial->versource->checkversource
checkversource(yes)->versmartcontract->checkversmartcontract
checkversource(no)->resno->e
checkversmartcontract(yes)->getproof->checkproof
checkversmartcontract(no)->resno->e
checkproof(yes)->verpath->checkpath
checkproof(no)->resno->e
checkpath(yes)->getchaininfo->checkchaininfo
checkpath(no)->resno->e
checkchaininfo(yes)->resyes->e
checkchaininfo(no)->resno->e
```

[A sample flow](./verify-flow.md)

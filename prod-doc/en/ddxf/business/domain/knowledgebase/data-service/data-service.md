## common

```
verifyToken(token) boolean

useToken(token) (err, txhash)

/ddxf/seller/useToken

createToken(meta) (token, txhash)

removeToken(token) txhash

updateToken(token, meta) txhash

get(token) meta
```

## data service access

```
useToken(token, ...resource) err
```

## data service update

```
useToken(token, ...resource) (err, ...updated_resource)
```

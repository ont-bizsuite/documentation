## common

```
verifyToken(token) boolean

/ddxf/dtoken/verify

useToken(token) (err, txhash)

/ddxf/dtoken/use

createToken(meta) (token, txhash)

/ddxf/dtoken/create

removeTokenTemplate(token) txhash

/ddxf/dtoken/remove_template

updateTokenTemplate(token, meta) txhash

/ddxf/dtoken/update_template

get(token) meta

/ddxf/dtoken/get
```

## data service access

```
useToken(token, ...resource) err
```

## data service update

```
useToken(token, ...resource) (err, ...updated_resource)
```

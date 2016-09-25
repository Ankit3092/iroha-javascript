# いろはjs(irohajs)  

## What's いろは(iroha)?  
いろは(iroha) is [this](https://github.com/soramitsu/iroha).

## Description  
いろはjs(irohajs) is client javascript library for using いろは(iroha).  
[demo]()

## Requirement  
* [js-sha3](https://github.com/emn178/js-sha3)
* [superagent](https://github.com/visionmedia/superagent)
* [supercop.js(GUCCI-swallow)](https://github.com/GUCCI-swallow/supercop.js)

## Installation  
*  Clone this repository.
*  [Download the latest reelase]().
*  [Feature]Install with npm/bower.

## Usage
### Load

```html
<script src="/path/to/iroha.js"></script>
```

### API
#### iroha.createKeyPair

```js
var keys = iroha.createKeyPair();
```



Return key object. Keys are used other API.  
**keys**:

```js
//keys
{
	publicKey: A 32 byte public key encoded base64,
	privateKey: A 64 byte private key encoded base64
}
```

#### iroha.registAccount

```js
var res = iroha.registAccount({
				accessPoint: ip address or url,
				name: account name,
				publicKey: public key(base64)
			});
```

Return いろは(iroha) response object.  
**Response**:
Success:
```json
{
  "message": response message,
  "status": response code,
  "uuid": uuid(sha3)
}

```

Duplicate:
```json

{
  "status": 400,
  "message": "duplicate user"
}
```

#### iroha.getAccountInfo

```js
var res = iroha.getAccountInfo({
				accessPoint: ip address or url,
 				uuid: uuid(sha3)
			});
```

Return いろは(iroha) response object.  
**Response**:
Success:
```json

{
  "status": status code,
  "alias": alias
```

User not found:
```json

{
  "message": "User not found!",
  "status": 400
}
```


#### iroha.registDomain

```js
var res = iroha.registDomain({
				accessPoint: ip address or url,
 				domainName: domain name,
 				ownerPublicKey: owner public key(base64),
 				ownerPrivateKey: owner private Key(base64)
			});
```

Return いろは(iroha) response object.  
**Response**:
Success:
```json
{
  "status": 200,
  "message": "Domain registered successfully."
}
```

#### iroha.getDomainList

```js
var res = iroha.getDomainList(uuid(sha3));
```

Return いろは(iroha) response object.  
**Response**:
Success:
```json

[
    {
      "domain" : domain name,
      "creator" : "base64_public_key",
      "signature" : "b64encoded?_signature",
      "creationDate" : unixtime
    },
    {
      "domain" : domain name,
      "creator" : "base64_public_key",
      "signature" : "b64encoded?_signature",
      "creationDate" : unixtime
    }, ...
]
```



#### iroha.createAsset

```js
var res = iroha.createAsset({
 				accessPoint: ip address or url,
 				assetName: asset name,
 				domainName: domain name,
				creatorPublicKey: creator public key(base64),
 				creatorPrivateKey: creator private key(base64)
			});
```

Return いろは(iroha) response object.  
**Response**:
Success:
```json
{
  "status": 200,
  "message": "Asset created successfully."
}
```


#### iroha.operateAsset

```js
var res = iroha.operateAsset({
				accessPoint: ip address or url,
 				assetUuid: asset uuid(sha3),
 				command: operation command,
 				amount: amount,
 				senderPublicKey: sender public key(base64),
 				senderPrivateKey: sender private key(base64),
 				receiverPublicKey: receiver public key(base64)
			});
```

Return いろは(iroha) response object.  
**Response**:
Success:
```json
{
  "status": 200,
  "message": "Asset 'command' successfully."
}
```

#### iroha.getAssetList

```js
var res = iroha.getAssetList({
				 accessPoint: ip address or url,
 				 domainName: domain name
			});
```

Return いろは(iroha) response object.  
**Response**:
Success:
```json
[

    {
      "name" : asset name,
      "creator" : "base64_public_key",
      "signature" : "b64encoded?_signature",
      "creationDate" : unixtime
    },
    {
      "name" : asset name,
      "creator" : "base64_public_key",
      "signature" : "b64encoded?_signature",
      "creationDate" : unixtime
    }, ...
]

```

#### iroha.getAssetTransaction

```js
var res = iroha.getAssetTransaction({
 				accessPoint: ip address or url,
 				domainName: domain name,
 				assetName: asset name
			});
```

Return いろは(iroha) response object.  
**Response**:
Success:
```json
{
  "uuid":"sha3",
  "timestamp": unixtime,
  "history":[
    {
      "params":{
        "sender" : "pubkey",
        "amount" : amount
      }
    },
    {
      "asset-uuid":"sha3",
      "params":{
        "sender" : "pubkey",
        "amount" : amount
      }
    }, ...
  ]
}
```


#### iroha.getUserTransaction

```js
var res = iroha.getUserTransaction({
				accessPoint: ip address or url,
 				uuid: user uuid(sha3)
			});
```

Return いろは(iroha) response object.  
**Response**:
Success:
```json

{
  "uuid" : "user's_uuid",
  "timestamp" : unixtime,
  "history" : [
    {
      "asset-uuid":"sha3",
      "params":{
        "sender" : "pubkey",
        "amount" : amount
      }
    },
    {
      "asset-uuid":"sha3",
      "params":{
        "sender" : "pubkey",
        "amount" : amount
      }
    }, ...
  ]
}

```


## Author  
[GUCCI-swallow](https://github.com/GUCCI-swallow)

## License

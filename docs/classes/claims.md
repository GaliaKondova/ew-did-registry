[@ew-did-registry/claims](../README.md) › [Globals](../globals.md) › [Claims](claims.md)

# Class: Claims

**`class`** 
Base class for extending by other claims classes

## Hierarchy

* **Claims**

  ↳ [ClaimsUser](claimsuser.md)

  ↳ [ClaimsIssuer](claimsissuer.md)

  ↳ [ClaimsVerifier](claimsverifier.md)

## Implements

* [IClaims](../interfaces/iclaims.md)

## Index

### Constructors

* [constructor](claims.md#constructor)

### Properties

* [did](claims.md#did)
* [jwt](claims.md#jwt)
* [keys](claims.md#keys)

### Methods

* [getDocument](claims.md#getdocument)
* [verifySignature](claims.md#verifysignature)

## Constructors

###  constructor

\+ **new Claims**(`keys`: IKeys, `resolver`: IResolver): *[Claims](claims.md)*

Defined in claims/src/claims/claims.ts:28

**`constructor`** 

**Parameters:**

Name | Type | Description |
------ | ------ | ------ |
`keys` | IKeys | user key pair |
`resolver` | IResolver |   |

**Returns:** *[Claims](claims.md)*

## Properties

###  did

• **did**: *string*

*Implementation of [IClaims](../interfaces/iclaims.md).[did](../interfaces/iclaims.md#did)*

Defined in claims/src/claims/claims.ts:28

___

###  jwt

• **jwt**: *IJWT*

Defined in claims/src/claims/claims.ts:21

jwt stores the JWT to manage web tokens

___

###  keys

• **keys**: *IKeys*

*Implementation of [IClaims](../interfaces/iclaims.md).[keys](../interfaces/iclaims.md#keys)*

Defined in claims/src/claims/claims.ts:26

Key pair represents the implementation of key management interface

## Methods

###  getDocument

▸ **getDocument**(`did`: string): *Promise‹IDIDDocument›*

Defined in claims/src/claims/claims.ts:59

Fetches DID document of the corresponding DID

**`example`** 
```typescript
import { Keys } from '@ew-did-registry/keys';
import { Claims } from '@ew-did-registry/claims';

const user = new Keys();
const claims = new Claims(user);
const did = `did:${Networks.Ethereum}:user_id`;
const document = await claims.getDocument(did);
```

**Parameters:**

Name | Type |
------ | ------ |
`did` | string |

**Returns:** *Promise‹IDIDDocument›*

___

###  verifySignature

▸ **verifySignature**(`token`: string, `signer`: string): *Promise‹boolean›*

Defined in claims/src/claims/claims.ts:81

Verifies signers signature on received token

**`example`** 
```typescript
import { Keys } from '@ew-did-registry/keys';
import { Claims } from '@ew-did-registry/claims';

const user = new Keys();
const claims = new Claims(user);
const verified = claims.verifySignature(token, userDid);
```

**Parameters:**

Name | Type | Description |
------ | ------ | ------ |
`token` | string | token signature on which you want to check |
`signer` | string | did of the signer  |

**Returns:** *Promise‹boolean›*
[@ew-did-registry/claims](../README.md) › [Globals](../globals.md) › [ClaimsVerifier](claimsverifier.md)

# Class: ClaimsVerifier

## Hierarchy

* [Claims](claims.md)

  ↳ **ClaimsVerifier**

## Implements

* [IClaims](../interfaces/iclaims.md)
* [IClaimsVerifier](../interfaces/iclaimsverifier.md)

## Index

### Constructors

* [constructor](claimsverifier.md#constructor)

### Properties

* [did](claimsverifier.md#did)
* [jwt](claimsverifier.md#jwt)
* [keys](claimsverifier.md#keys)

### Methods

* [getDocument](claimsverifier.md#getdocument)
* [verifyPrivateProof](claimsverifier.md#verifyprivateproof)
* [verifyPublicProof](claimsverifier.md#verifypublicproof)
* [verifySignature](claimsverifier.md#verifysignature)

## Constructors

###  constructor

\+ **new ClaimsVerifier**(`keys`: IKeys, `resolver`: IResolver): *[ClaimsVerifier](claimsverifier.md)*

*Inherited from [Claims](claims.md).[constructor](claims.md#constructor)*

Defined in claims/src/claims/claims.ts:28

**`constructor`** 

**Parameters:**

Name | Type | Description |
------ | ------ | ------ |
`keys` | IKeys | user key pair |
`resolver` | IResolver |   |

**Returns:** *[ClaimsVerifier](claimsverifier.md)*

## Properties

###  did

• **did**: *string*

*Implementation of [IClaims](../interfaces/iclaims.md).[did](../interfaces/iclaims.md#did)*

*Inherited from [Claims](claims.md).[did](claims.md#did)*

Defined in claims/src/claims/claims.ts:28

___

###  jwt

• **jwt**: *IJWT*

*Inherited from [Claims](claims.md).[jwt](claims.md#jwt)*

Defined in claims/src/claims/claims.ts:21

jwt stores the JWT to manage web tokens

___

###  keys

• **keys**: *IKeys*

*Implementation of [IClaims](../interfaces/iclaims.md).[keys](../interfaces/iclaims.md#keys)*

*Inherited from [Claims](claims.md).[keys](claims.md#keys)*

Defined in claims/src/claims/claims.ts:26

Key pair represents the implementation of key management interface

## Methods

###  getDocument

▸ **getDocument**(`did`: string): *Promise‹IDIDDocument›*

*Inherited from [Claims](claims.md).[getDocument](claims.md#getdocument)*

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

###  verifyPrivateProof

▸ **verifyPrivateProof**(`proofToken`: string, `privateToken`: string): *Promise‹boolean›*

*Implementation of [IClaimsVerifier](../interfaces/iclaimsverifier.md)*

Defined in claims/src/claimsVerifier/claimsVerifier.ts:50

Checks issuer signature on issued token and user signature on proof token
and verifies that proof and private data mathches to each other

**`example`** 
```typescript
import { ClaimsVerifier } from '@ew-did-registry/claims';
import { Keys } from '@ew-did-registry/keys';

const keys = new Keys();
const claims = new ClaimsVerifier(verifier);
const verified = claims.verifyPrivateProof(proofToken, privateToken);
```

**Parameters:**

Name | Type | Description |
------ | ------ | ------ |
`proofToken` | string | contains proof data |
`privateToken` | string | contains private data |

**Returns:** *Promise‹boolean›*

whether the proof was succesfull

___

###  verifyPublicProof

▸ **verifyPublicProof**(`token`: string): *Promise‹boolean›*

*Implementation of [IClaimsVerifier](../interfaces/iclaimsverifier.md)*

Defined in claims/src/claimsVerifier/claimsVerifier.ts:26

Checks issuer signature on token

**`example`** 
```typescript
import { ClaimsVerifier } from '@ew-did-registry/claims';
import { Keys } from '@ew-did-registry/keys';

const keys = new Keys();
const claims = new ClaimsVerifier(verifier);
const verified = claims.verifyPublicProof(issuedToken);
```

**Parameters:**

Name | Type | Description |
------ | ------ | ------ |
`token` | string | containing proof data |

**Returns:** *Promise‹boolean›*

whether the proof was succesfull

___

###  verifySignature

▸ **verifySignature**(`token`: string, `signer`: string): *Promise‹boolean›*

*Inherited from [Claims](claims.md).[verifySignature](claims.md#verifysignature)*

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
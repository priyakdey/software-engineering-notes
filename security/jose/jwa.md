# JSON Web Algorithms (JWA)

[RFC 7518](https://www.rfc-editor.org/rfc/rfc7518.html)

This specification registers the cryptographic algorithms and identifiers to be used in [JSON Web Signing](./jws.md), [JSON Web Encryption](./jwe.md) and [JSON Web Key](./jwk.md). 

##  Cryptographic Algorithms for Digital Signatures and MACs

The algorithms used for signing messages - Message Authentication Codes. It helps determine the authenticity and integrity of messages across systems. JWS uses one of these algorithms to digitally sign/create a MAC of the contents of the JWS header and payload.

## [Header Values for the algorithms](https://www.rfc-editor.org/rfc/rfc7518.html#section-3.1)
   
| "alg" Param Value |       Digital Signature of MAC algorithm       | Implementation Requirements |
| :---------------: | :--------------------------------------------: | :-------------------------: |
|       HS256       |               HMAC using SHA-256               |          Required           |
|       HS384       |               HMAC using SHA-384               |          Optional           |
|       HS512       |               HMAC using SHA-512               |          Optional           |
|       RS256       |         RSASSA-PKCS1-v1_5 usingSHA-256         |         Recommended         |
|       RS384       |        RSASSA-PKCS1-v1_5 using SHA-384         |          Optional           |
|       RS512       |        RSASSA-PKCS1-v1_5 using SHA-512         |          Optional           |
|       ES256       |         ECDSA using P-256 and SHA-256          |        Recommended+         |
|       ES384       |         ECDSA using P-384 and SHA-384          |          Optional           |
|       ES512       |         ECDSA using P-521 and SHA-512          |          Optional           |
|       PS256       | RSASSA-PSS using SHA-256 and MGF1 with SHA-256 |          Optional           |
|       PS384       | RSASSA-PSS using SHA-384 and MGF1 with SHA-384 |          Optional           |
|       PS512       | RSASSA-PSS using SHA-512 and MGF1 with SHA-512 |          Optional           |
|       none        |     No digital signature or MAC performed      |          Optional           |

## [HMAC : Keyed-Hashing for Message Authentication Code](https://www.rfc-editor.org/rfc/rfc2104)

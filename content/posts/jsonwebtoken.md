---
author: Nekilc
title: JsonWebToken(JWT)
date: 2023-05-16
---

## Introduce

## Format

`header`.`claims`.`signature`

## Header
- typ(Type): JWT 
- cty(Content Type): Indicate the encryption method when nesting encryption.
- alg(Algorithm): JWT Signature Algorithm, HS256,RS256,ECDSA,EDDSA etc.

## Claim
- exp Expire time
- iat Issued At
- iss Issue
- sub Subject
- aud Audience
- nbf Not before
- jti JWT ID


# Reference

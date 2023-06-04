---
author: Nekilc
title: Generate EdDSA/Ed25519 key-pair by OpenSSL
date: 2023-05-16
---

## Introduce
http://ed25519.cr.yp.to/index.html

## Generate private
`openssl genpkey -algorithm ed25519 -out private.key `

## Generate public from private
`openssl pkey -in private.key -pubout -out public.pub`

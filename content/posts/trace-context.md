---
author: Nekilc
title: Trace context in HTTP response
date: 2021-01-04
tags: [http,backend]
---

## Header: traceparent

### Format

`format   = version "-" trace-id "-" parent-id "-" trace-flags`

    version          = 00
    trace-id         = 32HEXDIGLC  ; 16 bytes array identifier. All zeroes forbidden
    parent-id        = 16HEXDIGLC  ; 8 bytes array identifier. All zeroes forbidden
    trace-flags      = 2HEXDIGLC   ; 8 bit flags. Currently, only one bit is used. See below for details

## Header: tracestate

### Format

`key1=value1,key2=value2`

Key:

    key = simple-key / multi-tenant-key
    simple-key = lcalpha 0*255( lcalpha / DIGIT / "_" / "-"/ "*" / "/" )
    multi-tenant-key = tenant-id "@" system-id
    tenant-id = ( lcalpha / DIGIT ) 0*240( lcalpha / DIGIT / "_" / "-"/ "*" / "/" )
    system-id = lcalpha 0*13( lcalpha / DIGIT / "_" / "-"/ "*" / "/" )
    lcalpha    = %x61-7A ; a-z

Value:

    value    = 0*255(chr) nblk-chr
    nblk-chr = %x21-2B / %x2D-3C / %x3E-7E
    chr      = %x20 / nblk-chr

## Reference

https://www.w3.org/TR/trace-context/#traceparent-header
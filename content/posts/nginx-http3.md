---
author: Nekilc
title: Nginx enable HTTP/3 
date: 2023-5-25
tags: [http,http3,backend,nginx]
---

Nginx released version 1.25.0 on May 23, 2023 to provide HTTP/3 experimental support.

## Example

```conf
http{
    include       mime.types;
    default_type  application/octet-stream;

    server{
        server_name api.hikit.io;

        listen [::]:443 quic reuseport ipv6only=off;
        listen [::]:443 ssl http2 ipv6only=off;

        http3 on;
        quic_gso on;
        quic_retry on;

        ssl_early_data on;
        ssl_protocols TLSv1.3;
        ssl_certificate  /app/api.hikit.io.pem;
        ssl_certificate_key /app/api.hikit.io.key;

        add_header alt-svc 'h3=":443"; ma=86400';
        add_header QUIC-Status $http3;
    }
}
```

## Directives

### Enables HTTP/3 protocol negotiation.
    Syntax:	    http3 on | off;
    Default:	http3 on;
    Context:	http, server

### Enables HTTP/0.9 protocol negotiation used in QUIC interoperability tests.
    Syntax:	    http3_hq on | off;
    Default:	http3_hq off;
    Context:	http, server

### Sets the maximum number of concurrent HTTP/3 request streams in a connection.
    Syntax:	    http3_max_concurrent_streams number;
    Default:	http3_max_concurrent_streams 128;
    Context:	http, server

### Sets the size of the buffer used for reading and writing of the QUIC streams.
    Syntax:	    http3_stream_buffer_size size;
    Default:    http3_stream_buffer_size 64k;
    Context:	http, server

### Sets the QUIC active_connection_id_limit transport parameter value

This is the maximum number of client connection IDs which can be stored on the server.

    Syntax:	    quic_active_connection_id_limit number;
    Default:    quic_active_connection_id_limit 2;
    Context:	http, server

### Enables routing of QUIC packets using eBPF.

When enabled, this allows supporting QUIC connection migration.

`The directive is only supported on Linux 5.7+.`

    Syntax:	    quic_bpf on | off;
    Default:    quic_bpf off;
    Context:	main
 


### Enables sending in optimized batch mode using segmentation offloading.

`Optimized sending is supported only on Linux featuring UDP_SEGMENT.`

    Syntax:	    quic_gso on | off;
    Default:    quic_gso off;
    Context:	http, server

### Sets a file with the secret key used to encrypt stateless reset and address validation tokens

By default, a random key is generated on each reload. Tokens generated with old keys are not accepted.

    Syntax:	    quic_host_key file;
    Default:	—
    Context:	http, server

### Enables the QUIC Address Validation feature.

This includes sending a new token in a Retry packet or a NEW_TOKEN frame and validating a token received in the Initial packet.

    Syntax:	    quic_retry on | off;
    Default:	quic_retry off;
    Context:	http, server

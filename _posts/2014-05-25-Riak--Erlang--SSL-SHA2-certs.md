---
layout: post
title: Riak + Erlang + SSL SHA2 certs
summary:
status: draft
hn-discussion:
comments: true
---

I recently spent some time trying to install Riak 1.4.8-1 (to use with datomic)
on Ubuntu 12.04 64-bit.  Everything was working pretty well as I followed the
install guide until I tried to install my own SSL certificate signed by
StartSSL.  

Here is the error I got when trying ```curl -v https://127.0.0.1:8069/riak/test```

```
* About to connect() to 127.0.0.1 port 8069 (#0)
*   Trying 127.0.0.1... connected
* successfully set certificate verify locations:
*   CAfile: none
  CApath: /etc/ssl/certs
* SSLv3, TLS handshake, Client hello (1):
* Unknown SSL protocol error in connection to 127.0.0.1:8069
* Closing connection #0
curl: (35) Unknown SSL protocol error in connection to 127.0.0.1:8069
```

I found an IRC transcript that highlighted several key points:

* Riak comes with Erlang R15B01
* Support for SHA2 wasn't added until R15B02

My current solution is to generate SHA-1 certs until I can figure out a cleaner way
to run a different version of erlang without needing to install riak from
source.

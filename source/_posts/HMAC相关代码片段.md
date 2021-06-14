---
title: HMAC相关代码片段
date: 2021-06-13 15:36
categories: 
  - Cryptography
  - Snippet
tags: 
  - Cryptography
  - Snippet
  - Python
  - Javascript
---
## 各语言的实现

### Javascript

``` bash
async function get_timestamp_sign(secret) {
    async function hmac_sha256_b64(secret, data) {
        const encoder = new TextEncoder()
        const key = await crypto.subtle.importKey(
            "raw",
            encoder.encode(secret),
            { name: "HMAC", hash: "SHA-256" },
            false,
            ["sign"],
        )
        const mac = await crypto.subtle.sign("HMAC", key, encoder.encode(data))
        return encodeURIComponent(btoa(String.fromCharCode(...new Uint8Array(mac))))
    }
    let timestamp = Date.now()
    return {
        sign: await hmac_sha256_b64(secret, `${timestamp}\n${secret}`),
        timestamp: timestamp
    }
}
```

### Python

``` bash
import time
import hmac
import hashlib
import base64
from urllib.parse import quote_plus

def hmac_sha256_b64(key, data):
    def hmac_sha256_64(key, data):
        return hmac.new(
            key.encode(), 
            data.encode(), 
            digestmod=hashlib.sha256
        ).digest()
    def quote_base64_encode(bytecode):
        return quote_plus(base64.b64encode(bytecode))
    return quote_base64_encode(hmac_sha256_64(key, data))

def get_timestamp_sign(secret):
    timestamp = str(round(time.time()*1000))
    sign = hmac_sha256_b64(secret, f'{timestamp}\n{secret}')
    return dict(timestamp=timestamp,sign=sign)
```


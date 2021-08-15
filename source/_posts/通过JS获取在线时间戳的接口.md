---
title: 通过JS获取在线时间戳的接口
date: 2021-08-15 10:56
categories: 
  - Snippet
tags: 
  - Snippet
  - Vue
  - Javascript
  - Time
---
### 通过taobao API获取网络时间

```vue
import fetch from "node-fetch"

async function getTimestampFromApi() {
    let resp = await fetch(
        "http://api.m.taobao.com/resty/api3.do?api=mtop.common.getTimestamp",
        {
            method: "GET"
        }
    )
    return parseInt((await resp.json()).data.t)
}

async function getTimestamp() {
    return getTimestampFromApi()
}

export default {
    getTimestamp
}

```


---
title: Python发送Post请求时移除Content-Type.md
date: 2021-08-17 09:30
categories:
  - HTTP
tags:
  - Python
  - HTTP
---

## 实现
使用Python3的环境，代码如下
```python
try:
    from urllib.request import Request, urlopen, build_opener, BaseHandler
except ImportError:
    from urllib2 import Request, urlopen, build_opener, BaseHandler

# 移除ContentType
class ContentTypeRemover(BaseHandler):
    def http_request(self, req):
        if req.has_header('Content-type'):
            req.remove_header('Content-type')
        return req
    https_request = http_request

def main():
	url = 'https://httpbin.org/post'
	body = 'aaaa=1&bbbb=2&ccc=3'
	headers = {
		'user-agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/92.0.4515.131 Safari/537.36 Edg/92.0.902.73',
		'content-type': 'application/json' # 测试效果
	}
	opener = build_opener(ContentTypeRemover())
	req = Request(url, data=body.encode(), headers=headers)
	text = opener.open(req).read().decode()
	print(text)

if __name__ == '__main__':
	main()

```

## 输出

```
{
  "args": {}, 
  "data": "aaaa=1&bbbb=2&ccc=3", 
  "files": {}, 
  "form": {}, 
  "headers": {
    "Accept-Encoding": "identity", 
    "Content-Length": "19", 
    "Host": "httpbin.org", 
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/92.0.4515.131 Safari/537.36 Edg/92.0.902.73", 
    "X-Amzn-Trace-Id": "Root=1-611b1bc3-4647055177ea24302edc33ea"
  }, 
  "json": null, 
  "origin": "{ip}", 
  "url": "https://httpbin.org/post"
}
```

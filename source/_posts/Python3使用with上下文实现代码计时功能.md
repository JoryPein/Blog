---
title: Python3使用with上下文实现代码计时功能
date: 2021-06-14 12:29
categories: 
  - Snippet
tags: 
  - Snippet
  - Python
  - Context
  - Time
---
### Python

``` python
import time

class timer():

    def __init__(self, name):
        self.name = name
        self.start = 0

    def __enter__(self):
        self.start = time.time()
        return self

    def __exit__(self, *args):
        print(f'[{self.name}] done in {round(time.time() - self.start, 3)} seconds')


def task():
    print('Task is starting')
    time.sleep(2)
    print('Task was finished')


if __name__ == '__main__':
    with timer('Task'):
        task()

```

输出：

```
Task is starting
Task was finished
[Task] done in 2.009 seconds
```


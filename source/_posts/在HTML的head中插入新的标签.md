---
title: 在HTML的head中插入新的标签
date: 2021-07-04 13:00
categories: 
  - Snippet
tags: 
  - HTML
  - Javascript
---

## 实现如下

``` javascript
function addHtmlTag(htmlTag){
  var position = document.getElementsByTagName('head')[0];
  var matchGroup = htmlTag.match(/<(\w+)\s(.*?)>(.*?)?(<)?/);
  if (matchGroup[1]){
    var tagName = matchGroup[1];
    var attrs = matchGroup[2].split(" ");
    var tag = document.createElement(tagName);
    for(var i=0;i<attrs.length;i++){
        var pair = attrs[i].split("=");
        tag[pair[0]] = pair[1].replace(/^"|"$/g, '');
    }
    position.appendChild(tag);
  }
}

addHtmlTag('<script src="https://code.jquery.com/jquery-1.11.3.min.js"></script>')
addHtmlTag('<link rel="icon" href="favicon.ico">')
```

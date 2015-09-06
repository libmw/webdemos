---
  layout: api
  title: http
---

## http缓存


#### 协议参考 <http://blog.csdn.net/gueter/article/details/1524447>
## Ajax

在ie里使用ajax的get请求，如果服务器没有返回no-cache，则会缓存请求。也就是说每次请求的内容都是一样的，不管服务器更新没更新。

所以使用$.get或者$.getJSON都需要加上 `_t = (+ new Date())` 参数


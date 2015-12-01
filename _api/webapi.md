---
  layout: api
  title: webapi
---


## Ajax

在ie里使用ajax的get请求，如果服务器没有返回no-cache，则会缓存请求。也就是说每次请求的内容都是一样的，不管服务器更新没更新。

所以使用$.get或者$.getJSON都需要加上 `_t = (+ new Date())` 参数

## Fetch

Fetch提供了比xhr更优雅的获取资源的方式。<http://www.w3ctech.com/topic/854>

## Service Worker

Service Worker可以把静态文件缓存在本地，可以监控本域发起的各种请求，提高访问速度，使网站支持离线访问。

[Service Worker 入门](http://www.w3ctech.com/topic/866)


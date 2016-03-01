---
  layout: api
  title: JavaScript标准
---

# JavaScript标准

## 书籍

###  [阮一峰的ES6](http://es6.ruanyifeng.com/)

### [深入浅出ES6中文版]http://www.infoq.com/cn/minibooks/ES6-in-Depth

## setTimeout/setInterval

setTimeout(func,time)

会在本轮代码执行完成后，下一次event loop的时候检查是否到了时间，到了就执行。所以它无法保证一定会在time后执行代码。

大多数浏览器存储time使用32位带符号整型，因此time最大为Math.pow(2, 32) - 1，超过后会在下一轮执行时立即执行func

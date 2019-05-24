---
  layout: api
  title: JavaScript标准
---


# JavaScript标准

## 书籍

###  [阮一峰的ES6](http://es6.ruanyifeng.com/)

### [深入浅出ES6中文版]http://www.infoq.com/cn/minibooks/ES6-in-Depth

## 面向对象

[《JavaScript面向对象精要》](https://segmentfault.com/a/1190000004334910)

[JavaScript继承来历](http://www.ruanyifeng.com/blog/2011/06/designing_ideas_of_inheritance_mechanism_in_javascript.html)

[JavaScript继承的实现](http://www.ruanyifeng.com/blog/2010/05/object-oriented_javascript_inheritance.html)

## setTimeout/setInterval

setTimeout(func,time)

会在本轮代码执行完成后，下一次event loop的时候检查是否到了时间，到了就执行。所以它无法保证一定会在time后执行代码。

大多数浏览器存储time使用32位带符号整型，因此time最大为Math.pow(2, 32) - 1，超过后会在下一轮执行时立即执行func

## let,const

在for循环中，括号中的let变量每次循环都会重新申明，花括号中的let变量与中括号中的let变量是父作用域与子作用域的关系。

const变量的作用域与let一致

let作用域内变量在声明前都不能被引用，申明前的区域称之为暂时性死区，就算是typeof也不能访问变量。

## 块级作用域

es6的{}形成一个块级作用域，有了这个很多地方就不需要再使用闭包。

## 字符串方法

includes是否包含，startsWith是否开始，endsWith是否结束，repeat重复当前字符串，padStart、padEnd用一个字符串补全当前字符串到指定长度

## 函数

箭头函数里的this指向外层函数的this，箭头函数本身无this特性

函数的length属性，如果参数有默认值或者rest参数，则只计算到这个参数的前一个参数

## 数组

console.log(a, b, c) 与 console.log(...[a, b, c])等价

Array.from转换类数组为数组

fill方法用于初始化数组 new Array(3).fill('a') 得到 [a, a, a]  fill方法还可以接受第二个和第三个参数，用于指定填充的起始位置和结束位置。

## 对象

name = 'Jim'; var obj = {name} 则obj为 {'name': 'jim'}

对象中的函数可以简写：

<pre><code data-language="javascript">
var obj = {
  log() {
    console.log('this is log');
  }
}
</code></pre>

直接通过大括号把变量作为key： obj = {[name]: value, ['a' + 'b']: value1};

## Promise

把Promise实例看成一个拥有各种状态和一些方法的对象，则：

+  新建Promise的时候，首先执行传入的function，执行这个function的时候传入内部包装好的resolve和reject

+  一旦resolve或者reject被调用，即可在内部改变Promise实例的状态，从而判断是否需要执行then

+  如果传入function直接return，则Promise实例立即resolve，resolve的value即为return的value

+  then方法调用的时候，如果Promise状态已经resolve，待当前片段所有同步脚本执行完成之后直接执行，不然就记录下来，resolve的时候再执行.

+ 由于then需要等到同步脚本执行后才能执行，因此resolve并不能保证让then立即执行

而对于then方法的参数function：

+ 如果此function返回promise对象，则then的执行结果为此promise对象

+ 否则，then的执行结果为一个状态为resolve的promise对象

## async

async表面是function，实际上这个function和传统的function有很大的区别：

+ async无论有没有return执行后均返回一个promise实例

+ 要得到async的值，第一种方式是promise.then，第二种是await

## await

await是用来得到一个promise的resolve的值

+ await用在异步function里，一旦出现await则此行语句会被包装成promise，呆await的promise得到resolve后再then后面的语句

+ 如果await用在赋值语句里：value = await promise(); 则value的最终值为promise的resolve值，如果promise已经resolve，value可以立即得到值

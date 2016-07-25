---
  layout: architecture
  title: 模块化
---

# 模块化

## CommonJS

通过一个叫做require的方法，同步加载依赖，然后返导出API供其它模块使用，一个模块可以通过exports或者module.exports导出API。
CommonJS规范中，一个单独的文件就是一个模块。每一个模块都是一个单独的作用域，在一个文件中定义的变量，都是私有的，对其他文件是不可见的。

    require("module");
    require("../file.js");
    exports.doStuff = function() {};
    module.exports = someValue;

典型代表: `NodeJS`

Node.js主要用于服务器的编程，加载的模块文件一般都已经存在本地硬盘，所以加载起来比较快，不用考虑异步加载的方式，所以CommonJS规范比较适用。但如果是浏览器环境，要从服务器加载模块，这是就必须采用异步模式。所以就有了 AMD 、CMD 的解决方案。

## AMD: 异步require

    require(["module", "../file"], function(module, file) { /* ... */ });
    define("mymodule", ["dep1", "dep2"], function(d1, d2) {
     return someExportedValue;
    });

AMD 规范中，define 函数有一个公有属性 `define.amd`。

典型代表：`require.js`

## CMD

CMD是SeaJS 在推广过程中对模块定义的规范化产出

CMD 规范中定义了 define 函数有一个公有属性 `define.cmd`。

CMD 模块中有两种方式提供对外的接口，一种是 exports.MyModule = ...，一种是使用 return 进行返回。

### AMD和CMD区别

    //AMD
    define(['./a','./b'], function (a, b) {

     //依赖一开始就写好
     a.test();
     b.test();
    });

    //CMD
    define(function (requie, exports, module) {

     //依赖可以就近书写
     var a = require('./a');
     a.test();

     if (status) {
     var b = requie('./b');
     b.test();
     }
    });

## UMD: 通用模块规范

UMD就是兼容CommonJS和AMD以及全局变量的写法。

UMD是AMD和CommonJS两者的结合,AMD 浏览器第一的原则发展，异步加载模块。CommonJS 模块以服务器第一原则发展，同步加载模块，它的模块无需包装。

但是我如果想同时支持两种风格呢？于是通用模块规范（UMD）诞生了。这个模式中加入了当前存在哪种规范的判断，所以能够“通用”，它兼容了AMD和CommonJS，同时还支持老式的“全局”变量规范：

    (function (root, factory) {
     if (typeof define === "function" && define.amd) {
    // AMD
    define(["jquery"], factory);
    } else if (typeof exports === "object") {
    // Node, CommonJS之类的
    module.exports = factory(require("jquery"));
    } else {
    // 浏览器全局变量(root 即 window)
    root.returnExports = factory(root.jQuery);
    }
    }(this, function ($) {
     // 方法
     function test(){};

     // 暴露公共方法
     return test;
    }));

### ES6 modules: 你们都让开，我才是标准

ES6为JavaScript添加了一些语言结构，形成另一个模块系统。

import "jquery"; export function doStuff() {} module "localModule" {}

目前的浏览器大都还不兼容，要想使用这种方式的模块系统，貌似只能借助于转译工具了（比如Babel）

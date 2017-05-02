---
  layout: lib
  title: Vue.js
---

## 官方文档

[Vue官方文档](https://vuejs.org/)

## 关于computed properties的实现

计算属性的魔法在于缓存，即不需要在每次读取的时候去运行计算方法，而仅仅是依赖的变量变化后才运行计算方法。

其实现的主要思路为：

```
    var name = {
        data: {
            firstName: 'bill',
            lastName: 'gates'
        },
        computed: {
            fullName: function(){
                return this.firstName + this.lastName;
            }
        }
    }
```

* 在第一次取fullName的时候，在一个全局的依赖对象dependence中加入依赖属性:dependence.fullName = true

* 在firstName和lastName的getter函数中，存储全局dependence对象中的依赖，setter中执行计算函数：

```
    var computedPropertiesWhoDependenceMe = [];
    getter: function(){
        for(dep in dependence){
            computedPropertiesWhoDependenceMe.push(dep)
        }
    },
    setter: function(){
        //执行computedPropertiesWhoDependenceMe里的依赖属性对应的dependenceFunction，得到计算属性的值，并保存起来
    }
```

* 在第二次及以后取fullName的时候，直接返回保存的计算值

参考：<https://www.skyronic.com/blog/vuejs-internals-computed-properties>
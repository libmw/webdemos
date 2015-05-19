---
  layout: lib
  title: rainbow代码高亮
---

# 通过rainbow组件实现代码高亮

rainbow组件基于jquery，通过给不同类型的代码符号加类名实现代码高亮。

官方网站为：<https://craig.is/making/rainbows>

##规则

rainbow通过data-language属性，对不同的语言进行解析，把不同类型的代码符号加上不同的类名。然后通过css来控制最终的样式。

ranbow支持很多种语言和多种主题，官网都有提供。

## 运行效果

<pre><code data-language="javascript">/*
 * do some jQuery magic on load
 */
$(document).ready(function() {
    function showHiddenParagraphs() {
        $("p.hidden").fadeIn(500);
    }
    setTimeout(showHiddenParagraphs, 1000);
});</code></pre>

## 使用步骤

1. 把需要高亮的代码放到pre=>code标签里，给code标签加上data-language属性。

2. 载入css。css到[官方github](https://github.com/ccampbell/rainbow/tree/master/themes)上下载。

3. 载入js。js到[官方网站](https://craig.is/making/rainbows)根据要高亮的代码语言来打包。也可以先把核心代码引入，再引入某个语言对应的代码包。

4. 完毕了。rainbow加载完成会自动对满足格式的代码进行高亮。


<script>
</script>




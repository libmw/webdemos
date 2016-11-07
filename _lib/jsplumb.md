---
  layout: lib
  title: jsplumb
---
<style>
    #div1,#div2{
        width: 200px;
        height: 200px;
        margin: 20px;
        border: 1px solid blue;
    }
</style>

# jsplumb

[jsplumb](https://jsplumbtoolkit.com/community/doc/home.html)是一个用箭头曲线连接两个或多个dom的组件，使用它可以方便在页面上画出流程图等。

## 典型用法

<pre><code data-language="javascript">jsPlumb.ready(function(){
  jsPlumb.connect({
      source:'div1',
      target:'div2',
      paintStyle:{strokeWidth:15,stroke:'rgb(243,230,18)'},
      endpointStyle:{fill:'rgb(243,229,0)'}
  });
});
</code></pre>

## 示例

<div id="div1"></div>
<div id="div2"></div>
<script src="jsPlumb-2.2.3.js"></script>
<script>
    jsPlumb.ready(function(){
        jsPlumb.connect({
            source:'div1',
            target:'div2',
            paintStyle:{strokeWidth:15,stroke:'rgb(243,230,18)'},
            endpointStyle:{fill:'rgb(243,229,0)'}
        });
    });
</script>
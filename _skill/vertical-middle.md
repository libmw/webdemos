---
  layout: skill
  title: css垂直居中对齐
---
<style>
    .vertical-wrapper{
        border: 1px solid red;
        width: 400px;
        height: 300px;
        text-align:center;
    }
    .vertical-middle{
        background: green;
        width: 100px;
        height: 130px;
        margin: 0 auto;
    }
</style>

# css垂直居中对齐

## 使用table-cell [IE8+]

外层容器display:table-cell，vertical-align:middle即可。

### 此方法的已知问题：

1.不支持外层容器position:absolute的情况

2.table-cell的包含块是display:table的元素。因此如果要在table-cell上使用百分比高度，必须要指定父级为display:table

<div class="vertical1 vertical-wrapper" style="display: table-cell;vertical-align: middle;">
    <div class="vertical-middle"></div>
</div>

## inline-block [IE8+]

1.由于辅助元素需要设置高度为100%;所以作为包含块的父级元素必须显示指定height值(即不可为百分比)

2.辅助元素和被居中的元素都应display:inline-block;vertical-align:middle;

<div class="vertical1 vertical-wrapper">
    <div class="vertical-middle" style="vertical-align:middle;display:inline-block;"></div>
    <div style="display:inline-block;vertical-align:middle;height:100%;width:1px;"></div>
</div>

## translate(-50%,-50%) [IE9+]

只支持现代浏览器。手机上可用

由于`translate的百分比是相对于自身`的，所以可用百分比来实现不定高度的垂直居中。

<div class="vertical1 vertical-wrapper" style="position: relative;">
    <div class="vertical-middle" style="transform: translate(-50%,-50%);position:absolute;top:50%;left:50%"></div>
</div>

## button居中

只试用可用放入button中的标签，如img

<style>
button {
 width: 400px;
 height: 400px;
 background: none;
 border: 1px solid #ccc;
}
</style>
<button>
  <img src="http://placehold.it/200x200" style="display:inline" />
</button>

如果要实现ie7、6的垂直居中，请直接用table嵌套
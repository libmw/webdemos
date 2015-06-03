---
  layout: h5
  title: meta标签
---

# 手机端meta标签

## 常用设置
<pre><code data-language="html">    <meta name="viewport" content="width=device-width, minimum-scale=1.0, maximum-scale=1.0">
    <meta name="format-detection" content="telephone=no">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black">
</code></pre>


## viewport

设置视图的大小、缩放等等参数。

height = [pixel_value / device-height] ,

width = [pixel_value / device-width ] ,

initial-scale = float_value ,

minimum-scale = float_value ,

maximum-scale = float_value ,

user-scalable = [yes / no] ,

target-densitydpi = [dpi_value / device-dpi / high-dpi / medium-dpi / low-dpi]

通常设置宽度为设备宽度，不能缩放：

<pre><code data-language="html">    <meta name="viewport" content="width=device-width, minimum-scale=1.0, maximum-scale=1.0">
</code></pre>

## format-detection

启动或禁用自动识别页面中的电话号码。

<pre><code data-language="html">    <meta name="format-detection" content="telephone=no">
</code></pre>

## apple-mobile-web-app-capable

是否全屏模式运行，通常设置为yes

<pre><code data-language="html">    <meta name="apple-mobile-web-app-capable" content="yes">
</code></pre>

## apple-mobile-web-app-status-bar-style

设置Web App的状态栏（屏幕顶部栏）的样式

只有apple-mobile-web-app-capable=yes此标签才起作用

default|默认值
black|黑色状态栏
black-translucent|半透明黑色状态栏

<pre><code data-language="html">    <meta name="apple-mobile-web-app-status-bar-style" content="black">
</code></pre>



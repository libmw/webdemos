---
  layout: lib
  title: Highcharts
---

# Highcharts

## 文档地址

[DEMO](http://www.highcharts.com/demo)

[官方文档](http://api.highcharts.com/highcharts)

[中文文档](http://www.hcharts.cn/api/)

## DEMO

[渐变、圆角折线图](http://jsfiddle.net/gb93kk37/6/)

[自定义仪表盘](http://jsfiddle.net/v5v3wdcy/)

## 总结

x坐标支持html，因此在x轴为时间的时候可以在日期和时间之间插入br换行


## 去掉右下角highcharts

credits: {
        enabled:false
    }


## x坐标为category类型时，让x坐标从最左开始而不是有一个空隙：

如果用spacingLeft/spacingRight方法，像素值需要根据图表大小自己设定,不推荐这种方法，这样可能会导致y轴坐标由于负偏移而显示不完全。推荐保持这个空隙。

<http://stackoverflow.com/questions/10087294/how-to-get-highcharts-x-axis-categories-starting-at-the-left-most-point>






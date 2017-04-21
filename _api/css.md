---
  layout: api
  title: CSS标准
---

# CSS标准

## [Containing block 包含块](http://www.w3.org/TR/CSS2/visuren.html#containing-block)

在css2.1中很多定位和尺寸的计算，都是相对于一个矩形区域，这个区域就叫做包含块，如以下的标准：

**"top":**

`Percentages:  	refer to height of containing block`

包含块的判定流程为：

![container block](css_containerblock.png)

所以大多数节点的包含块都是块级祖先容器。absolute和fixed特殊。

另: td(display:table-cell)的包含块是table(display:table)

三种比较少见的包含块，灰色区域是span，position是relative

![container block](css_containerblock1.png)

'direction' 是 'ltr'
![container block](css_containerblock2.png)

'direction' 是 'rtl'

![container block](css_containerblock3.png)

## [height](http://www.w3.org/TR/CSS2/visudet.html#the-height-property)


当height的值为百分比的时候，基数为包含块:

1.如果包含块`没有设置height值`，则这个百分比值无效，将自动转换为`auto`。

2.如果当前元素为`absolute`，则会自动计算包含块`padding盒子`的高度为基数。

codepen示例： <http://codepen.io/libmw/pen/ZOPaQN>

## [margin-top,margin-bottom](http://www.w3.org/TR/CSS2/box.html#margin-properties)

为内联元素设置margin，仅仅`左右margin有效`

当上下margin的值为百分比的时候，基数为包含块的`宽度`而非高度

# 选择器

![CSS选择符归类](http://ww2.sinaimg.cn/large/c5131475jw1ez3oi2e092j21h72e0wvu.jpg)

# 预处理

css预处理非常有必要，即使你不使用任何其他工具，预处理也应该使用，这样能够大大提高写码效率。

css最常见预处理工具为less和sass。

less预处理可以使用winless或者考拉直接编译，如果有构建工具，则构建工具可以直接编译。

# 模块化

css的全局作用域导致了变量名冲突的潜在危险，而模块化便是把css限制在一个局部的作用域里。

* 通过明明实现模块化，说白了就是每个模块通过命名规范来避免冲突，典型的如[BEM](http://getbem.com/)

* 通过js来写css。就是react那套方案了，带来的危害就是全成内联样式了。那你还给我谈css搞毛啊？react这套显然不好。

* 通过编译工具来实现模块化。说白了就是通过js的模块化方案来引入css，通过编译工具来对className进行统一的处理，且让js可以访问className，爽歪歪。典型的就是[cssModules了](https://github.com/css-modules/css-modules)

# vertical-align

看字面意是垂直方向的对齐，这个对齐可以取很多的值，但是大多数值都是基于当前内联元素的baseline的。baseline就是X字符的下边缘。

如设置为10px，意思是把本元素的baseline放到父元素的baseline的上方10px处。

百分比值取本元素的line-height为基数

top就是本身的顶与父元素的顶对齐，bottom同理，middle则不是
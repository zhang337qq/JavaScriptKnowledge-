# Bootstrap 

1、bootstrap 中用到一些 HTML元素和CSS属性需要将页面设置为 HTML5 文档类型，即在页面顶部添加“<!DOCTYPE html>”

2、布局容器：Bootstrap 需要为页面内容和栅格系统包裹一个 .container或container-fluid（占据全部视口viewport的容器）容器。

3、栅格系统，Bootstrap 提供了一套最多12列的流式栅格系统，通过 .row表示行 和 .col-xs-4 这种表示宽度的列快速创建栅格布局。

4、Bootstrap 排版、链接样式设置了基本的全局样式。

  font-size 设置为 14px，line-height 设置为 1.428。

<p> （段落）元素还被设置了等于 1/2 行高（即 10px）的底部外边距（margin）。

## **栅格系统**----用于页面布局的

Grid system ---- 固定的格子设计版面布局

 栅格系统用于通过一系列的行（row）与列（column）的组合来创建页面布局，你的内容就可以放入这些创建好的布局中。

1 栅格系统的种类

Container---固定宽度且居中，把页面放在一个.container（固定宽度且居中）的盒内；

container-fluid ---流式布局，把页面内容放在一个宽度为100%的盒内；

 

将container 或 container-fluid 盒水平向划分为12等分，使用row作为父级盒，内部可以水平排列一组子盒，宽度可以为总宽度的 1/12----12/12 ；

 

## （1）临界值(视口尺寸)

<img src="file:///D:/feiq/Program%20Files/feiq/Recv%20Files/JS2/day25-bootstrap/00-%E7%AC%94%E8%AE%B0_files/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20180825225910.png" />



（2）栅格原理

1) 一个row最多能容纳12个栅格单位，超出会换行;

2) 对于sm、md、lg，视口大于**临界值**，水平布局，小于**临界值**会垂直布局；

3) 对于xs，列块始终是水平布局；

 

（3）混合使用

当xs，sm， md， lg混合使用：

1) 垂直布局临界值以小屏幕的优先

2) 区块宽度以大屏幕优先

 

（4）列重置

为解决列高度不一致可能导致的问题，可以加入

<div class="row">

<div class="col-md-6"></div>

<div class="col-md-6"></div>

<div class="clearfix visible-xs"></div>

 

clearfix   清浮动  

visible-xs 只有在xs生效尺寸范围内(<768px)显示

 

 

（5）列偏移

col-sm-offset-4         向右偏移4个sm单位

col-md-offset-2        向右偏移2个md单位

col-xs-offset-5          向右偏移5个xs单位

列偏移：通过margin实现

 

（6）列嵌套

子列宽度是相对于父级盒的宽度

 

（7）列排序

Col-md-push-3 列相对于原来的位置**向右**偏移3个md单位；

Col-md-pull-9   列相对于原来的位置**向左**偏移9个md单位；

 
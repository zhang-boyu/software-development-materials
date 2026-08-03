# 第4章 跨平台移动Web技术

《HTML5移动Web开发（第2版）》

# 学习目标/Target

# 章节概述/ Summary

在Web开发中，用户体验是网站成功的一个关键因素，如果网站能够在不同的设备上拥有相似的用户体验，将会增强用户对网站的好感。为了实现相似的用户体验，在开发中需要用到跨平台移动Web技术。

本章将针对跨平台移动Web技术中的响应式Web设计、媒体查询、栅格系统、弹性盒布局进行详细的讲解，并通过阶段项目“旅游网”进行开发实战。

# 目录/Contents

# 响应式Web设计

4.1

# 4.1 响应式Web设计

为什么学习响应式Web设计？

在传统网站开发中，用户可以在移动浏览器上对网页进行缩放，将自己想要浏览的内容完全呈现出来。这样，虽然可以完整地呈现出用户想要浏览的内容，但鉴于移动设备屏幕大小的限制，过多的内容会使页面看起来杂乱无章，这就使得用户很难找到自己关注的内容。

响应式Web设计为我们解决了这一问题。响应式Web设计并不是将整个网页缩放给用户，而是经过精心筛选，有选择性的显示页面的内容。

# 先定一个小目标！

了解响应式Web设计，能够说出响应式Web设计的作用、概念和理念

4.1.1  响应式Web设计简介

# 4.1.1  响应式Web设计简介

响应式Web设计（Responsive Web Design）是由伊桑•马科特（Ethan Marcotte）于2010年提出的，能够使网页根据用户行为进行相应的调整，并展示合理的页面效果。


响应式Web设计是一种跨终端的新型网页开发技术，它可以让网页根据不同终端设备自动调整内容，达到了“一套设计，多处适用”的目的。

响应式Web设计简介

# 4.1.1  响应式Web设计简介

以三星电子商城网站为例演示响应式Web页面效果。

# 4.1.1  响应式Web设计简介

使用鼠标缩小浏览器的窗口宽度，查看页面效果。

# 先定一个小目标！

熟悉响应式Web设计相关技术，能够说出响应式Web设计常用的技术

4.1.2  响应式Web设计相关技术

# 4.1.2  响应式Web设计相关技术

在网页开发时，如果我们想要让页面根据设备的屏幕大小进行相应的调整，那么就需要使用响应式Web设计来实现。

响应式Web设计相关技术：

流式布局（Fluid Layout）
媒体查询（Media Queries）
栅格系统（Grid Systems）
弹性盒布局（Flexible Box）

# 4.1.2  响应式Web设计相关技术

流式布局：根据浏览器的宽度和屏幕的大小自动调整页面效果实现页面中文档流的控制。

媒体查询：识别媒体类型，特征（屏幕宽度，像素比等），可以根据窗口宽度、屏幕比例和设备方向等差异来改变页面的显示方式。

栅格系统：依赖于媒体查询，根据不同的屏幕大小调整布局。

弹性盒布局：提供一种有效的方式对容器中的子元素进行排列、对齐和分配空白空间。

# 媒体查询

4.2

# 先定一个小目标！

熟悉媒体查询的概念，能够说出媒体查询的作用以及媒体查询的使用方法

4.2.1  媒体查询的概念

# 媒体查询（也称为媒介查询）的概念：是CSS3新增的一种语法，用来根据窗口宽度、屏幕比例和设备方向等差异来改变页面的显示方式。

媒体查询的作用：使用媒体查询能够在不改变页面内容的情况下，为特定的输出设备制定显示效果。

什么是媒体查询

4.2.1  媒体查询的概念

# 4.2.1  媒体查询的概念

@media mediatype and|not|only (media feature) {
    CSS代码;
  }

媒体查询的基本语法形式

@media：表示声明媒体查询。
mediatype：表示媒体类型。
and、not和only：逻辑操作符，用于联合构造复杂的媒体查询
media feature：表示媒体特性。如果当前设备符合媒体类型和媒体特性，则大括号{ }中的CSS代码就会生效。

# 4.2.1  媒体查询的概念

媒体特性是由“属性:值”组成的，常用的属性有width、min-width和max-width。

width：定义输出设备中页面可见区域的宽度。
min-width：定义输出设备中页面可见区域的最小宽度。
max-width：定义输出设备中页面可见区域的最大宽度。

媒体特性

# 4.2.1  媒体查询的概念

（1）内联式：直接将@media写在<style>标签中。

<style>
  @media screen and (min-width:640px){
    body {
      background-color: pink;
    }
  }
</style>

利用媒体查询实现当页面宽度大于等于640px时，对CSS样式进行修改，将body的背景色改为pink（粉红色）。

媒体查询的使用方法

# 4.2.1  媒体查询的概念

（2）外联式：通过单独的CSS文件从外部引入，将@media写在CSS文件中即可。此外，还可以在<link>标签中使用media属性替代@media语法。

<link href="style.css" media="screen and (min-width:640px)" ref="stylesheet">

利用媒体查询实现当页面宽度大于等于640px时，style.css中的样式就会生效。

媒体查询的使用方法

# 先定一个小目标！

掌握媒体查询实现响应式布局容器，能够使用媒体查询实现响应式页面

4.2.2  使用媒体查询实现响应式布局容器

# 4.2.2  使用媒体查询实现响应式布局容器

响应式网站通常使用布局容器来控制页面中元素的大小和布局变化。

布局容器：是一个父级元素，它用来配合子级元素实现变化效果。

通过媒体查询可以改变不同屏幕下布局容器的大小，以及布局容器中的子元素的排列方式和大小，从而实现在不同屏幕下使页面布局和样式发生变化。

# 响应式布局容器宽度划分

4.2.2  使用媒体查询实现响应式布局容器

| 设备划分 | 屏幕宽度 | 布局容器宽度 |
|---|---|---|
| 超小屏幕 | <576px | 100% |
| 小屏幕 | ≥576px | 540px |
| 中等屏幕 | ≥768px | 720px |
| 大屏幕 | ≥992px | 960px |
| 超大屏幕 | ≥1200px | 1140px |

# 4.2.2  使用媒体查询实现响应式布局容器

使用媒体查询实现响应式布局容器，效果如图：

浏览器窗口宽度小于576px时页面效果

# 4.2.2  使用媒体查询实现响应式布局容器

浏览器窗口宽度大于576px时页面效果

使用媒体查询实现响应式布局容器，效果如图：

# 4.2.2  使用媒体查询实现响应式布局容器

<style>
    body {
      padding:0;
      margin:0
    }
    .container {
      height: 50px;
      background: #ddd;
      margin: 0 auto
    }
</style>
<body>
  <div class="container">布局容器</div>
</body>

定义布局容器
创建C:\code\chapter04\demo01.html文件，定义布局容器。

# 4.2.2  使用媒体查询实现响应式布局容器

/* 超小屏幕（小于576px）布局容器的宽度为100% */
@media screen and (max-width: 575px) {
  .container {
    width: 100%;
  }
}
/* 小屏幕（大于等于576px）布局容器的宽度为540px */
@media screen and (min-width: 576px) {
  .container {
    width: 540px;
  }
}

设置超小屏幕、小屏幕下布局容器宽度
修改demo01.html文件，设置超小屏幕（小于576px）下布局容器的宽度为100%，小屏幕（大于等于576px）下布局容器的宽度为540px。

# 4.2.2  使用媒体查询实现响应式布局容器

在浏览器中访问demo01.html文件
浏览器窗口宽度小于576px时页面效果。

# 4.2.2  使用媒体查询实现响应式布局容器

在浏览器中访问demo01.html文件
浏览器窗口宽度大于576px时页面效果。

# 4.2.2  使用媒体查询实现响应式布局容器

设置中等屏幕下布局容器宽度
修改demo01.html文件，设置中等屏幕（大于等于768px）下布局容器的宽度为720px。

/* 中等屏幕（大于等于768px）布局容器宽度为720px */
@media screen and (min-width: 768px) {
.container {
    width: 720px;
  }
}

# 4.2.2  使用媒体查询实现响应式布局容器

设置大屏幕、超大屏幕下布局容器宽度
设置大屏幕（大于等于992px）下布局容器的宽度为960px，超大屏幕（大于等于1200px）下布局容器的宽度为1140px 。

/* 大屏幕（大于等于992px）布局容器宽度为960px */
@media screen and (min-width: 992px) {
  .container {
    width: 960px;
  }
}
/* 超大屏幕（大于等于1200）布局容器宽度为1140px */
@media screen and (min-width: 1200px) {
  .container {
    width: 1140px;
  }
}

# 栅格系统

4.3

# 先定一个小目标！

了解栅格系统的概念，能够说出栅格系统的作用

4.3.1  栅格系统的概念

# 4.3.1  栅格系统的概念

栅格系统的由来：最早是应用于印刷媒体上的。在印刷媒体中，一个印刷版面上划分了若干个格子。每个格子的大小都是平均分配出来的，通过计算格子的份数来实现页面布局，有了这些格子以后，再进行排版的时候就非常方便了。

网页中的栅格系统（又称网格系统）：就是用固定的格子进行网页布局，是一种清晰、工整的设计风格。

什么是栅格系统

# 4.3.1  栅格系统的概念

栅格系统示意图

栅格系统示意图

# 4.3.1  栅格系统的概念

栅格系统被应用于网页布局中，随着响应式设计的流行，栅格系统开始被赋予了新的意义，即一种响应式设计的实现方式。

响应式栅格系统

# 先定一个小目标！

熟悉简单版栅格系统，能够动手实现简单版栅格系统

4.3.2  动手实现简单版栅格系统

# 4.3.2  动手实现简单版栅格系统

实现简单版栅格系统，效果如图：

栅格系统6列横向排列页面效果

栅格系统6列纵向排列页面效果

# 4.3.2  动手实现简单版栅格系统

设置页面结构
创建C:\code\chapter04\demo02.html文件，配置视口。

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="user-scalable=no,width=device-width,initial-scale=1.0, maximum-scale=1.0">
  <title>简单版栅格系统</title>
</head>
<body>
</body>
</html>

# 4.3.2  动手实现简单版栅格系统

设置页面结构
在<body></body>之间添加代码，定义行和列基本的页面结构。

<div class="row">
    <div class="col1">1</div>
    <div class="col1">2</div>
    <div class="col1">3</div>
    <div class="col1">4</div>
    <div class="col1">5</div>
    <div class="col1">6</div>
  </div>

# 4.3.2  动手实现简单版栅格系统

设置排列效果（浏览器窗口大于576px时）
修改demo02.html文件，实现栅格系统6列横向排列效果。

<style>
.row {
  width: 80%;
  margin: 0 auto
}
/* CSS3新增[attribute^=value]选择器，用于匹配属性值以指定值开头的每个元素 */
[class^="col"] {
  float: left;
  background-color: #e0e0e0;
}

# 4.3.2  动手实现简单版栅格系统

设置排列效果（浏览器窗口大于576px时）
修改demo02.html文件，继续编写代码实现栅格系统6列横向排列效果。

.col1 {
  width: 16%;
  border: 1px solid #fff;
  text-align: center;
  height: 50px;
  line-height: 50px;
}
</style>

# 4.3.2  动手实现简单版栅格系统

在浏览器中访问demo02.html文件
栅格系统6列横向排列页面效果。

栅格系统6列横向排列页面效果

# 4.3.2  动手实现简单版栅格系统

设置排列效果（浏览器窗口小于或等于576px时）
修改demo02.html文件，实现栅格系统6列纵向排列效果。

@media screen and (max-width: 576px) {
  [class^="col"] {
    float: none;
    width: 100%;
  }
}

# 4.3.2  动手实现简单版栅格系统

在浏览器中访问demo02.html文件
栅格系统6列纵向排列页面效果。

栅格系统6列纵向排列页面效果

# 弹性盒布局

4.4

# 弹性盒布局

日常生活中，我们经常浏览一些网站，网站中是如何使用弹性盒布局的呢？

# 先定一个小目标！

了解弹性盒布局的概念，能够说出弹性盒布局的结构

4.4.1  什么是弹性盒布局

# 4.4.1  什么是弹性盒布局

说到响应式，就不得不提CSS3中的弹性盒布局了，它可以轻松地创建响应式网页布局。弹性盒改进了盒子模型，既不使用浮动，也不会合并弹性盒容器与其内容之间的外边距，是一种非常灵活的布局方法。

什么是弹性盒布局

# 4.4.1  什么是弹性盒布局

弹性盒结构

弹性盒结构

弹性盒由容器、子元素和轴（包括横轴、纵轴）构成，并且默认情况下，子元素的排列方向与横轴的方向是一致的。

# 4.4.1  什么是弹性盒布局

弹性盒布局浏览器支持情况

弹性盒布局几乎在主流浏览器中都得到了支持。

| iOS Safari | Android Browser | IE | Opera | Chrome | Firefox |
|---|---|---|---|---|---|
| 7.0+ | 4.4+ | 11+ | 12.1+ | 21+ | 22+ |

# 先定一个小目标！

掌握弹性盒属性，能够使用弹性盒属性实现弹性盒布局

4.4.2  弹性盒常用属性

# 4.4.2  弹性盒常用属性

弹性盒提供了一些常用的属性：

display属性
 flex-flow属性
 justify-content属性
 align-items属性
 align-self属性
 order属性
 flex属性

我们要使用弹性盒，首先需要通过display属性指定外部父元素容器的类型为弹性盒容器，然后就可以使用弹性盒相关的属性了。

# 4.4.2  弹性盒常用属性

定义弹性盒容器

创建C:\code\chapter04\demo03.html文件，定义弹性盒容器。

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>弹性盒布局</title>
</head>
<body>
  <div class="box">
    <div class="one">one</div>
    <div class="two">two</div>
    <div class="three">three</div>
  </div>
</body>
</html>

# 4.4.2  弹性盒常用属性

display属性用于指定元素容器的类型，其默认值为inline，这意味着此元素会被显示为一个内联元素。如果设置display的值为flex，则表示用于指定弹性盒的容器。

display属性

# 4.4.2  弹性盒常用属性

<style>
  .box {
    display: flex;
    background-color: #999;
    height: 80px;
  }
  .box div {
    background-color: white;
    border: 1px solid gray;
    margin: 2px;
  }
</style>

打开demo03.html文件，设置弹性盒父容器的样式。

# 4.4.2  弹性盒常用属性

在浏览器中访问demo03.html文件，页面显示弹性盒布局。

# 4.4.2  弹性盒常用属性

flex-flow属性是flex-direction和flex-wrap的简写，用于排列弹性子元素。

flex-direction用于调整主轴的方向，可以调整为横向或者纵向。
默认情况下为横向，此时横轴为主轴，纵轴为交叉轴（或称为侧轴）；
如果改为纵向，则纵轴为主轴，横轴为交叉轴。

flex-flow属性

# 4.4.2  弹性盒常用属性

flex-direction取值：

flex-flow属性

| 取值 | 描述 |
|---|---|
| row | 弹性盒子元素按横轴方向顺序排列（默认值） |
| row-reverse | 弹性盒子元素按横轴方向逆序排列 |
| column | 弹性盒子元素按纵轴方向顺序排列 |
| column-reverse | 弹性盒子元素按纵轴方向逆序排列 |

# 4.4.2  弹性盒常用属性

flex-wrap取值：

flex-flow属性

| 取值 | 描述 |
|---|---|
| nowrap | 弹性盒容器为单行，该情况下flex子项可能会溢出容器 |
| wrap | 弹性盒容器为多行，flex子项溢出的部分会被放置到新行，第一行在上方 |
| wrap-reverse | 反转wrap排列（换行），第一行显示在下方 |

# 4.4.2  弹性盒常用属性

当使用 flex-flow 属性时，其值是 flex-direction 属性的值和 flex-wrap 属性的值的组合。例如，将 flex-direction 设为 row，将 flex-wrap 设为 nowrap，示例代码如下：

flex-flow属性

/* 简写形式 */
flex-flow: row nowrap;
/* 分开写 */
flex-direction: row;
flex-wrap: nowrap;

# 4.4.2  弹性盒常用属性

.box {
  display: flex;
  background-color: #999;
  flex-flow: column;
}

打开demo03.html文件，修改div.box元素的样式，实现弹性子元素纵向排列。

# 4.4.2  弹性盒常用属性

在浏览器中访问demo03.html文件，页面效果如下。

# 4.4.2  弹性盒常用属性

justify-content属性能够设置子元素在主轴方向的排列方式。justify-content取值：

justify-content属性

| 取值 | 描述 |
|---|---|
| flex-start | 弹性盒子元素将向行起始位置对齐（默认值） |
| flex-end | 弹性盒子元素将向行结束位置对齐 |
| center | 弹性盒子元素将向行中间位置对齐 |
| space-between | 弹性盒子元素会平均地分布在行里，第一个元素的边界与行的起始位置边界对齐，最后一个元素的边界与行结束位置的边距对齐 |
| space-around | 弹性盒子元素会平均地分布在行里，两端保留子元素与子元素之间间距大小的一半 |

# 4.4.2  弹性盒常用属性

.box {
  display: flex;
  background-color: #999;
  height: 80px;
  justify-content: space-between;
}

打开demo03.html文件，修改div.box元素的样式，实现弹性子元素两端对齐，弹性子元素之间的间隔都相等。

# 4.4.2  弹性盒常用属性

在浏览器中访问demo03.html文件，页面效果如下。

# 4.4.2  弹性盒常用属性

.box {
  display: flex;
  background-color: #999;
  height: 80px;
  justify-content: space-around;
}

修改demo03.html文件，将justify-content的值改为space-around。

# 4.4.2  弹性盒常用属性

在浏览器中访问demo03.html文件，页面效果如下 。

# 4.4.2  弹性盒常用属性

align-items属性用于设置子元素在交叉轴（十字轴）上的对齐排列方式。align-items取值：

align-items属性

| 取值 | 描述 |
|---|---|
| flex-start | 弹性盒子元素向交叉轴的起始位置对齐 |
| flex-end | 弹性盒子元素向交叉轴的结束位置对齐 |
| center | 弹性盒子元素向交叉轴的中间位置对齐 |
| baseline | 如果弹性盒子元素的行内轴与交叉轴为同一条，则该值与'flex-start'等效。其他情况下，该值将参与子元素的第一行文字的基线对齐 |
| stretch | 默认值，将元素拉伸以适合伸缩容器。可用空间在所有元素之间平均分配。如果子元素没有设置高度或者高度为“auto”，则将会占满整个容器的高度，但同时会遵照“min/max-width/height”属性的限制 |

# 4.4.2  弹性盒常用属性

.box {
  display: flex;
  background-color: #999;
  height: 80px;
  align-items: center;
}

打开demo03.html文件，修改div.box元素的样式，实现弹性子元素向交叉轴的中间位置对齐。

# 4.4.2  弹性盒常用属性

在浏览器中访问demo03.html文件，页面效果如下。

# 4.4.2  弹性盒常用属性

.box {
  display: flex;
  background-color: #999;
  height: 80px;
  align-items: flex-end;
}

打开demo03.html文件，将align-items的值设置为flex-end，实现弹性盒子元素向交叉轴的结束位置对齐。

# 4.4.2  弹性盒常用属性

在浏览器中访问demo03.html文件，页面效果如下。

# 4.4.2  弹性盒常用属性

align-self属性能够覆盖容器中的align-items属性，它允许设置单独的子元素的对齐排列方式。其取值有auto、flex-start、flex-end、center、baseline和stretch，每个值的意义与align-items属性的取值类似。

align-self属性

# 4.4.2  弹性盒常用属性

.two {
  align-self: center
}

打开demo03.html文件，将div.box容器中的第2个弹性子元素div单独设置为垂直居中效果。

# 4.4.2  弹性盒常用属性

在浏览器中访问demo03.html文件，页面效果如下。

# 4.4.2  弹性盒常用属性

order属性用于设置子元素的排列顺序，order的取值默认为0，且数值越小，排列越靠前。

order属性

.one {
  order: 3;
}
.two {
  order: 1;
}
.three {
  order: 2;
}

打开demo03.html文件，将div.box容器中的子元素one、two、three的order值分别设置为3、1、2。

# 4.4.2  弹性盒常用属性

在浏览器中访问demo03.html文件，页面效果如下。

# 4.4.2  弹性盒常用属性

flex属性能够设置子元素的伸缩性。

flex属性是以下3个属性的缩写：

flex-grow（放大比率，默认为0，比较常用）
flex-shrink（缩小比率，默认为1，可选属性）
flex-basis（宽度，像素值，默认为auto，可选属性）

flex属性

# 4.4.2  弹性盒常用属性

.one {
  flex-grow: 1; /* 也可以简写为 flex: 1; */
}

打开demo03.html文件，将one的flex-grow设置为1，将div.one元素占满整个盒子的可用空间。

# 4.4.2  弹性盒常用属性

在浏览器中访问demo03.html文件，页面显示将one的flex-grow设置为1的弹性盒布局。

# 阶段项目——旅游网

4.5

# 先定一个小目标！

熟悉旅游网项目分析，能够对项目有一个整体的认识。

4.5.1  旅游网项目分析

# 旅游网是一个为外出旅行人群提供景点推荐、酒店预订、机票订购、门票订购服务的网站。接下来将使用跨平台移动Web技术实现旅游网首页页面效果。

4.5.1  旅游网项目分析

# 4.5.1  旅游网项目分析

旅游网首页效果如图：

首页页面效果

# 4.5.1  旅游网项目分析

首页功能模块如图：

首页功能模块

# 4.5.1  旅游网项目分析

在C:\code\chapter04 目录下创建 travel 项目，项目目录结构如图：

项目目录结构

# 4.5.1  旅游网项目分析

下面对旅游网项目目录结构中的各个目录及文件进行说明。
（1） travel：项目根目录，在该目录下包含css、images目录，以及项目入口文件index.html。      
（2）css：CSS文件目录，该目录下存放CSS文件，用于添加自定义的样式代码。
（3）images：图片文件目录，该目录下存放项目引用的图片文件。

# 先定一个小目标！

掌握旅游网首页整体布局，能够对旅游网首页布局有一个整体的认识

4.5.2  旅游网首页整体布局

# 旅游网首页的外层容器为body元素，该容器中包含搜索栏、焦点图、快捷导航栏以及主导航栏4个功能模块，具体实现细节如下。

4.5.2  旅游网首页整体布局

外层容器body元素在页面中垂直居中显示。
使用<div>标签定义搜索栏模块，采用固定定位将搜索栏定位在顶部。
使用<div>标签定义焦点图模块。
使用<ul>标签定义快捷导航栏模块，并设置为弹性盒子。
使用<nav>标签定义主导航栏模块。

# 创建C:\code\chapter04\travel\index.html，定义主体结构，引入normalize.css文件和index.css文件。

4.5.2  旅游网首页整体布局

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <link rel="stylesheet" href="css/normalize.css">
  <link rel="stylesheet" href="css/index.css">
  <title>旅游网</title>
</head>
<body>
</body>
</html>

# 4.5.2  旅游网首页整体布局

<div class="search-index">
    搜索栏模块
  </div>
  <div class="focus">
    焦点图模块
  </div>
  <ul class="local-nav">
     快捷导航栏模块
  </ul>
  <nav>
    主导航栏模块
  </nav>

在index.html文件的<body></body>中间，定义搜索栏、焦点图、快捷导航栏和主导航栏模块。

# 4.5.2  旅游网首页整体布局

body {
  max-width: 540px;
  min-width: 320px;
  margin: 0 auto;
  font: normal 14px/1.5 Tahoma, "Lucida Grande", Verdana, "Microsoft Yahei", STXihei, hei;
  color: #000;
  background: #f2f2f2;
  overflow-x: hidden;
  -webkit-tap-highlight-color: transparent;
}

在index.css文件中，实现搜索栏、焦点图、快捷导航栏和主导航栏最外层盒子结构页面样式效果。

# 4.5.2  旅游网首页整体布局

ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
div {
  box-sizing: border-box;
}
/* 搜索栏模块 */
.search-index {
  display: flex;
  /* 固定定位 */
  position: fixed;

top: 0;
  left: 50%;
  /* 让固定定位的元素居中 */
  transform: translateX(-50%);
  width: 100%;
  min-width: 320px;
  max-width: 540px;
  height: 44px;
  /* background-color: pink; */
  background-color: #F6F6F6;
  border-top: 1px solid #ccc;
  border-bottom: 1px solid #ccc;
}

在index.css文件中，实现搜索栏、焦点图、快捷导航栏和主导航栏最外层盒子结构页面样式效果。

# 4.5.2  旅游网首页整体布局

/* 焦点图模块 */
.focus {
  padding-top: 44px;
}
/* 快捷导航栏模块 */
.local-nav {
  display: flex;
  height: 64px;
  margin: 3px 4px;
  background-color: #fff;
  border-radius: 8px;
}

在index.css文件中，实现搜索栏、焦点图、快捷导航栏和主导航栏最外层盒子结构页面样式效果。

/* 主导航栏模块 */
nav {
  overflow: hidden;
  border-radius: 8px;
  margin: 0 4px 3px;
}

# 4.5.2  旅游网首页整体布局

在浏览器中，打开index.html文件，各个模块的外层盒子页面效果。

# 先定一个小目标！

掌握搜索栏布局的实现，能够实现搜索栏布局效果

4.5.3  搜索栏布局

# 4.5.3  搜索栏布局

搜索栏效果图

搜索栏定位在页面的顶端，用来实现快速搜索功能。

# 4.5.3  搜索栏布局

结构分析

整个搜索栏包含在父级容器<div>标签中，采用固定定位，固定在顶端。
左侧搜索内容区使用<div>标签定义，采用相对定位。
右侧“我的”使用<a>标签定义。

# 4.5.3  搜索栏布局

<!-- 搜索栏 -->
<div class="search">
  <input type="text" placeholder="搜索:目的地/酒店/景点/航班号">
</div>
<a href="#" class="user">我 的</a>

在index.html文件中定义搜索栏结构。

# 4.5.3  搜索栏布局

.search {
  position: relative;
  height: 26px;
  line-height: 24px;
  border: 1px solid #ccc;
  flex: 1;
  font-size: 12px;
  color: #666;
  margin: 7px 10px;
  padding-left: 25px;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, .2);
}

在index.css文件中实现搜索栏页面结构样式。

# 4.5.3  搜索栏布局

.search::before {
  content: "";
  position: absolute;
  top: 5px;
  left: 5px;
  width: 15px;
  height: 15px;
  background: url(../images/sprite.png) no-repeat -59px -279px;
  background-size: 104px auto;
}

在index.css文件中实现搜索栏页面结构样式。

# 4.5.3  搜索栏布局

.user {
  width: 44px;
  height: 44px;
  font-size: 12px;
  text-align: center;
  color: #2eaae0;
}

在index.css文件中实现搜索栏页面结构样式。

.user::before {
  content: "";
  display: block;
  width: 23px;
  height: 23px;
  background: url(../images/sprite.png) no-repeat -59px -194px;
  background-size: 104px auto;
  margin: 4px auto -2px;
}

# 4.5.3  搜索栏布局

a {
  text-decoration: none;
  color: #222;
}
input {
  width: 90%;
  background: #f2f2f2;
  border: none;
}
input:focus {
  outline: none;
}

在index.css文件中实现搜索栏页面结构样式。

# 4.5.3  搜索栏布局

在浏览器中打开index.html文件，页面显示搜索栏效果。

# 先定一个小目标！

掌握焦点图布局，能够实现焦点图模块效果

4.5.4  焦点图布局

# 4.5.4  焦点图布局

焦点图效果图

整个焦点图是一张图片，可以进行等比例缩放。

# 4.5.4  焦点图布局

结构分析

整个焦点图包含在<div>容器中。
焦点图片使用<img>标签定义，设置图片宽度100%。

# 4.5.4  焦点图布局

<img src="images/focus.jpg" alt="">

在index.css文件中实现焦点图模块样式。

.focus img {
  width: 100%;
}

在index.html文件中定义焦点图模块结构。

# 4.5.4  焦点图布局

保存文件，运行结果如下图所示。

# 先定一个小目标！

掌握快捷导航栏布局，能够实现快捷导航栏模块效果。

4.5.5  快捷导航栏布局

# 4.5.5  快捷导航栏布局

快捷导航栏效果图

快捷导航栏用来实现“景点·玩乐”“周边游”“美食林”“一日游”和“当地攻略”图标按钮。

# 4.5.5  快捷导航栏布局

结构分析

整个快捷导航栏包含在父级容器<ul>中。
使用<li>标签定义快捷导航栏中的每一项。
使用<a>标签为快捷导航栏中的每一项添加超链接。
<a>标签中有两个<span>标签，上面的<span>标签用于显示图标，下面的<span>标签用于显示文本。

# 4.5.5  快捷导航栏布局

<li>
  <a href="#" title="景点·玩乐">
    <span class="local-nav-icon-icon1"></span>
    <span>景点·玩乐</span>
  </a>
</li>
<li>
  <a href="#" title="周边游">
    <span class="local-nav-icon-icon2"></span>
    <span>周边游</span>
  </a>
</li>

在index.html文件中定义快捷导航栏模块结构。

# 4.5.5  快捷导航栏布局

<li>
  <a href="#" title="美食林">
    <span class="local-nav-icon-icon3"></span>
    <span>美食林</span>
  </a>
</li>
<li>
  <a href="#" title="一日游">
    <span class="local-nav-icon-icon4"></span>
    <span>一日游</span>
  </a>
</li>
<li>
  <a href="#" title="当地攻略">
    <span class="local-nav-icon-icon5"></span>
    <span>当地攻略</span>
  </a>
</li>

在index.html文件中定义快捷导航栏模块结构。

# 4.5.5  快捷导航栏布局

.local-nav li {
  flex: 1;
}
.local-nav a {
  display: flex;
  flex-direction: column;
  /* 交叉轴居中对齐 */
  align-items: center;
  font-size: 12px;
}

在index.css文件中实现快捷导航栏模块结构样式。

# 4.5.5  快捷导航栏布局

.local-nav li [class^="local-nav-icon"] {
  width: 32px;
  height: 32px;
  background-color: pink;
  margin-top: 8px;
  background: url(../images/localnav_bg.png) no-repeat 0 0;
  background-size: 32px auto;
}

在index.css文件中实现快捷导航栏模块结构样式。

# 4.5.5  快捷导航栏布局

.local-nav li .local-nav-icon-icon2 {
  background-position: 0 -32px;
}
.local-nav li .local-nav-icon-icon3 {
  background-position: 0 -64px;
}
.local-nav li .local-nav-icon-icon4 {
  background-position: 0 -96px;
}
.local-nav li .local-nav-icon-icon5 {
  background-position: 0 -128px;
}

在index.css文件中实现快捷导航栏模块结构样式。

# 4.5.5  快捷导航栏布局

保存文件，运行结果如下图所示。

# 先定一个小目标！

掌握主导航栏布局，能够实现主导航栏模块效果。

4.5.6  主导航栏布局

# 4.5.6  主导航栏布局

主导航栏效果图

主导航栏用来实现酒店、机票和旅游的分类。

# 4.5.6  主导航栏布局

结构分析

# 4.5.6  主导航栏布局

整个导航栏包含在父级容器<nav>中。
使用<div>标签定义主导航栏中的每一项。
主导航栏中的每一项的内部由3个<div>标签组成，第1个<div>标签中有1个<a>标签，第2个和第3个<div>标签中有上下排列的两个<a>标签。

# 4.5.6  主导航栏布局

<div class="nav-common">
  <div class="nav-items">
    <a href="#">酒店</a>
  </div>
  <div class="nav-items">
    <a href="#">海外酒店</a>
    <a href="#">特价酒店</a>
  </div>
  <div class="nav-items">
    <a href="#">团购</a>
    <a href="#">民宿·客栈</a>
  </div>
</div>

<div class="nav-common">
  <div class="nav-items">
    <a href="#">机票</a>
  </div>
  <div class="nav-items">
    <a href="#">火车票</a>
    <a href="#">特价机票</a>
  </div>
  <div class="nav-items">
    <a href="#">汽车票·船票</a>
    <a href="#">专车·租车</a>
  </div>
</div>

在index.html文件中定义主导航栏模块结构。

# 4.5.6  主导航栏布局

<div class="nav-common">
  <div class="nav-items">
    <a href="#">旅游</a>
  </div>
  <div class="nav-items">
    <a href="#">门票</a>
    <a href="#">目的地攻略</a>
  </div>
  <div class="nav-items">
    <a href="#">游轮旅行</a>
    <a href="#">定制旅行</a>
  </div>
</div>

在index.html文件中定义主导航栏模块结构。

# 4.5.6  主导航栏布局

nav {
  overflow: hidden;
  border-radius: 8px;
  margin: 0 4px 3px;
}
.nav-common {
  display: flex;
  height: 88px;
  background-color: pink;
}
.nav-common:nth-child(2) {
  margin: 3px 0;
}
.nav-items {
  flex: 1;
  display: flex;
  flex-direction: column;

在index.css文件中，实现主导航栏模块结构样式。

# 4.5.6  主导航栏布局

.nav-items a {
  flex: 1;
  text-align: center;
  line-height: 44px;
  color: #fff;
  font-size: 14px;
  /* 文字阴影 */
  text-shadow: 1px 1px rgba(0, 0, 0, .2);
}
.nav-items a:nth-child(1) {
  border-bottom: 1px solid #fff;
}
.nav-items:nth-child(1) a {
  border: 0;
  background: url(../images/hotel.png) no-repeat bottom center;
  background-size: 121px auto;
}

在index.css文件中，实现主导航栏模块结构样式。

# 4.5.6  主导航栏布局

. /* -n+2用于选择前面两个div.nav-items元素 */
.nav-items:nth-child(-n+2) {
  border-right: 1px solid #fff;
}
.nav-common:nth-child(1) {
  background: linear-gradient(to left, #FA994D, #FA5A55);
}
.nav-common:nth-child(2) {
  background: linear-gradient(to left, #53BCED, #4B90ED);
}
.nav-common:nth-child(3) {
  background: linear-gradient(to left, #6CD559, #34C2A9);
}

在index.css文件中，实现主导航栏模块结构样式。

# 4.5.6  主导航栏布局

.nav-common:nth-child(2) .nav-items:nth-child(1) a {
  border: 0;
  background: url(../images/plane.png) no-repeat bottom center;
  background-size: 93px auto;
}
.nav-common:nth-child(3) .nav-items:nth-child(1) a {
  border: 0;
  background: url(../images/travel.png) no-repeat bottom center;
  background-size: 93px auto;
}

在index.css文件中，实现主导航栏模块结构样式。

# 4.5.6  主导航栏布局

保存文件，运行结果如图。

# 本章小结

本章主要讲解了响应式Web设计的概念、媒体查询、栅格系统、弹性盒布局等内容，还讲解了旅游网项目，包括搜索栏页面效果、焦点图页面效果等。通过学习本章内容，希望大家能够使用媒体查询和弹性盒布局相关内容独立完成旅游网项目功能的开发。

本

章

小

结
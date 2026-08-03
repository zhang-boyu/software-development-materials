# 第3章  移动端页面布局和常用事件

《HTML5移动Web开发（第2版）》

# 学习目标/Target

# 章节概述/ Summary

目前移动设备大多采用触屏操作，这使得用户逐渐摆脱了PC端使用键盘和鼠标操作的束缚，人机交互更加方便。触屏操作不仅体现在功能强大、多样化的App应用程序上，对于移动Web应用程序同样也提供了良好的使用体验。本章将针对移动Web开发用到的流式布局、视口和移动端常用事件进行详细讲解，并运用所学知识完成移动商城网站首页的页面制作。

# 目录/Contents

# 流式布局

3.1

# 先定一个小目标！

掌握流式布局，能够通过流式布局对页面进行布局

3.1 流式布局

# 3.1 流式布局

流式布局使用场景：为了适应小屏幕设备，移动设备和跨平台（响应式）网页开发大多采用流式布局。
流式布局是一种等比例缩放布局方式，在CSS代码中使用百分比来设置宽度，所以也称为百分比自适应布局。

什么是流式布局

# 流式布局实现方法：将CSS固定像素宽度换算为百分比宽度，换算公式如下。

流式布局实现方法

3.1 流式布局

百分比宽度 = 目标元素宽度 / 父盒子宽度

# 使用CSS固定像素宽度布局与流式布局两种布局方式实现多栏布局结构，效果如图：

3.1 流式布局

CSS固定像素宽度的布局方式

流式布局方式

# 3.1 流式布局

通过案例演示CSS固定像素宽度布局与流式布局两种布局方式的使用，对比这两种布局方式的区别。
案例实现步骤：
先采用CSS固定像素宽度布局方式实现多栏布局。
然后分析这种方式存在的问题。
最后改为流式布局方式实现多栏布局，验证问题是否解决。

# 编写页面结构
在C:\code\chapter03\demo01.html文件中，编写代码实现多栏布局结构。

<body>
  <header>header</header>
  <nav>nav</nav>
  <section>
    <aside>aside</aside>
    <article>article</article>
  </section>
  <footer>footer</footer>
</body>

STEP  01

3.1 流式布局

# 实现CSS固定像素宽度布局
编写页面样式代码。

STEP  02

3.1 流式布局

<style>
  body > * {
    width: 980px;height: auto;margin: 10px auto 0;
    border: 1px solid #000;padding: 5px;text-align: center;}
  header { height: 50px; }
  section { height: 300px; }
  footer { height: 30px; }
  section > * {height: 100%;border: 1px solid #000;float: left;}
  aside { width: 250px; }
  article { width: 710px; margin-left: 16px; }
</style>

# 访问测试
在浏览器中访问demo01.html文件。

STEP  03

3.1 流式布局

CSS固定像素宽度的布局方式

# 尝试缩小浏览器窗口，会发现demo01.html页面元素的大小不会随着浏览器窗口改变，浏览器会出现滚动条。

STEP  04

3.1 流式布局

缩小浏览器窗口

# STEP  05

3.1 流式布局

采用流式布局方式
将页面<title>标签的内容改为“流式布局”，然后修改页面样式，将所有CSS固定像素宽度修改为百分比宽度的形式，让页面元素的大小随着浏览器窗口改变。

<style>
  body > * {
    width: 95%;   /* 设置body的第一级子元素宽度为95% */
    height: auto;margin: 10px auto 0;
    border: 1px solid #000;padding: 5px;text-align: center;
  }
  header { height: 50px; }
  section { height: 300px; }
  footer { height: 30px; }

# STEP  05

3.1 流式布局

采用流式布局方式
将页面<title>标签的内容改为“流式布局”，然后修改页面样式，将所有CSS固定像素宽度修改为百分比宽度的形式，让页面元素的大小随着浏览器窗口改变。

section > * {
      height: 100%;      /* 设置section的第一级子元素高度为100% */
      border: 1px solid #000;float: left;
    } 
    /* aside百分比宽度 = 目标元素宽度250px / 父盒子宽度980px */
    aside { width: 25.51%; } 
    /* article百分比宽度 = 目标元素宽度710px / 父盒子宽度980px */
    article { width: 72.45%; margin-left: 1.04%; } 
</style>

# 在浏览器中访问demo01.html文件。
将浏览器窗口进行缩放，会发现页面宽度也会按照一定的比例进行缩放。

STEP  06

3.1 流式布局

# 视口

3.2

# 先定一个小目标！

熟悉视口的概念，能够说出视口的作用和分类

3.2.1  视口的概念

# 在移动Web开发中，视口（viewport）的概念起初是由苹果公司为iOS系统的Safari浏览器引入的，其目的是为了让iPhone的小屏幕尽可能完整地显示整个网页。

通过设置视口，能将大分辨率网页缩小显示在手机浏览器上，这样保证网页在手机上看起来更像在桌面浏览器中的样子。

简单来说，视口就是浏览器显示页面内容的区域。

什么是视口

3.2.1  视口的概念

# 视口的分类

3.2.1  视口的概念

布局视口

视觉视口

理想视口（重点）

视口的分类

# 布局视口

3.2.1  视口的概念

布局视口（layout viewport）：指浏览器绘制网页的视口，目前大多数移动端浏览器都默认设置了布局视口的宽度为980px。

为什么采用默认的宽度：移动端浏览器之所以采用这样的默认宽度，是为了防止早期的PC端网页在屏幕宽度过小的情况下出现排版混乱的问题。

# 3.2.1  视口的概念

布局视口的效果图。

# 3.2.1  视口的概念

布局视口：当浏览器刚打开网页时，浏览器会按照980px的宽度进行网页绘制，由于手机的屏幕宽度比较窄，浏览器为了将网页显示完整，默认情况下会对网页进行等比例缩小，导致网页中的图片和文字都变得非常小。

用户虽然可以通过双击屏幕将网页放大到正常的大小，但网页在浏览器中会出现横向滚动条，必须左右滑动屏幕才能查看完整的一行内容。

# 视觉视口

3.2.1  视口的概念

视觉视口（visual viewport）：指显示在屏幕上的网页区域，这个区域的宽度等同于移动设备的浏览器窗口的宽度。

视觉视口的宽度取决于手机的屏幕分辨率，不同手机的宽度不同。当用户在手机上缩放网页时，操作的是视觉视口，而布局视口仍然保持原来的宽度。

# 3.2.1  视口的概念

视觉视口的效果图。

# 理想视口

3.2.1  视口的概念

理想视口（ideal viewport）：指对设备来讲最理想的视口。

采用理想视口的方式，可以使网页在移动端浏览器上获得最理想的浏览和阅读的宽度。
在理想视口情况下，布局视口的宽度和屏幕宽度是一致的，这样就不需要左右滚动页面了。

# 3.2.1  视口的概念

理想视口的效果图。

# 先定一个小目标！

掌握如何使用<meta>标签设置视口，能够为移动端页面设置合适的视口

3.2.2  使用<meta>标签设置视口

# STEP  02

3.2.2  使用<meta>标签设置视口

将<meta>标签中的name属性设为viewport，即可设置视口。

利用<meta>标签设置视口

<meta name="viewport">

# STEP  02

3.2.2  使用<meta>标签设置视口

在使用<meta>标签设置视口时，可以在<meta>标签的content属性中添加一些参数，其格式为“参数名=参数值”，多个参数用“,”分开。

例如“width=device-width, initial-scale=1.0”，其中width和initial-scale是参数名，device-width和1.0是参数值。

<meta>标签的content属性

# 3.2.2  使用<meta>标签设置视口

content属性的常用参数

| 参数名 | 说明 |
|---|---|
| width | 设置视口宽度，可以设为正整数（像素）或特殊值device-width |
| height | 设置视口高度，可以设为正整数（像素）或特殊值device-height |
| initial-scale | 设置视口的默认缩放比，取值范围为0.0~10.0 |
| maximum-scale | 最大允许缩放比，取值范围为0.0~10.0 |
| minimum-scale | 最小允许缩放比，取值范围为0.0~10.0 |
| user-scalable | 设置视口是否允许用户自行缩放，其值为yes（默认）或no（禁止用户缩放），也可以使用数字1（允许用户缩放）或数字0（禁止用户缩放） |

# 3.2.2  使用<meta>标签设置视口

使用<meta>标签配置视口属性。

<meta name="viewport" content="user-scalable=no, width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">

user-scalable=no：不允许用户自行缩放页面。
width=device-width：通知浏览器布局视口的宽度应该与当前设备的宽度一致，即设备有多宽，布局视口就有多宽。
initial-scale=1.0：视口默认缩放比为1.0。
maximum-scale=1.0：最大允许缩放为1.0。
minimum-scale=1.0：最小允许的缩放比例1.0。

# 案例：通过Chrome浏览器模拟移动设备访问网页，观察页面在设置视口前后的区别。

3.2.2  使用<meta>标签设置视口

设置视口之后的页面效果

模拟移动设备的显示效果
（设置视口前）

# 编写页面
创建C:\code\chapter03\demo02.html文件，在页面中使用<img>标签创建图片，在这一步先不给页面设置视口。

<style>
    .title {width: 320px;font-size: 20px;color: red;margin: 0 auto;text-align: center;}
    img {border: 1px solid #000;}
  </style>
</head>
<body>
  <div class="title">
    <img src="images/cp3.jpg">
    <span>限时试用</span>
  </div>
</body>

STEP  01

3.2.2  使用<meta>标签设置视口

# 在浏览器中访问demo02.html文件
PC端浏览器页面显示效果。

STEP  02

3.2.2  使用<meta>标签设置视口

# 在浏览器中访问demo02.html文件。
启动开发者工具，模拟移动设备的显示效果。

STEP  03

3.2.2  使用<meta>标签设置视口

# 切换到移动设备
单击图中标注的     按钮，切换到移动设备（如iPhone 6/7/8），此时会看到页面整体缩小了，并且在页面的顶部出现了设备的名称，移动设备上页面显示效果。

STEP  04

3.2.2  使用<meta>标签设置视口

# 修改网页
修改demo02.html文件，将<title>中的内容修改为“设置视口后”，同时在<head>标签中添加<meta>标签设置视口。

STEP  05

3.2.2  使用<meta>标签设置视口

<meta name="viewport" content="user-scalable=no, width=device-width, 
initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">

# 在移动设备中查看设置视口之后的页面效果。

3.2.2  使用<meta>标签设置视口

# 移动端touch事件

3.3

# 先定一个小目标！

熟悉touch事件，能够灵活使用4种基本touch事件

3.3.1  touch事件简介

# 3.3.1  touch事件简介

touch的中文翻译为“触摸、接触”。touch事件是一组事件的统称。

4种基本的touch触屏事件

| 事件 | 事件描述 |
|---|---|
| touchstart | 当手指触摸屏幕时触发 |
| touchmove | 当手指在屏幕上滑动时触发 |
| touchend | 当手指离开屏幕时触发 |
| touchcancel | 当系统取消touch事件的时候触发（如来电、弹出信息等） |

# 3.3.1  touch事件简介

touch触屏事件需要通过addEventListener()方法向指定元素添加事件监听。

<style>
  .box {width: 50px;height: 50px;background-color: red; }
</style>
<div class="box"></div>
<script>
  window.onload = function() {
    var box = document.querySelector('.box'); // 1. 获取DOM元素
    // 2. 为元素添加事件
  （代码见下页）
 };

# 3.3.1  touch事件简介

// 2. 为元素添加事件
    box.addEventListener('touchstart', function() {  // 添加开始触摸事件：当手指触摸屏幕时触发
      console.log('touchstart');
    });
   box.addEventListener('touchmove', function() {  // 添加手指滑动事件：当手指在屏幕上滑动时触发
      console.log('touchmove');
    });
    box.addEventListener('touchend', function() {  // 添加触摸结束事件：当手指离开屏幕时触发
      console.log('touchend');
    });
    box.addEventListener('touchcancel', function() {  // 添加触摸意外中断事件
      console.log('touchcancel');
    });

touch触屏事件需要通过addEventListener()方法向指定元素添加事件监听。

# 3.3.1  touch事件简介

移动端的touch触屏事件发生后会产生TouchEvent对象，该对象包含3个用于跟踪触屏的属性，用于返回不同的触屏点集合。

TouchEvent对象的重要属性

| 属性名称 | 属性描述 |
|---|---|
| touches | 表示当前跟踪的触摸操作的 touch 对象的触摸点集合 |
| targetTouches | 表示当前对象上所有触摸点的集合 |
| changedTouches | 返回在上一次触摸和此次触摸之间状态发生变化的所有触摸对象的集合 |

# 3.3.1  touch事件简介

触摸点集合中每个touch对象代表一个触点，它包含一些用于获取触摸信息的常用属性，如位置、大小、形状、压力大小和目标元素属性等。

touch对象的常用属性

| 属性名称 | 描述 |
|---|---|
| clientX | 触摸目标在视口中的x坐标 |
| clientY | 触摸目标在视口中的y坐标 |
| identifier | 标识触摸的唯一ID |
| pageX | 触摸目标在页面中的x坐标 |
| pageY | 触摸目标在页面中的y坐标 |
| screenX | 触摸目标在屏幕中的x坐标 |
| screenY | 触摸目标在屏幕中的y坐标 |
| target | 触摸的DOM节点目标 |

# 3.3.1  touch事件简介

多学一招：touch事件获取坐标

触摸点的相关信息可以通过TouchEvent对象获取，示例代码如下。

e.触摸点集合.属性名称

例如，当手指触摸屏幕时或者当手指在屏幕上滑动时获取触摸目标相对于当前视口的x坐标距离，可以使用e.targetTouches[0].clientX或e.touches[0].clientX进行获取。

# 先定一个小目标！

掌握如何解决移动端click事件的延时问题，能够运用3种方式解决问题

3.3.2  解决移动端click事件的延时问题

# 3.3.2  解决移动端click事件的延时问题

移动端使用click事件时会出现300ms左右的延时问题，其原因是浏览器需要判断用户的操作是单次点击还是双次点击。
举例：
例如，在手机上浏览网页时，由于手机屏幕比较小，页面中可能会有一些文字看不清楚。为了看清楚文字，用户通常会快速双击屏幕放大页面查看内容。当用户第一次点击屏幕时，浏览器无法立刻判断用户的操作，浏览器会等待300ms。如果用户在300ms内再次点击了屏幕，浏览器就会认为是一个双次点击的操作，否则就会认为是一个单次点击操作。

移动端click事件的延时问题的原因

# 3.3.2  解决移动端click事件的延时问题

随着移动端网页的流行与普及，用户对网页性能有了更高的要求，而在移动端使用click事件会出现延时，这会影响用户的体验。

下面我们给出了3个解决方案，用来处理click事件出现300ms延时的问题，读者可以根据实际需求进行选择。

解决移动端click事件的延时问题

# 3.3.2  解决移动端click事件的延时问题

解决移动端click事件的延时问题

禁用缩放

封装touch事件

使用Fastclick插件

3种解决移动端click事件的延时问题的方法

# 3.3.2  解决移动端click事件的延时问题

禁用缩放解决移动端click事件的延时问题

使用user-scalable=no设置当前页面不可缩放，禁用浏览器默认的双击缩放，去掉300ms的点击延时。
缺点：它完全禁用了双击缩放，当我们需要放大文字或者图片时无法满足需求。

<meta name="viewport" content="user-scalable=no">

# 3.3.2  解决移动端click事件的延时问题

封装touch事件解决移动端click事件的延时问题

封装touch事件，解决300ms延时问题。
缺点：这种方式可以检测单个元素发生点击时的状态，解决移动端click事件出现300ms的延时问题。但是不能检查多个元素发生点击时的状态。

# 3.3.2  解决移动端click事件的延时问题

实现思路：
当手指触摸屏幕时，记录当前触摸开始的时间；
当手指离开屏幕时，用离开的时间减去触摸开始的时间，得到手指停留时间；
如果手指停留时间小于150ms，并且没有滑动过屏幕，那么就定义为点击。

封装touch事件解决移动端click事件的延时问题

# 3.3.2  解决移动端click事件的延时问题

function tap(obj, callback) {
  var isMove = false;	// 记录手指是否移动
  var startTime = 0;	// 记录触摸时候的时间变量
  obj.addEventListener('touchstart', function(e) {
    startTime = Date.now(); // 记录触摸时间
  });
  // 当手指触摸屏幕时，记录当前触摸时间
  obj.addEventListener('touchmove', function(e) { 
    isMove = true;// 查看手指是否有滑动（如果有滑动算拖拽，不算点击） 
  });

代码实现：当手指触摸屏幕时，记录当前触摸时间。

# 3.3.2  解决移动端click事件的延时问题

obj.addEventListener('touchend', function(e) {
    // 如果手指触摸和离开时间小于150ms算点击
    if (!isMove && (Date.now() - startTime) < 150) {
       callback && callback(); // 执行回调函数
    }
    isMove = false;  // 取反
    startTime = 0;
  });
}
// 调用封装好的tap()方法
tap(div, function() {
  // 执行点击后的代码
});

代码实现：当手指离开屏幕时，用离开的时间减去触摸的时间，得到手指停留时间，如果手指停留时间小于150ms，并且没有滑动过屏幕，那么就定义为点击。

# 3.3.2  解决移动端click事件的延时问题

使用Fastclick插件解决移动端click事件的延时问题

使用Fastclick插件，解决300ms延时问题。
实现原理：在检测到touchend事件的时候，通过DOM自定义事件立即触发click事件，并把浏览器在300ms之后的click事件阻止掉。
优点：可以完美解决移动端click事件出现300ms的延时问题。

# 3.3.2  解决移动端click事件的延时问题

下载并引入插件
首先通过官网下载fastclick.js至本地，并在HTML网页中使用<script>标签引入fastclick.js文件。

<script src="fastclick.js"></script>

# 3.3.2  解决移动端click事件的延时问题

if ('addEventListener' in document) {
  document.addEventListener('DOMContentLoaded', function() {
     // 表示将document.body下面的所有元素都绑定为Fastclick
     FastClick.attach(document.body);
  }, false);
}

初始化插件
通过JavaScript方式对Fastclick进行初识化。

# 3.3.2  解决移动端click事件的延时问题

<!-- HTML结构 -->
<body>
  <div></div>
</body>

// 编写JavaScript代码，绑定click事件
var Odiv = document.querySelector('div');
Odiv.addEventListener('click', function() {
  alert('点击操作');
});

使用插件
在项目中使用fastclick.js插件。

# 阶段项目——移动商城

3.4

# 先定一个小目标！

熟悉移动商城项目分析，能够对项目有一个整体的认识

3.4.1  项目分析

# 3.4.1  项目分析

“移动商城”是一个类似淘宝、京东的电商类移动端网站。在本项目中我们仅实现首页的相关功能，首页主要分为4个模块，分别是搜索栏、轮播图、导航栏和商品区。实现的过程中用到了前面所学到的流式布局、视口和touch事件。

# 3.4.1  项目分析

首页页面效果

# 首页功能模块

首页由4个功能模块组成，分别是搜索栏、轮播图、导航栏和商品区。

3.4.1  项目分析

# 3.4.1  项目分析

为了方便读者进行项目的搭建，在shopM文件夹中创建项目的其他目录和文件。

首页目录结构

# 3.4.1  项目分析

下面对项目目录结构中的各个目录及文件进行说明。

shopM：项目根目录，在该目录下包含css、images、js目录，以及index.html文件。
css：css文件目录，该目录下存放CSS文件，用于添加自定义的样式代码。
images：图片文件目录，该目录下存放项目引用的图片文件。
js：JavaScript文件目录，该目录里存放封装首页页面功能的index.js文件。
index.html：首页页面文件。

# 先定一个小目标！

掌握首页整体布局的搭建，能够完成首页整体布局的搭建

3.4.2  搭建首页整体布局

# 在C:\code\chapter03目录下，新建shopM文件夹作为项目站点。然后在shopM文件夹下新建index.html文件作为项目首页，编写首页结构代码。

<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0">
  <title>首页</title>
</head>
<body>
  <div class=“hm_layout”>  <!-- 页面版心容器 -->
  </div>
</body>
</html>

3.4.2  搭建首页整体布局

# 在css目录下新建base.css文件，作为项目的公共样式文件，编写重置样式。

@charset "utf-8";
/* 重置样式 */
*,
::before,
::after {
  margin: 0;padding: 0;
  -webkit-tap-highlight-color: transparent;/* 清除点击高亮效果 */
  -webkit-box-sizing: border-box;               /* 处理主流移动端浏览器兼容 */
   box-sizing: border-box;
}

3.4.2  搭建首页整体布局

# 在css目录下新建base.css文件，作为项目的公共样式文件，编写重置样式。

body {
   font-size: 14px;
   font-family: "MicroSoft YaHei",sans-serif;  /* 设备默认字体 */
   background-color: #f5f5f5;
}
a {color: #333;text-decoration: none;}
a:hover {text-decoration: none;}
ul, ol {list-style: none;}
input, textarea {
  border: none;outline: none;resize: none;  /* 清除移动端输入框特有的样式 */
  -webkit-appearance: none;
}

3.4.2  搭建首页整体布局

# 编写公用样式。

/* 公用样式 */
.f_left {float: left;}
.f_right {float: right;}
/* 清除浮动 */
.clearfix::before,
.clearfix::after {content: "";height: 0;line-height: 0;display: block;visibility: hidden;clear: both;}
[class^="icon_"] {
  background: url("../images/sprites.png") no-repeat;
  background-size: 200px 200px;
}

3.4.2  搭建首页整体布局

.m_l10 {margin-left: 10px;}
.m_r10 {margin-right: 10px;}
.m_b10 {margin-bottom: 10px;}
.m_t10 {margin-top: 10px;}

# 打开C:\code\chapter03\shopM\index.html文件，在<head>标签中引入外部base.css文件和index.css文件，并在版心容器内添加各个功能模块内容。

<head>
  <link rel="stylesheet" href="css/base.css">
  <link rel="stylesheet" href="css/index.css">
</head>
<body>
  <div class="hm_layout">
    <header class="hm_header"></header><!-- 搜索栏 -->
    <div class="hm_banner"></div>	<!-- 轮播图 -->
    <nav class="hm_nav"></nav>	<!-- 导航栏 -->
    <main class="hm_product"></main>	<!-- 商品区 -->
  </div>
</body>

3.4.2  搭建首页整体布局

# 在css目录下创建index.css文件，编写版心容器样式代码。

@charset "utf-8";
/* 版心容器 */
.hm_layout {
  width: 100%;
  max-width: 640px;	/* 最大宽度 */
  min-width: 320px;	/* 最小宽度 */
  margin: 0 auto;
  position: relative;
}

3.4.2  搭建首页整体布局

# 先定一个小目标！

掌握搜索栏布局的搭建，能够实现搜索栏布局效果

3.4.3  搜索栏布局

# 搜索栏会定位在页面的顶端，搜索栏的宽度会随着浏览器窗口的大小而变化，并且透明度会在往下滑动时发生变化，搜索栏效果如图。

3.4.3  搜索栏布局

# 结构分析

整个搜索栏可以分为3部分，包括Logo、搜索框和登录链接，搜索栏的结构图。

3.4.3  搜索栏布局

# 结构分析

3.4.3  搜索栏布局

整个搜索栏包含在div.hm_header_box容器中。
搜索栏实现细节说明：
整个搜索栏包含在<header>容器中，采用固定定位，浮动在顶端。
父容器使用<div>标签定义，采用相对定位。
Logo使用<a>（左侧）标签定义，宽度固定，参照父容器进行定位。
搜索框使用<form>标签定义，存储用户搜索信息，宽度随浏览器窗口的大小而变化。
登录链接使用<a>（右侧）标签定义，宽度固定，参照父容器进行定位。

# <!-- 搜索栏 -->
<header class="hm_header">
  <div class="hm_header_box">
    <!-- Logo -->
    <a></a>
    <!-- 搜索框-->
    <form action="#"></form>
    <!-- 登录链接 -->
    <a></a>
  </div>
</header>

3.4.3  搜索栏布局

编写搜索栏结构
在index.html文件中编写搜索栏结构代码。

# /* 搜索栏 */
.hm_header {
  position: fixed;  left: 0;top: 0;height: 40px;width: 100%;
  z-index: 1000;   /* 避免搜索栏被遮挡 */
}
.hm_header_box {
  width: 100%;
  max-width: 640px; 		/* 设置最大宽度 */
  min-width: 320px; 		/* 设置最小宽度 */
  margin: 0 auto;		/* 设置水平居中 */
  background: rgba(201,21,35,0);	/* 设置透明度 */
  height: 40px; position: relative;
}

3.4.3  搜索栏布局

编写搜索栏样式
在index.css文件中编写搜索栏样式代码。

# <header class="hm_header">
  <div class="hm_header_box">
    <!-- Logo -->
    <a href="javascript:;" class="icon_logo"></a>
  </div>
</header>

3.4.3  搜索栏布局

编写Logo结构
在index.html文件中编写搜索栏Logo部分结构代码。

# .hm_header_box .icon_logo {
  width: 60px;
  height: 36px;
  position: absolute;
  background-position: 0 -103px;
  top: 4px;
  left: 10px;
}

3.4.3  搜索栏布局

编写Logo样式
在index.css文件中编写搜索栏Logo部分样式代码。

# 为了方便查看Logo效果，给.hm_header元素临时设置一个背景色background:#000，在浏览器中查看Logo效果。

3.4.3  搜索栏布局

# <header class="hm_header">
  <div class="hm_header_box">
    <!-- 搜索框 -->
    <form action="#">
      <span class="icon_search"></span>
      <input type="search" placeholder="搜索">
    </form>
  </div>
</header>

3.4.3  搜索栏布局

编写搜索框结构
在index.html文件中编写搜索框结构代码。

# .hm_header_box form {
  width: 100%;padding-left: 75px;padding-right: 50px;height: 40px;position: relative;
}
.hm_header_box form input {
  width: 100%;height: 30px;border-radius: 15px;margin-top: 5px;padding-left: 30px;
}
.hm_header_box form .icon_search {
  height: 20px;width: 20px;position: absolute;background-position: -60px -109px;top: 10px;left: 85px;
}

3.4.3  搜索栏布局

编写搜索框样式
在index.css文件中编写搜索框样式代码。

# 在浏览器中查看搜索框效果。

3.4.3  搜索栏布局

# <header class="hm_header">
  <div class="hm_header_box">
    <!-- 登录链接 -->
    <a href="#" class="login">登录</a>
  </div>
</header>

3.4.3  搜索栏布局

编写登录链接结构
在index.html文件中编写搜索栏登录链接结构代码。

# .hm_header_box .login {
  width: 50px;
  height: 40px;
  line-height: 40px;
  text-align: center;
  color: #fff;
  position: absolute;
  right: 0;
  top: 0;
  font-size: 15px;
}

3.4.3  搜索栏布局

编写登录链接样式
在index.css文件中编写搜索栏登录链接样式代码。

# 保存上述代码，在浏览器中查看登录链接效果。




搜索栏布局完成后，为了不影响后面其他模块的实现效果，我们需要去掉前面给.hm_header元素临时设置的背景色background:#000;。

3.4.3  搜索栏布局

# 先定一个小目标！

掌握轮播图布局的搭建，能够实现轮播图布局效果

3.4.4  轮播图布局

# “移动商城”搜索栏的下方是轮播图。网页中使用轮播图可以增加焦点信息量，可以在一个区域展示多张宣传图。

3.4.4  轮播图布局

# 结构分析

整个轮播图可以分为两部分，包括轮播图图片和轮播图指示器（图片轮播时随之变化的小圆点），轮播图结构设计图。

3.4.4  轮播图布局

# 结构分析

3.4.4  轮播图布局

轮播图实现细节说明。
整个轮播图包含在<div>容器中，采用相对定位。
轮播图图片使用<ul>、<li>布局。
轮播图指示器使用<ul>、<li>布局，用于控制轮播图播放序列。

# <!-- 轮播图 -->
<div class="hm_banner">
  <ul class="clearfix hm_bannerImg">
    <li><a href="javascript:;"><img src="images/1.jpg"></a></li>
    <li><a href="javascript:;"><img src="images/2.jpg"></a></li>
    <!-- ...此处省略8个<li>... -->
  </ul>
  <ul class="hm_bannerIndicator">
    <li class="active"></li>
    <li></li>
     <!-- ...此处省略6个<li>... -->
  </ul>
</div>

3.4.4  轮播图布局

编写轮播图结构
在index.html文件中编写轮播图结构代码。

# /* 轮播图 */
.hm_banner {
  width: 100%;
  overflow: hidden;
  position: relative;
}
.hm_bannerImg {width: 800%;}
.hm_bannerImg > li {
  width: 12.5%;float: left;
}
.hm_bannerImg > li img {
  width: 100%;display: block;
}

3.4.4  轮播图布局

编写轮播图样式
在index.css文件中编写轮播图样式代码。

# /* 指示器样式 */
.hm_bannerIndicator {
  width: 128px;height: 10px;
  /* 轮播图指示器居中显示 */
  position: absolute;left: 50%;bottom: 5px;transform: translateX(-50%);
}
.hm_bannerIndicator > li {
  width: 6px;height: 6px;border-radius: 3px;border: 1px solid #fff;float: left;margin-left: 10px;
}
.hm_bannerIndicator > li:first-of-type {margin-left: 0px;/* 重置第一个li的左边距为0 */}
.hm_bannerIndicator > li.active {background-color: #fff;}

3.4.4  轮播图布局

编写轮播图指示器样式
在index.css文件中编写轮播图指示器样式代码。

# 在浏览器中查看轮播图效果。

3.4.4  轮播图布局

# 先定一个小目标！

掌握导航栏布局的搭建，能够实现导航栏布局效果

3.4.5  导航栏布局

# 对于电商网站首页而言，无论是PC端还是移动端，导航栏都是不可缺少的内容。
移动端为了方便用户点触，一般会设计成独立图标的形式。

3.4.5  导航栏布局

# 结构分析

整个导航栏的页面结构都是由<ul>和<li>实现的，导航栏结构设计图如下。

3.4.5  导航栏布局

# <!-- 导航栏 -->
<nav class="hm_nav">
  <ul class="clearfix">
    <li>
      <a href="#">
        <img src="images/nav0.png" alt=""/>
        <p>分类查询</p>
      </a>
    </li>
    <!-- ...此处省略多个<li>... -->
  </ul>
</nav>

3.4.5  导航栏布局

编写导航栏结构
在index.html文件中编写导航栏结构代码。

# /* 导航栏 */
.hm_nav {
  width: 100%;background-color: #fff; /* 设置父元素.hm_nav宽度为100% */
}
.hm_nav li {  /* 设置父元素中的子元素li宽度为25%，一行显示4个 */
  width: 25%;float: left;text-align: center;margin-top: 5px; 
}
.hm_nav li img {
  width: 60px;
}
.hm_nav li p {
  line-height: 25px;
}

3.4.5  导航栏布局

编写导航栏样式
在index.css文件中编写导航栏样式代码。

# 先定一个小目标！

掌握商品区整体布局的搭建，能够实现商品区整体布局效果

3.4.6  商品区的整体布局

# 整个商品区可以分为3部分，分别是秒杀区块（掌上秒杀）、产品区块1（优惠活动）和
产品区块2（黑马超市）。

3.4.6  商品区的整体布局

# 结构分析

整个商品区包含在<main>容器内，并且秒杀区块（掌上秒杀）和产品区块1（优惠活动）和产品区块2（黑马超市）这3部分的头部内容和主体内容结构相似。商品区整体结构如下。

3.4.6  商品区的整体布局

# <!-- 商品区 -->
<main class="hm_product">
  <section class="product_box">             <!-- 秒杀区块 -->
    <div class="product_box_tit"></div>  <!-- 头部内容 -->
    <div class="product_box_con"></div> <!-- 主体内容 -->
  </section>
  <!-- 产品区块1 -->
  <section class="product_box">
    <div class="product_box_tit"></div> <!-- 头部内容 -->
    <div class="product_box_con"></div> <!-- 主体内容 -->
  </section>

3.4.6  商品区的整体布局

编写商品区结构
在index.html文件中编写商品区结构代码。

# 3.4.6  商品区的整体布局

编写商品区结构
在index.html文件中编写商品区结构代码。

<!-- 产品区块2 -->
  <section class="product_box">
    <div class="product_box_tit"></div>   <!-- 头部内容 -->
    <div class="product_box_con"></div> <!-- 主体内容 -->
  </section>
</main>

# /* 商品区 */
.hm_product {
  width: 100%;
}
.product_box {
  width: 100%;
  margin-top: 10px;
  background-color: #fff;
  box-shadow:0 0 1px #e0e0e0; /* 添加阴影 */
}

3.4.6  商品区的整体布局

编写商品区样式
在index.css文件中编写商品区样式代码。

# 先定一个小目标！

掌握商品区秒杀区块布局的搭建，能够实现秒杀区块的布局效果

3.4.7  商品区-秒杀区块布局

# 3.4.7  商品区-秒杀区块布局

秒杀区块包含在<section>容器中，秒杀区块结构。

结构分析

# <!-- 秒杀区块 -->
<section class="product_box hm_sk clearfix">
  <!-- 头部内容 -->
  <div class="product_box_tit">
    <div class="f_left m_l10">
      <span class="sk_icon m_l10"></span>	   <!-- 秒杀图标 -->
      <span class="sk_name m_l10">掌上秒杀</span><!-- 秒杀文字 -->

3.4.7  商品区-秒杀区块布局

编写秒杀区块头部结构
在index.html文件中编写秒杀区块头部内容结构代码。

# <div class="sk_time m_l10">		    <!-- 秒杀时间 -->
        <span>0</span><span>0</span><span>:</span><span>0</span>
        <span>0</span<span>:</span><span>0</span<span>0</span>
      </div>
    </div>
    <div class="f_right m_r10"><a href="#">更多></a></div>
  </div>
  <!-- 主体内容 -->
  <div class="product_box_con"></div>
</section>

3.4.7  商品区-秒杀区块布局

编写秒杀区块头部结构
在index.html文件中编写秒杀区块头部内容结构代码。

# /* 秒杀区块-头部内容 */
.hm_sk{   /* 设置一个样式标记：秒杀块样式开始 */   }
.hm_sk .product_box_tit {border-bottom: none;  /* 去除底部边框 */  padding-left: 0; }
/* 秒杀图标 */
.hm_sk .sk_icon { background: url("../images/seckill-icon.png") no-repeat;
  background-size: 16px 20px;width: 16px;height: 20px;float: left;margin-top: 3px;
}

3.4.7  商品区-秒杀区块布局

编写秒杀区块头部样式
在index.css文件中编写秒杀区块头部内容样式代码。

# /* 秒杀文字 */
.hm_sk .sk_name { color: #d8505c;font-size: 15px;float: left; }
/* 秒杀时间 */
.hm_sk .sk_time { float: left;margin-top:8px; }
.hm_sk .sk_time span {
  float: left;width: 15px;height: 15px;line-height: 15px;text-align: center;background: #333;
  color: #fff;margin-left: 3px;
}
.hm_sk .sk_time span:nth-child(3n) {background: transparent;color: #333;width: 5px;}

3.4.7  商品区-秒杀区块布局

编写秒杀区块头部样式
在index.css文件中编写秒杀区块头部内容样式代码。

# 在浏览器中查看秒杀区块头部内容页面效果。

3.4.7  商品区-秒杀区块布局

# <!-- 主体内容 -->
<div class="product_box_con">
  <ul class="clearfix">
    <li>
      <a href="javascript:;"><img src="images/detail01.jpg" /></a>
      <p>&yen;10.00</p><p>&yen;100.00</p>
    </li>
    <li>

3.4.7  商品区-秒杀区块布局

编写秒杀区块主体内容结构
在index.html文件中编写秒杀区块主体内容结构代码。

# <li>
      <a href="javascript:;"><img src="images/detail02.jpg" /></a>
      <p>&yen;10.00</p><p>&yen;100.00</p>
    </li>
    <li>
      <a href="javascript:;"><img src="images/detail01.jpg" /></a>
      <p>&yen;10.00</p><p>&yen;100.00</p>
    </li>
  </ul>
</div>

3.4.7  商品区-秒杀区块布局

编写秒杀区块主体内容结构
在index.html文件中编写秒杀区块主体内容结构代码。

# /* 秒杀区块-主体内容 */
.hm_sk .product_box_con {
  padding: 20px;
}
.hm_sk .product_box_con > ul {
  width: 100%;
}
.hm_sk .product_box_con > ul > li {
  width: 33.33%;float: left;text-align: center;
}
.hm_sk .product_box_con > ul > li img {
  width: 60%;
  display: inline-block;
  /* 清除文本基线，居中对齐 */
}

3.4.7  商品区-秒杀区块布局

编写秒杀区块主体内容样式
在index.css文件中编写秒杀区块主体内容样式代码。

# .hm_sk .product_box_con > ul > li >p:first-of-type {
   color: #d8505c;
   padding-top: 5px;
}
.hm_sk .product_box_con > ul > li >p:last-of-type {
  text-decoration: line-through;
  color: #666;
  padding-top: 5px;
}

3.4.7  商品区-秒杀区块布局

编写秒杀区块主体内容样式
在index.css文件中编写秒杀区块主体内容样式代码。

# 在浏览器中查看秒杀区块主体内容页面效果。

3.4.7  商品区-秒杀区块布局

# 先定一个小目标！

掌握商品区产品区块1布局的搭建，能够实现产品区块1的布局效果

3.4.8  商品区-产品区块1布局

# 3.4.8  商品区-产品区块1布局

产品区块1包含在<section>容器中，产品区块1结构。

结构分析

# <!-- 产品区块1 -->
<section class="product_box">
  <!-- 头部内容 -->
  <div class="product_box_tit”><h3>优惠活动</h3></div>
  <!-- 主体内容 -->
  <div class="product_box_con clearfix">
    <a href="javascript:;" class="f_left w_50 b_right"><img src="images/cp1.jpg" /></a>
    <a href="javascript:;" class="f_right w_50 b_bottom"><img src="images/cp2.jpg" alt=""/></a>
    <a href="javascript:;" class="f_right w_50 "><img src="images/cp3.jpg" alt=""/></a>
  </div>
</section>

3.4.8  商品区-产品区块1布局

编写产品区块1结构
在index.html文件中编写产品区块1结构代码。

# .product_box > .product_box_tit { 
width: 100%;height: 30px;line-height: 30px;border-bottom: 1px solid #ccc; padding-left: 30px;}
.product_box > .product_box_tit > h3 {  position: relative; color: #666;font-weight: normal;font-size: 15px;}
.product_box > .product_box_tit > h3::before {
  content: "";  position: absolute;  width: 3px;height: 12px;background-color: #e92322;top: 9px;left: -8px;}
.w_50 {display: block;width: 50%; }
.w_50 > img {width: 100%;display: block; }
.b_right {border-right: 1px solid #ccc; }
.b_bottom {border-bottom: 1px solid #ccc; }

3.4.8  商品区-产品区块1布局

编写产品区块1样式
在index.css文件中编写产品区块1样式代码。

# 保存上述代码，在浏览器中查看产品区块1页面效果。

3.4.8  商品区-产品区块1布局

# 先定一个小目标！

掌握商品区产品区块2布局的搭建，能够实现产品区块2的布局效果

3.4.9  商品区-产品区块2布局

# 3.4.9  商品区-产品区块2布局

产品区块2包含在<section>容器中，产品区块2结构。

结构分析

# 代码实现

在index.html文件中编写产品区块2结构代码。

<!-- 产品区块2 -->
<section class="product_box">
  <!-- 头部内容 -->
  <div class="product_box_tit"><h3>黑马超市</h3></div>
  <!-- 主体内容 -->
  <div class="product_box_con clearfix">
    <a href="javascript:;" class="f_right w_50 b_left"><img src="images/cp4.jpg" alt=""/></a>
    <a href="javascript:;" class="f_left w_50 b_bottom"><img src="images/cp5.jpg" alt=""/></a>
    <a href="javascript:;" class="f_left w_50"><img src="images/cp6.jpg" alt=""/></a>
  </div>
</section>

3.4.9  商品区-产品区块2布局

# 保存上述代码，在浏览器中查看产品区块2页面效果。

3.4.9  商品区-产品区块2布局

# 先定一个小目标！

掌握首页搜索栏模块的实现，能够独立完成该模块功能

3.4.10  实现首页搜索栏模块效果

# 3.4.10  实现首页搜索栏模块效果

搜索栏模块背景默认是透明的，当用户向上滑动内容时，搜索栏模块背景的透明度会慢慢加深，直到整个轮播图模块移出当前屏幕外，搜索栏模块背景会保持一个固定的透明色。

如果用户向下滑动内容，搜索栏模块背景的透明度会慢慢变浅，直到搜索栏模块固定在顶部时背景色变为透明。

功能分析

# 3.4.10  实现首页搜索栏模块效果

搜索栏需要实现以下3个效果：
搜索栏固定浮动在顶部。
搜索栏的宽度会随着浏览器窗口的大小而变化。
搜索栏的透明度会在往下滑动时透明度发生变化。

# // 入口函数，页面加载完成之后执行
// 添加search()方法
window.onload = function() {
  search(); // 搜索栏
};

3.4.10  实现首页搜索栏模块效果

创建index.js文件
在C:\code\chapter03\shopM\js目录下，新建index.js文件，
编写搜索栏模块效果。

添加search()方法
在index.js文件的window.onload = function(){}方法中添加search()方法。

# // 搜索栏
function search() {
  // 1 获取当前banner元素的高度
  var banner = document.querySelector('.hm_banner');
  var bannerHeight = banner.offsetHeight;
  var search = document.querySelector('.hm_header');
  window.onscroll = function () {  // 监听屏幕滚动
    （代码见下一页）
  }
}

3.4.10  实现首页搜索栏模块效果

编写search()的具体实现

# // 2 获取当前屏幕滚动时，banner滚动出屏幕的距离
    var offsetTop  = document.body.scrollTop || document.documentElement.scrollTop;
    // 3 计算比例值，获取透明度，设置背景颜色的样式
    var opacity = 0; // 默认透明度为0
    // 判断如果当banner还没有完全滚出屏幕，才有必要去计算并设置透明度
    if (offsetTop < bannerHeight) {
      opacity = offsetTop / bannerHeight;
      search.style.backgroundColor = "rgba(201,21,35," + opacity + ")"; // 设置样式
    }

3.4.10  实现首页搜索栏模块效果

编写search()的具体实现

# 保存上述代码，在浏览器中当用户向上滑动内容时，搜索栏模块背景的透明度会慢慢加深。

3.4.10  实现首页搜索栏模块效果

# 当超出轮播图模块高度时，搜索栏模块背景会保持一个固定的颜色。

3.4.10  实现首页搜索栏模块效果

# 先定一个小目标！

掌握首页倒计时效果的实现，能够能够独立完成该模块功能

3.4.11  实现首页倒计时效果

# 3.4.11  实现首页倒计时效果

功能分析

倒计时需要实现以下3个效果：
设置初始的倒计时时间。
如果倒计时时间已经完成清除定时器。
如果倒计时时间没有完成，获取剩余时间中的时分秒并显示在页面中。

# // 入口函数，页面加载完成之后执行
// 添加search()方法
window.onload = function() {
  search();		// 搜索栏
  downTime();	// 倒计时
};

3.4.11  实现首页倒计时效果

实现秒杀倒计时效果
在index.js文件中的window.onload = function(){}方法中添加
downTime()方法。

# // 倒计时
function downTime() {
  var spans = document.querySelector('.sk_time').querySelectorAll('span');
  var totalTime = 1 * 60 * 60;
  var timer = setInterval(() => { // 开启定时器
    totalTime--;
    if (totalTime < 0) {	// 判断倒计时时间是否已经完成
      clearInterval(timer);	// 清除定时器
      return;
    }

3.4.11  实现首页倒计时效果

实现秒杀倒计时效果
编写downTime()的具体实现。

# 3.4.11  实现首页倒计时效果

实现秒杀倒计时效果
编写downTime()的具体实现。

// 获取剩余时间中的 时分秒
    var h = Math.floor(totalTime / 3600);            // 获取小时数
    var m = Math.floor(totalTime % 3600 / 60);  // 获取分钟数
    var s =  Math.floor(totalTime % 60);              // 获取秒钟数
    // 赋值，将时间填充到span中
    spans[0].innerHTML = Math.floor(h / 10);
    spans[1].innerHTML = Math.floor(h % 10);
    spans[3].innerHTML = Math.floor(m / 10);
    spans[4].innerHTML = Math.floor(m % 10);
    spans[6].innerHTML = Math.floor(s / 10);
    spans[7].innerHTML = Math.floor(s % 10);
  }, 1000);
}

# 在浏览器中查看倒计时效果。

3.4.11  实现首页倒计时效果

# 先定一个小目标！

掌握首页轮播图自动轮播效果的实现，能够独立完成该模块功能

3.4.12  实现首页轮播图自动轮播效果

# 功能分析

3.4.12  实现首页轮播图自动轮播效果

轮播图需要实现以下5个效果：
使用定时器和过渡让轮播图片自动滚动起来；
轮播器指示点也要随着轮播图图片滚动起来。
使用touch事件实现图片滑动；
当滑动距离不超过特定屏幕宽度的时候，进行回弹操作定位回去 ；
当滑动距离超过特定屏幕宽度的时候，进行翻页操作滚动到下一张。

# 代码实现

如果要实现轮播图自动循环轮播效果，需要在原始图片的首尾添加图片，具体操作为在轮播图开始位置添加原始的最后一张图片，在轮播图最后位置添加原始的第一张图片。

在实际开发中，轮播图是通过服务器进行返回的，因为服务器返回的轮播图数量不固定，所以应该通过JavaScript代码动态添加首尾图片，而不是手动添加首尾图片。

3.4.12  实现首页轮播图自动轮播效果

# /* 轮播图 */
.hm_banner{
  width: 100%;  
  overflow: hidden;
  position: relative;
}
.hm_bannerImg{
  width: 1000%;      /* 将宽度设置为1000%，这是因为此时需要存放10张图片 */
  position: relative; /* 当前元素必须使用relative相对定位，否则父容器无法获取正确的高度 */
  left: -100%;
}

3.4.12  实现首页轮播图自动轮播效果

修改轮播图样式
在index.css文件中修改轮播图样式代码。

# 3.4.12  实现首页轮播图自动轮播效果

修改轮播图样式
在index.css文件中修改轮播图样式代码。

.hm_bannerImg > li{
  width: 10%;         /* li的宽度相应需要改为10% */
  float: left;
}

# // 入口函数，页面加载完成之后执行
// 添加search()方法
window.onload = function() {
  search();		// 搜索栏
  downTime();	// 倒计时
  bannerEffect();	// 轮播图
};

3.4.12  实现首页轮播图自动轮播效果

修改轮播图逻辑
打开index.js文件，在window.onload = function(){}方法中添加bannerEffect()方法。

# function bannerEffect() { 
  var banner = document.querySelector('.hm_banner'); 	// 获取轮播图结构
  var imgBox = banner.querySelector('ul:first-of-type');	// 获取轮播图容器
  var first = imgBox.querySelector('li:first-of-type'); 	// 获取原始的第一张图片
  var last = imgBox.querySelector('li:last-of-type');  	// 获取原始的最后一张图片
  imgBox.appendChild(first.cloneNode(true)); 
  imgBox.insertBefore(last.cloneNode(true), imgBox.firstChild);

3.4.12  实现首页轮播图自动轮播效果

动态添加首尾图片
编写bannerEffect()的具体实现。

# // 设置对应的样式
  var lis = imgBox.querySelectorAll('li');		// 获取所有li元素
  var count = lis.length;				// 获取li元素的数量
  var bannerWidth = banner.offsetWidth; 		// 获取当前banner的宽度
  imgBox.style.width = count * bannerWidth + 'px'; 	// 设置图片盒子的宽度
  for (var i = 0; i < lis.length; i++){ 
    lis[i].style.width = bannerWidth + ‘px’;		// 设置每一个li元素的宽度
 }
  var index = 1;   // 定义图片索引，因为图片有了一个宽度的默认偏移，所以索引为1
  imgBox.style.left = -bannerWidth + 'px';  		// 设置默认的偏移

3.4.12  实现首页轮播图自动轮播效果

动态添加首尾图片
编写bannerEffect()的具体实现。

# 3.4.12  实现首页轮播图自动轮播效果

动态添加首尾图片
编写bannerEffect()的具体实现。

// 当屏幕变化时，重新计算宽度
  window.onresize = function () {
    bannerWidth = banner.offsetWidth;		// 获取当前banner的宽度，覆盖全局宽度
    imgBox.style.width = count * bannerWidth + 'px';	// 设置图片盒子的宽度
    for (var i = 0; i < lis.length; i++){ lis[i].style.width = bannerWidth + 'px'; // 设置每一个li元素的宽度}
    imgBox.style.left = -index * bannerWidth + 'px'; 	// 重新设置偏移
  }
}

# 保存上述代码，在浏览器中审查元素，<li>元素由之前的8个变为了10个，
说明已经动态添加完成首尾两张图片。

3.4.12  实现首页轮播图自动轮播效果

# // 实现自动轮播，封装定时器
var timerId;
var startTime = function () {
  timerId = setInterval(function () {
    index++;			//  下一张
    imgBox.style.transition = 'left 0.5s ease-in-out';
    imgBox.style.left = (-index * bannerWidth) + 'px'; 	// 向左偏移是负值

3.4.12  实现首页轮播图自动轮播效果

实现自动轮播功能
在步骤（2）中window.onresize代码外部编写定时器代码。

# setTimeout(function () { 	// 添加延时操作，等过渡完成之后，再进行判断
      // 判断是否到最后一张，如果是则执行如下操作
      if (index == count - 1) {
        index = 1;		// 索引为1
        imgBox.style.transition = 'none'; 	// 关闭过渡效果
        imgBox.style.left = (-index * bannerWidth) + 'px';
      }
    }, 500);
  }, 2000);
}
startTime();	// 开启定时器

3.4.12  实现首页轮播图自动轮播效果

实现自动轮播功能
在步骤（2）中window.onresize代码外部编写定时器代码。

# 先定一个小目标！

掌握首页轮播图手动轮播效果的实现，能够独立完成该功能模块

3.4.13  实现首页轮播图手动轮播效果

# 功能分析

3.4.13  实现首页轮播图手动轮播效果

轮播图的手动轮播效果，需要用到touch相关事件，如touchstart、touchmove、touchend。
手动轮播实现细节分为三步：
记录手指的起始位置；
记录手指在滑动过程中的位置，计算出相对于起始位置的偏移值，通过left样式实现图片的偏移；
在手指松开后，判断当前滑动的距离，如果超出指定的范围，就进行翻页操作（去到下一张），否则进行回弹操作（回到上一张）。

# 3.4.13  实现首页轮播图手动轮播效果

// 设置全局变量，开始坐标值、滑动过程中的坐标值、两者的差异值
var startX, moveX, distanceX;
// 为图片添加触摸事件-触摸开始
imgBox.addEventListener('touchstart', function (e) {    
  clearInterval(timerId); 		 // 清除定时器
  startX = e.targetTouches[0].clientX;  	// 获取当前手指的起始位置
});

实现图片的偏移
记录手指的起始位置、手指在滑动过程中的位置，计算出相对于起始位置的偏移值，通过left样式实现图片的偏移。
在bannerEffect()方法中，自动轮播代码完成后编写如下代码。

# 3.4.13  实现首页轮播图手动轮播效果

// 为图片添加触摸事件-滑动过程
imgBox.addEventListener('touchmove', function (e) {
  moveX = e.targetTouches[0].client;	// 记录手指在滑动过程中的位置
  distanceX = moveX - startX;	// 计算坐标的差异
  imgBox.style.transition = 'none'; 	// 为了保证效果正常，将之前可能添加的过渡样式清除
  imgBox.style.left = (-index * bannerWidth + distanceX) + 'px'; // 实现元素的偏移
});

实现图片的偏移

# // 为图片添加触摸事件-触摸结束
imgBox.addEventListener('touchend', function (e) { 
  if (Math.abs(distanceX) > 100) {
    // 判断滑动的方向
    if (distanceX > 0) { 
      index--;     // 上一张
    } else { 
      index++;   // 下一张
    }
    imgBox.style.transition = 'left 0.5s ease-in-out'; // 翻页，下一张图
    imgBox.style.left = -index * bannerWidth + 'px';

3.4.13  实现首页轮播图手动轮播效果

实现翻页和回弹
在手指松开后，判断当前滑动的距离，进行翻页或回弹操作。

# } else if (Math.abs(distanceX) > 0) { // 保证用户确实进行过滑动操作
    imgBox.style.transition = 'left 0.5s ease-in-out'; // 回弹操作，返回上一张图
    imgBox.style.left = -index * bannerWidth + 'px';
  }
});

3.4.13  实现首页轮播图手动轮播效果

实现翻页和回弹
在手指松开后，判断当前滑动的距离，进行翻页或回弹操作。

# 在浏览器中查看轮播图效果，当定位到第一张轮播图，然后向前手动滑动轮播图，此时会出现空白的区域。

3.4.13  实现首页轮播图手动轮播效果

# imgBox.addEventListener('webkitTransitionEnd', function () {
  if (index == count - 1) {  // 如果滑动到了最后一张(count-1)，就回到索引1
    index = 1;
    imgBox.style.transition = 'none';		  // 清除过渡
    imgBox.style.left = -index * bannerWidth + 'px';	  // 设置偏移
  } else if (index == 0) {  // 如果滑动到了第一张，回到索引count-2
    index = count - 2;
    imgBox.style.transition = 'none';		  // 清除过渡
    imgBox.style.left = -index * bannerWidth + 'px';	  // 设置偏移
  }
  startTime();			  // 重新开启定时器
});

3.4.13  实现首页轮播图手动轮播效果

解决空白区域问题
解决手动滑动轮播图时出现空白区域的问题。

# 在浏览器中查看轮播图效果，当定位到第一张轮播图，然后向前手动滑动轮播图此时不会出现空白区域。

3.4.13  实现首页轮播图手动轮播效果

在上图中，当快速滑动轮播图时也会出现空白的区域，这是因为在滑动时还没有等过渡事件触发，就再一次触发了touchmove事件，所以快速滑动会出现空白区域。解决方法：限制touchmove事件触发的条件，让其不能任意触发。

# // 设置全局变量，开始坐标值、滑动过程中的坐标值、两者的差异值
var startX, moveX, distanceX;
var isEnd = true;
imgBox.addEventListener('touchstart', function (e) {// 为图片添加触摸事件-触摸开始
  clearIntervar(timerId);		// 清除定时器
  startX = e.targetTouches[0].clientX;	// 获取当前手指的起始位置
}

3.4.13  实现首页轮播图手动轮播效果

快速滑动轮播图时出现轮播图区域空白的问题
创建一个变量isEnd，标记当前过渡效果是否执行完毕。

# // 为图片添加触摸事件-滑动过程
imgBox.addEventListener('touchmove', function (e) {
  if(isEnd == true){
    moveX = e.targetTouches[0].clientX;  // 记录手指在滑动过程中的位置
    distanceX = moveX - startX; 	   // 计算坐标的差异
    imgBox.style.transition = 'none';        // 为了保证效果正常，将之前可能添加的过渡样式清除
    imgBox.style.left = (-index * bannerWidth + distanceX) + 'px'; // 实现元素的偏移
  }
});

3.4.13  实现首页轮播图手动轮播效果

快速滑动轮播图时出现轮播图区域空白的问题
判断变量isEnd是否为true。

# // 为图片添加触摸事件-触摸结束
imgBox.addEventListener('touchend', function (e) {
  isEnd = false; 
  if (Math.abs(distanceX) > 100) {// 判断滑动的方向
    ……（原有代码略）
  }
  // 将上一次move产生的数据重置为0
  startX = 0;
  moveX = 0;
  distanceX = 0;
});

3.4.13  实现首页轮播图手动轮播效果

快速滑动轮播图时出现轮播图区域空白的问题
在执行本次拖动后，需要松开手指才可以执行下一次的拖动，所以需要在touchend事件中，将isEnd标记为false，表示当前过渡效果正在执行。

# 3.4.13  实现首页轮播图手动轮播效果

快速滑动轮播图时出现轮播图区域空白的问题
在过渡效果完成之后，需要将isEnd重置为true。

imgBox.addEventListener('webkitTransitionEnd', function () {
   ……（原有代码略）
  setTimeout(function() {
    isEnd = true;
    clearInterval(timerId);	// 清除之前添加的定时器
    startTime();		// 重新开启定时器
  }, 1000);
});

# // 标记点
var setIndicator = function (index) {
  var indicators = banner.querySelector('ul:last-of-type').querySelectorAll('li');// 获取点标记
  for (var i = 0; i < indicators.length; i++){
    indicators[i].classList.remove('active');
  }
  indicators[index-1].classList.add('active');
} 
// 实现自动轮播，封装定时器

3.4.13  实现首页轮播图手动轮播效果

实现轮播图指示器点标记效果
当图片轮播时，切换相应的轮播图指示器点标记。

# imgBox.addEventListener('webkitTransitionEnd', function () {
  // 原代码
  setIndicator(index);
  setTimeout(function() {
    isEnd = true;
    clearInterval(timerId);	// 清除之前添加的定时器
    startTime();	// 重新开启定时器
  }, 1000);
});

3.4.13  实现首页轮播图手动轮播效果

实现轮播图指示器点标记效果
图片轮播完成之后，再切换轮播图指示器点标记样式。

# 在浏览器中查看点标记样式随着轮播图的改变而进行了切换。

3.4.13  实现首页轮播图手动轮播效果

# 本章小结

本章首先介绍了流式布局和视口相关内容，然后讲解了移动端常用的touch事件相关内容，为后面移动端项目的实现夯实基础，最后通过对本章内容的学习完成移动商城项目首页功能模块。通过对本章项目的学习，读者需要将所学的技术知识运用到实际项目开发中。

本

章

小

结
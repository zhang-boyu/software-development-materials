# 第5章  Bootstrap响应式移动Web开发

# 学习目标/Target

# 章节概述/ Summary

在前面的章节中讲解了响应式Web设计，相信会有一部分读者觉得实现响应式是个很复杂的过程，需要调整很多细节。本章将会使用一个工具来让响应式变得容易实现，它就是Bootstrap。Bootstrap为用户提供了一套响应式的移动设备优先的流式栅格系统，能够自适应于多种设备屏幕大小，提高前端开发的工作效率。本章将针对Bootstrap响应式移动Web开发进行详细讲解。

# 目录/Contents

# Bootstrap简介

5.1

# 先定一个小目标！

了解Bootstrap的概念，能够说出Bootstrap的基本内容

5.1.1  Bootstrap的概念

# Bootstrap是由Twitter公司的设计师开发的一个前端开源框架，它于2011年8月在GitHub上发布，一经推出，就非常受欢迎。

Bootstrap是基于HTML、CSS和JavaScript等前端技术实现的框架。

Bootstrap由来

5.1.1  Bootstrap的概念

# 框架就是一套架构，具有一套比较完整的解决方案，而且控制权在框架本身。

怎么理解框架

5.1.1  Bootstrap的概念

# Bootstrap是一款用于网页开发的框架，它拥有样式库、组件和插件，使用者需要按照框架的规范进行开发。

怎么理解Bootstrap框架

5.1.1  Bootstrap的概念

# Bootstrap框架中提供的内容如下。

基本结构：Bootstrap提供了一个带有栅格系统、链接样式、背景的基本结构。

CSS：Bootstrap自带了全局的CSS设置、预定义的基本HTML元素样式、可扩展的class，以及一个先进的栅格系统。

布局组件：Bootstrap含了十几个可重用的组件，用于创建图像、下拉菜单、导航、警告框、弹出框等。

图标库：Bootstrap拥有开源的图标库，图标文件的格式是SVG，能够轻松快捷地进行缩放，并可以通过CSS设置样式。

JavaScript插件：Bootstrap包含十几个自定义的jQuery插件，可以直接包含所有的插件，也可以逐个包含这些插件。

定制：开发人员可以定制Bootstrap的组件、Less变量和jQuery插件来得到一套自定义的版本，提高了开发的灵活性。

5.1.1  Bootstrap的概念

# 先定一个小目标！

了解Bootstrap的特点，能够说出具体特点

5.1.2  Bootstrap的特点

# 使用Bootstrap可以构建出非常优雅的前端界面，而且占用资源非常小。

Bootstrap特点

5.1.2  Bootstrap的特点

移动设备优先：移动设备优先的样式贯穿于整个库。

浏览器支持度高：主流浏览器都支持Bootstrap，包括IE（支持IE 9+）、Firefox、Chrome、Safari等。

学习成本低，容易上手：只需使用者具备HTML、CSS和JavaScript的基础知识。

响应式设计：Bootstrap框架为用户提供了一套响应式的移动设备优先的流式栅格系统，能够自适应于台式机、平板计算机和手机的屏幕大小。

良好的代码规范：Bootstrap为开发人员创建接口提供了一个简洁统一的解决方案，减少了测试的工作量，使开发人员站在巨人的肩膀上，不重复造轮子。

强大的组件：Bootstrap包含功能强大的内置组件。

# Bootstrap下载和使用

5.2

# 5.2.1  下载Bootstrap预编译文件

Bootstrap提供了3种下载方式：

第1种方式是下载Bootstrap预编译文件。

第2种方式是下载源文件进行手动编译。

第3种方式是使用CDN来引入。

上述第1种方式Bootstrap预编译文件使用起来比较简单，它不包含文档和最初的源代码文件，可以直接引入到Web项目中。在这里我们选择第1种方式进行讲解。

# 先定一个小目标！

掌握Bootstrap预编译文件的下载，能够独立完成Bootstrap相应版本下载

5.2.1  下载Bootstrap预编译文件

# 下载Bootstrap预编译文件

打开浏览器，访问Bootstrap的官方网站，手动下载bootstrap-4.6.0-dist.zip文件。

5.2.1  下载Bootstrap预编译文件

http://getbootstrap.com/

# 下载成功后，解压缩ZIP文件，将看到下面的文件和目录结构。

5.2.1  下载Bootstrap预编译文件

bootstrap-4.6.0-dist/
├── css/
└── js/

解压缩文件

# bootstrap-4.6.0-dist目录下css和js文件中所有子文件。

5.2.1  下载Bootstrap预编译文件

bootstrap-4.6.0-dist/
├── css/
│   ├── bootstrap.css
│   ├── bootstrap.css.map
│   ├── bootstrap.min.css
│   ├── bootstrap.min.css.map
│   ├── bootstrap-grid.css
│   ├── bootstrap-grid.css.map
│   ├── bootstrap-grid.min.css
│   ├── bootstrap-grid.min.css.map
│   ├── bootstrap-reboot.css
│   ├── bootstrap-reboot.css.map
│   ├── bootstrap-reboot.min.css
│   └── bootstrap-reboot.min.css.map

bootstrap-4.6.0-dist/
├── js/
│  ├── bootstrap.bundle.js
│  ├── bootstrap.bundle.js.map
│  ├── bootstrap.bundle.min.js
│  ├── bootstrap.bundle.min.js.map
│  ├── bootstrap.js
│  ├── bootstrap.js.map
│  ├── bootstrap.min.js
│  └── bootstrap.min.js.map

# 5.2.1  下载Bootstrap预编译文件

bootstrap-4.6.0-dist目录结构中针对文件名的相关说明。

文件名带有min的文件是编译后的压缩版本，可以用于生产环境，文件比较小。

不带min的文件可以用于开发环境，源码比较清晰，容易阅读，便于代码调试。

文件名带有map文件是Source Map文件，用于查询精确的样式位置。

另外，该目录结构中没有jQuery文件，如果项目中需要使用的话，可以自行下载jQuery文件。

# 先定一个小目标！

掌握Bootstrap预编译文件的引入，能够在页面中正确引入编译好的核心CSS和JavaScript文件

5.2.2  引入Bootstrap预编译文件

# 5.2.2  引入Bootstrap预编译文件

在HTML中引入预编译文件中的核心CSS和JavaScript文件

在网页中引入Bootstrap框架。

使用<script>标签引入JavaScript文件。

使用<link>标签引入CSS文件。

需要注意的是，Bootstrap中的JavaScript效果都是基于jQuery的。如果想要使用JavaScript效果，必须将jquery.min.js文件放在bootstrap.min.js文件前面引入。

由于Bootstrap没有提供jquery.min.js文件，所以我们需要手动下载该文件或使用CDN方式进行引入jquery.min.js文件。

# 5.2.2  引入Bootstrap预编译文件

使用CDN方式引入的jquery.min.js文件

<!-- 引入Bootstrap 4.6.0核心CSS文件 -->
<link rel="stylesheet" href="bootstrap-4.6.0-dist/css/bootstrap.min.css">
<!-- jQuery文件，务必在bootstrap.min.js之前引入 -->
<script src="https://cdn.staticfile.org/jquery/3.2.1/jquery.min.js"></script>
<!-- 引入Bootstrap 4.6.0核心JavaScript文件 -->
<script src="bootstrap-4.6.0-dist/js/bootstrap.min.js"></script>

# 先定一个小目标！

掌握Bootstrap初始模板的创建，能够独立完成模板文件代码编写

5.2.3  创建Bootstrap初始模板

# Bootstrap的使用

5.2.3  创建Bootstrap初始模板

（1）将bootstrap-4.6.0-dist文件夹放到C:\code\chapter05目录下。

（2）下载jquery-3.5.1.slim.min.js文件和popper.min.js文件至本地。

（3）在chapter05目录下创建一个index.html文件，在该文档中直接引入编译好的CSS和JavaScript文件。

# 使用Bootstrap框架创建初始模板，在页面中输出Hello World，效果如图：

5.2.3  创建Bootstrap初始模板

# Bootstrap布局容器

5.3

# 先定一个小目标！

掌握布局容器，能够灵活运用.container类和.container-ﬂuid类完成对不同容器宽度的设置

5.3.1  初识布局容器

# .container类用于固定宽度并支持响应式布局的容器。

5.3.1  初识布局容器

布局容器

.container-fluid类用于在不同设备下设置100%宽度，占据全部视口的容器。

<div class="container">
   …
<div>

1

2

<div class="container-fluid">
   …
<div>

# 使用.container类和.container-fluid类设置布局容器，效果如图：

5.3.1  初识布局容器

# 对比.container类和.container-fluid类
在C:\code\chapter05\demo01.html文件中，编写代码。

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0,  shrink-to-fit=no">
  <link rel="stylesheet" href="bootstrap-4.6.0-dist/css/bootstrap.min.css">
  <title>布局容器</title>
</head>
<body>
  <div class="container-fluid bg-dark text-light mb-1">.container-fluid设置布局容器</div>
  <div class="container bg-dark text-light">.container设置布局容器</div>
</body>
</html>

STEP  01

5.3.1  初识布局容器

# 测试网页程序
运行demo01.html程序，演示两种容器的对比效果。

STEP  02

运行demo01.html文件

5.3.1  初识布局容器

# 先定一个小目标！

掌握响应式布局容器的使用，能够合理利用响应式容器完成页面的布局

5.3.2  响应式布局容器

# 5.3.2  响应式布局容器

.container-{breakpoint}类创建响应式布局容器，目的是在屏幕分辨率要求不同的情况下，容器宽度的显示规则更加灵活。breakpoint允许的取值有sm、md、lg和xl。

<div class="container-{sm|md|lg|xl}">
   …
<div>

响应式布局容器

# 5.3.2  响应式布局容器

| 类 | 布局容器宽度 |  |  |  |  |
|---|---|---|---|---|---|
|  | 超小屏幕         <576 | 小屏幕
∈[576, 768） | 中等屏幕
∈[769, 992） | 大屏幕
∈[992,1200） | 超大屏幕
≥1200 |
| .container | 100% | 540px | 720px | 960px | 1140px |
| .container-sm | 100% | 540px | 720px | 960px | 1140px |
| .container-md | 100% | 100% | 720px | 960px | 1140px |
| .container-lg | 100% | 100% | 100% | 960px | 1140px |
| .container-xl | 100% | 100% | 100% | 100% | 1140px |
| .container-fluid | 100% | 100% | 100% | 100% | 100% |

# 使用.container-sm布局容器设置在断点处的布局容器宽度，效果如图：

移动设备的屏幕宽度设置为576px

5.3.2  响应式布局容器

移动设备的屏幕宽度设置为575px

# .container-sm布局容器
在C:\code\chapter05\demo02.html文件中，编写代码。

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0,  shrink-to-fit=no">
  <link rel="stylesheet" href="bootstrap-4.6.0-dist/css/bootstrap.min.css">
  <title>响应式布局容器</title>
</head>
<body>
  <div class="container-sm border mt-1">.container-sm</div>
</body>
</html>

STEP  01

5.3.2  响应式布局容器

# 测试网页程序
在浏览器中打开demo02.html文件，按“F12”键启动开发者工具，进入移动设备调试模式，将移动设备的宽度设置为575px。

STEP  02

5.3.2  响应式布局容器

# 将移动设备的宽度设置为576px（大于等于576px）时，会发现布局容器的最大宽度（即max-width值）为540px。

5.3.2  响应式布局容器

# Bootstrap栅格系统

5.4

# 先定一个小目标！

熟悉Bootstrap栅格系统，能够说出栅格系统中定义列的类有哪些

5.4.1  Bootstrap栅格系统概述

# Bootstrap栅格系统：基于12列布局，可以适配5种屏幕宽度，分别对应不同的屏幕大小，通过一系列的行（row）与列（column）的组合来创建页面布局。

开发者可以将内容放入创建好的布局中，让内容根据父元素盒子（布局容器）宽度的大小进行适当地调节，从而达到响应式页面布局的效果。

栅格系统

5.4.1  Bootstrap栅格系统概述

# Bootstrap栅格系统提供了定义列的类，用于在不同宽度的屏幕中实现不同的排列方式。

Bootstrap栅格系统定义列的类

5.4.1  Bootstrap栅格系统概述

| 屏幕类型 | 超小屏幕宽度         <576 | 小屏幕宽度
∈[576, 768） | 中等屏幕宽度
∈[769, 992） | 大屏幕宽度
∈[992,1200） | 超大屏幕宽度
≥1200 |
|---|---|---|---|---|---|
| 类 | .col-* | .col-sm-* | .col-md-* | .col-lg-* | .col-xl-* |

# 先定一个小目标！

掌握Bootstrap栅格系统的基本使用，能够为不同屏幕设备设置不同的列的宽度

5.4.2  Bootstrap栅格系统的基本使用

# 栅格系统的基本使用方法

5.4.2  Bootstrap栅格系统的基本使用

Bootstrap栅格系统为不同屏幕宽度定义了不同的类，使用非常方便，直接为元素添加类名即可，如.col-*、.col-sm-*等。

行（row）使用.row类定义，列（column）使用.col-*或.col-*-*类定义，内容应当放置于列内，列大于12时，将会另起一行排列。

行（row）必须包含在布局容器.container类或.container-ﬂuid类中，方便为其赋予合适的排列（alignment）和内边距（padding）。

通过行（row）可以创建水平方向的一组列（column），并且只有列（column）可以作为行（row）的直接子元素。例如，可以使用3个.col-xs-4类的div元素创建3个等宽的列。

# 设置子元素（列）的宽度

5.4.2  Bootstrap栅格系统的基本使用

.col-栅格的数量：设置超小屏幕下列的宽度。

.col-sm-栅格的数量：设置小屏幕下列的宽度。

.col-md-栅格的数量：设置中等屏幕下列的宽度。

.col-lg-栅格的数量：设置大屏幕下列的宽度。

.col-xl-栅格的数量：设置超大屏幕下列的宽度。

# 5.4.2  Bootstrap栅格系统的基本使用

使用栅格系统实现中等屏幕上显示4行2列，在小屏幕上显示2行3列布局效果，如图：

移动设备的屏幕宽度设置为768px

移动设备的屏幕宽度设置为576px

# 为小屏幕设备和中等屏幕设备设置列宽度
创建C:\Bootstrap\chapter05\demo03.html文件，实现中等屏幕上显示4行2列，在小屏幕上显示2行3列布局效果。

<head>
  <link rel="stylesheet" href="bootstrap-4.6.0-dist/css/bootstrap.min.css">
</head>
<body>
  <div class="container"> <!-- 定义外部布局容器 -->
    <div class="row mt-2"><!-- 在容器内部定义行（row） -->
      <div class="col-sm-4 col-md-6 border">1</div>
      <div class="col-sm-4 col-md-6 border">2</div>
      <div class="col-sm-4 col-md-6 border">3</div>
    </div>

STEP  01

5.4.2  Bootstrap栅格系统的基本使用

# 为小屏幕设备和中等屏幕设备设置列宽度
创建C:\Bootstrap\chapter05\demo03.html文件，实现中等屏幕上显示4行2列，在小屏幕上显示2行3列布局效果。

<div class="row-"><!-- 在容器内部定义行（row） ->
      <div class="col-sm-4 col-md-6 border">4</div>
      <div class="col-sm-4 col-md-6 border">5</div>
      <div class="col-sm-4 col-md-6 border">6</div>
    </div>
  </div>
</body>

STEP  01

5.4.2  Bootstrap栅格系统的基本使用

# 测试网页程序
运行demo03.html程序，按【F12】键启动开发者工具，进入移动设备调试模式，将移动设备的宽度设置为768px，将被识别为中等屏幕设备大小，说明.col-md-6类设置生效。

STEP  02

5.4.2  Bootstrap栅格系统的基本使用

# 测试网页程序
在移动设备调试模式，将移动设备的宽度设置为576px，将被识别为小屏幕设备大小，说明.col-sm-4类设置生效，每行显示3个div。

STEP  03

5.4.2  Bootstrap栅格系统的基本使用

# 先定一个小目标！

掌握利用Bootstrap栅格系统实现导航栏效果，能够完成具体效果

5.4.3  利用Bootstrap栅格系统实现导航栏效果

# 使用Bootstrap栅格系统相关内容实现导航栏效果，如图：

5.4.3  利用Bootstrap栅格系统实现导航栏效果

中等屏幕设备上的运行结果

小屏幕设备上的运行结果

# 导航栏实现思路

5.4.3  利用Bootstrap栅格系统实现导航栏效果

首先定义导航栏页面结构，通过Bootstrap栅格系统中的.container-fluid类设置导航栏的布局容器，在导航栏布局容器的每一行中设置不同的列数。

在中等屏幕设备下，所有列元素成一行显示。

在小屏幕设备下，每一列元素单独一行显示，即每列宽度为100%。

在编写本案例时应先实现导航栏的页面结构，再实现页面样式。

# 实现导航栏效果
创建C:\Bootstrap\chapter05\demo04.html文件，首先定义页面结构。

<head><link rel="stylesheet" href="bootstrap-4.6.0-dist/css/bootstrap.min.css"></head>
<body>
  <div class="container-fluid">
    <ul class="row">
      <li class="col-md-4 col-sm-12">LOGO</li>
      <li class="col-md-2 col-sm-12">首页</li>
      <li class="col-md-2 col-sm-12">新闻资讯</li>
      <li class="col-md-2 col-sm-12">关于我们</li>
      <li class="col-md-2 col-sm-12">客户服务</li>
    </ul>
  </div>
</body>

STEP  01

5.4.3  利用Bootstrap栅格系统实现导航栏效果

# 实现导航栏效果
在demo04.html文件中，定义页面样式。

STEP  02

5.4.3  利用Bootstrap栅格系统实现导航栏效果

<style>
  * {margin: 0;padding: 0;}
  li {
    list-style: none;
    text-align: center;
    padding: 10px;
    font-size: 20px;
  }
  li:hover {color: #c2bfbf;}
  .row {margin-bottom: 0;}
  .container-fluid{background-color: #000;color: #fff;}
</style>

# 测试网页程序
在浏览器中打开demo04.html文件，按“F12”键启动开发者工具，进入移动设备调试模式，将移动设备宽度设置为768px，将被识别为中等屏幕设备大小，说明.col-md-*类设置生效。

STEP  03

5.4.3  利用Bootstrap栅格系统实现导航栏效果

# 测试网页程序
在移动设备调试模式，将移动设备宽度设置为576px，将被识别为小屏幕设备大小，说明.col-sm-12类生效，导航栏中的标签会纵向排列。

STEP  04

5.4.3  利用Bootstrap栅格系统实现导航栏效果

# Bootstrap响应式工具类

5.5

# 先定一个小目标！

熟悉Bootstrap响应式工具类，能够利用响应式工具类实现元素在不同屏幕设备上的显示和隐藏

5.5 Bootstrap响应式工具类

# Bootstrap提供了一套响应式工具类，这些工具类可以将常见的重复属性值以单个类的形式表达出来，减少文件体积大小，更快捷地实现元素在不同屏幕设备上的显示和隐藏。

5.5 Bootstrap响应式工具类

响应式工具类

# 5.5 Bootstrap响应式工具类

元素隐藏的响应式工具类

| 类 | 不同屏幕宽度下的显示状态 |  |  |  |  |
|---|---|---|---|---|---|
|  | 超小屏幕宽度         <576 | 小屏幕宽度
∈[576, 768） | 中等屏幕宽度
∈[769, 992） | 大屏幕宽度
∈[992,1200） | 超大屏幕宽度
≥1200 |
| .d-none | 隐藏 | 隐藏 | 隐藏 | 隐藏 | 隐藏 |
| .d-none .d-sm-block | 隐藏 | 显示 | 显示 | 显示 | 显示 |
| .d-block .d-sm-none .d-md-block | 显示 | 隐藏 | 显示 | 显示 | 显示 |
| .d-block .d-md-none .d-lg-block | 显示 | 显示 | 隐藏 | 显示 | 显示 |
| .d-block .d-lg-none .d-xl-block | 显示 | 显示 | 显示 | 隐藏 | 显示 |
| .d-block .d-xl-none | 显示 | 显示 | 显示 | 显示 | 隐藏 |

# 5.5 Bootstrap响应式工具类

实现元素显示的响应式工具类

| 类 | 不同屏幕宽度下的显示状态 |  |  |  |  |
|---|---|---|---|---|---|
|  | 超小屏幕宽度         <576 | 小屏幕宽度
∈[576, 768） | 中等屏幕宽度
∈[769, 992） | 大屏幕宽度
∈[992,1200） | 超大屏幕宽度
≥1200 |
| .d-block | 显示 | 显示 | 显示 | 显示 | 显示 |
| .d-block .d-sm-none | 显示 | 隐藏 | 隐藏 | 隐藏 | 隐藏 |
| .d-none .d-sm-block .d-md-none | 隐藏 | 显示 | 隐藏 | 隐藏 | 隐藏 |
| .d-none .d-md-block .d-lg-none | 隐藏 | 隐藏 | 显示 | 隐藏 | 隐藏 |
| .d-none .d-lg-block .d-xl-none | 隐藏 | 隐藏 | 隐藏 | 显示 | 隐藏 |
| .d-none .d-xl-block | 隐藏 | 隐藏 | 隐藏 | 隐藏 | 显示 |

# 5.5 Bootstrap响应式工具类

模拟在超小屏幕设备、小屏幕设备、中等屏幕设备、大屏幕设备、超大屏幕设备的页面运行结果，如图：

超小屏幕设备运行结果

小屏幕设备运行结果

# 5.5 Bootstrap响应式工具类

中等屏幕设备运行结果

大屏幕设备运行结果

超大屏幕设备运行结果

# 5.5 Bootstrap响应式工具类

使用响应式工具类在不同屏幕上自适应隐藏或显示元素
创建C:\Bootstrap\chapter05\demo05.html文件，编写页面结构。

<head>
  <title>响应式工具</title>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href="bootstrap-4.6.0-dist/css/bootstrap.min.css" rel="stylesheet">
  <style>
    div {border: 1px solid black;}
  </style>
</head>
<body>
  <div class="container" style="padding: 40px;">
    <div class="row"> </div>
  </div>
</body>

STEP  01

# 5.5 Bootstrap响应式工具类

使用响应式工具类在不同屏幕上自适应隐藏或显示元素
在demo05.html文件的行内编写列内容。

<div class="row">
  <div class="col-6 col-sm-2">
    <span class="d-none d-sm-block">超小屏幕设备隐藏</span>
    <span class="d-block d-sm-none">✔在超小屏幕设备上可见</span>
  </div>
  <div class="col-6 col-sm-2">
    <span class="d-block d-sm-none d-md-block">小屏幕设备隐藏</span>
    <span class="d-none d-sm-block d-md-none">✔在小屏幕设备上可见</span>
  </div>
  <!-- 省略部分列内容 -->
</div>

STEP  02

# 5.5 Bootstrap响应式工具类

<div class="row">
  <!-- 省略部分列内容 -->
  <div class="col-6 col-sm-2">
    <span class="d-block d-md-none d-lg-block">中等屏幕设备隐藏</span>
    <span class="d-none d-md-block d-lg-none">✔在中等屏幕设备上可见</span>
  </div>
  <div class="col-6 col-sm-3">
    <span class="d-block d-lg-none d-xl-block">大屏幕设备隐藏</span>
    <span class="d-none d-lg-block d-xl-none">✔在大屏幕设备上可见</span>
  </div>
  <div class="col-6 col-sm-3">
    <span class="d-block d-xl-none">超大屏幕设备隐藏</span>
    <span class="d-none d-xl-block">✔在超大屏幕设备上可见</span>
  </div>
</div>

# 5.5 Bootstrap响应式工具类

STEP  03

测试网页程序
在浏览器中打开demo05.html文件，按“F12”键启动开发者工具，进入移动设备调试模式，将移动设备的宽度设置为575px，测试响应式工具类在超小屏幕上的运行结果。

# 5.5 Bootstrap响应式工具类

STEP  04

测试网页程序
将移动设备的宽度设置为576px，测试响应式工具类在小屏幕上的运行结果。

# 5.5 Bootstrap响应式工具类

STEP  05

测试网页程序
将移动设备的宽度设置为768px，测试响应式工具类在中等屏幕上的运行结果。

# 5.5 Bootstrap响应式工具类

STEP  06

测试网页程序
将移动设备的宽度设置为992px，测试响应式工具类在大屏幕上的运行结果。

# 5.5 Bootstrap响应式工具类

STEP  07

测试网页程序
将移动设备的设置为1200px，测试响应式工具类在超大屏幕上的运行结果。

# 本章小结

本章首先介绍了Bootstrap的概念，帮助读者对Bootstrap有一个初步的认识；然后讲解了Bootstrap的下载和使用，读者应掌握Bootstrap预编译文件的下载和引入，并能完成初始模板的创建；最后讲解了Bootstrap的布局容器、栅格系统和响应式工具类，读者可以根据实际需要灵活使用。

本

章

小

结
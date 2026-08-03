# 第6章 Bootstrap常用组件

# 学习目标/Target

# 章节概述/ Summary

Bootstrap组件：Bootstrap对网页中常用的公共代码进行封装，形成了各种各样的组件，如导航组件、导航栏组件、表单组件、按钮组件、轮播图组件等。

Bootstrap组件的作用：前端开发人员使用Bootstrap编写页面时，不需要写复杂的样式和逻辑代码，直接使用组件即可完成各种页面效果。这些组件也能够很好地支持响应式开发。

本章将针对Bootstrap中常用的组件进行详细讲解。

# 目录/Contents

# 导航组件

6.1

# 导航组件的作用：在网页中使用导航组件可以让用户清晰明了地找到所需要查看的页面。

Bootstrap提供了普通导航组件、标签式导航组件、胶囊式导航组件和面包屑导航组件。

6.1 导航组件

# 先定一个小目标！

掌握普通导航组件，能够创建普通导航页面

6.1.1  普通导航组件

# 普通导航组件使用列表标签和.nav类实现导航的基础效果

导航中的每一项使用.nav-item类设置样式

每一项的链接使用.nav-link类设置样式

普通导航默认是水平方向排列的，如果想要垂直排列，可以给列表标签添加.flex-column类来实现

普通导航

6.1.1  普通导航组件

# 实现普通导航页面，效果如图：

水平方向排列的普通导航

垂直排列的普通导航

6.1.1  普通导航组件

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link rel="stylesheet" href="bootstrap-4.6.0-dist/css/bootstrap.min.css">
</head>
<body>
</body>
</html>

实现普通导航页面
创建C:\code\chapter06\demo01.html，配置视口并引入依赖文件。

6.1.1  普通导航组件

# <!-- 普通导航 -->
  <ul class="nav">
    <li class="nav-item">
      <a class="nav-link" href="#">首页</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="#">简介</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="#">详情</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="#">联系电话</a>
    </li>
  </ul>

实现普通导航页面
修改demo01.html，实现普通导航页面效果。

6.1.1  普通导航组件

# 在浏览器中访问demo01.html
页面中显示水平方向排列的普通导航。

6.1.1  普通导航组件

# 设置垂直排列的普通导航
修改demo01.html，添加flex-column类名将导航的排列方向改为
垂直方向。

<ul class="nav flex-column">

6.1.1  普通导航组件

# 刷新页面
页面中显示垂直排列的普通导航。

6.1.1  普通导航组件

# 先定一个小目标！

掌握标签式导航组件，能够创建标签式导航页面

6.1.2  标签式导航组件

# 标签式导航组件的作用：可以实现在不跳转页面的情况下，切换标签页中显示的内容，这种实现效果类似于浏览器的标签页。

在实现标签页切换时，还需要在页面中引入Bootstrap提供的bootstrap.min.js文件，用来给页面添加JavaScript交互。

标签式导航

6.1.2  标签式导航组件

# 实现标签式导航页面，效果如图：

标签式导航

标签2页面内容效果

6.1.2  标签式导航组件

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link href="bootstrap-4.6.0-dist/css/bootstrap.min.css" rel="stylesheet">
  <script src="js/jquery.min.js"></script>
  <script src="bootstrap-4.6.0-dist/js/bootstrap.min.js"></script>
</head>
</html>

实现标签式导航页面
创建C:\code\chapter06\demo02.html，配置视口并引入依赖文件。

6.1.2  标签式导航组件

# <body class="m-3">
  <!-- 标签式导航 -->
  <ul class="nav nav-tabs">
    <li class="nav-item">
      <a class="nav-link active" data-toggle="tab" href="#home">标签1</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" data-toggle="tab" href="#profile">标签2</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" data-toggle="tab" href="#contact">标签3</a>
    </li>
  </ul>
</body>

实现标签式导航页面
修改demo02.html，实现标签式导航页面。

6.1.2  标签式导航组件

# <div class="tab-content">
  <div class="tab-pane fade show active" id="home">标签1页面内容</div>    
  <div class="tab-pane fade" id="profile">标签2页面内容</div>
  <div class="tab-pane fade" id="contact">标签3页面内容</div>
</div>

实现标签式导航页面
修改demo02.html，在</ul>标签后添加以下代码。

6.1.2  标签式导航组件

# 在浏览器中访问demo02.html
页面中显示标签式导航默认的页面效果。

标签式导航

6.1.2  标签式导航组件

# 在浏览器中访问demo02.html
单击“标签2”，显示标签2页面内容效果。

6.1.2  标签式导航组件

# 先定一个小目标！

熟悉胶囊式导航组件，能够创建胶囊式导航页面

6.1.3  胶囊式导航组件

# 胶囊式导航组件与标签式导航组件的区别：都能实现标签页切换功能，区别在于两种导航的样式不同。胶囊式导航的形状类似胶囊，看起来更加美观。

胶囊式导航的使用：给外层的<ul>标签设置nav-pills类名即可。

胶囊式导航组件

6.1.3  胶囊式导航组件

# 修改demo02.html文件，将<ul>标签的类名nav-tabs改为nav-pills。
在浏览器中访问demo02.html，胶囊式导航的页面效果如图。

6.1.3  胶囊式导航组件

# 先定一个小目标！

掌握面包屑导航，能够创建面包屑导航页面

6.1.4  面包屑导航组件

# 面包屑导航的由来：面包屑导航的概念来自童话故事《汉赛尔与格莱特》。在故事中，汉赛尔为了防止在森林里迷路，他在沿途走过的地方撒下了面包屑，沿着面包屑就可以找到回家的路。

网页中面包屑导航的作用：告诉访问者当前网页所处的位置以及如何返回。

Bootstrap中的面包屑导航通过.breadcrumb、.breadcrumb-item类实现。

面包屑导航组件

6.1.4  面包屑导航组件

# 实现面包屑导航页面，效果如图：

6.1.4  面包屑导航组件

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link rel="stylesheet" href="bootstrap-4.6.0-dist/css/bootstrap.min.css">
</head>
<body>
</body>
</html>

实现面包屑导航页面
创建C:\code\chapter06\demo03.html，配置视口并引入依赖文件。

6.1.4  面包屑导航组件

# <!-- 面包屑导航 -->
  <ol class="breadcrumb">
    <li class="breadcrumb-item">
      <a href="#">首页</a>
    </li>
    <li class="breadcrumb-item">
      <a href="#">简介</a>
    </li>
    <li class="breadcrumb-item">
      <a href="#">详情</a>
    </li>
    <li class="breadcrumb-item">
      <a href="#">联系电话</a>
    </li>
  </ol>

实现面包屑导航页面
修改demo03.html，在</body>标签结束前添加以下代码。

6.1.4  面包屑导航组件

# 在浏览器中访问demo03.html
面包屑导航的页面效果如图。

6.1.4  面包屑导航组件

# 导航栏组件

6.2

# 6.2 导航栏组件

导航栏组件的作用：导航栏组件通常应用于网页的头部，可以帮助用户快速找到他们想要访问的内容，方便用户从一个页面跳转到另一个页面。

# 先定一个小目标！

掌握基础导航栏组件，能够实现基础导航栏页面

6.2.1  基础导航栏组件

# 基础导航栏组件：是Bootstrap中作为网站导航页头的响应式组件，该组件可以使导航栏在大屏幕上水平铺开，小屏幕上垂直堆叠显示。

navbar类名：用于创建一个基础导航栏。

navbar-expand-sm类名：用于使导航栏在大屏幕上水平铺开，小屏幕上垂直堆叠，其中，sm表示小屏幕，还可以取值md、lg、xl表示不同的大小的屏幕。

bg-dark类名和navbar-dark类名：表示使用暗色的样式风格，如果省略bg-dark类名和navbar-dark类名则默认使用浅色的样式风格。

基础导航栏组件

6.2.1  基础导航栏组件

# 实现基础导航栏页面，效果如图：

基础导航栏（水平）页面效果

小屏幕上导航栏垂直排列

6.2.1  基础导航栏组件

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>导航栏</title>
  <link rel="stylesheet" href="bootstrap-4.6.0-dist/css/bootstrap.min.css">
</head>
<body>
</body>
</html>

实现基础导航栏页面
创建C:\code\chapter06\demo04.html，配置视口并引入依赖文件。

6.2.1  基础导航栏组件

# <!-- 小屏幕上水平导航栏会切换为垂直的 -->
  <nav class="navbar navbar-expand-sm bg-dark navbar-dark">
    <ul class="navbar-nav">
      <li class="nav-item">
        <a class="nav-link" href="#">首页</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">标题1</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">标题2</a>
      </li>
    </ul>
  </nav>

实现基础导航栏页面
修改demo04.html，在</body>标签结束之前添加以下代码。

6.2.1  基础导航栏组件

# 在浏览器中访问demo04.html
基础导航栏（水平）页面效果如图。

6.2.1  基础导航栏组件

# 缩小浏览器窗口
在小屏幕上水平导航栏会切换为垂直的导航栏。

6.2.1  基础导航栏组件

# 先定一个小目标！

掌握在导航栏中添加品牌标志的实现方法，能够实现带有品牌标志的导航栏页面

6.2.2  在导航栏中添加品牌标志

# 实现带有品牌标志的导航栏页面，效果如图：

6.2.2  在导航栏中添加品牌标志

# <!-- 小屏幕上水平导航栏会切换为垂直的 -->
<nav class="navbar navbar-expand-sm bg-dark navbar-dark">
  <a class="navbar-brand" href="#">Navbar</a>
  <!-- 原代码 -->
</nav>

6.2.2  在导航栏中添加品牌标志

修改导航栏页面
修改demo04.html文件，给导航栏添加品牌标志。

# 6.2.2  在导航栏中添加品牌标志

在浏览器种访问demo04.html
带有品牌标志的导航栏页面效果如图。

# 先定一个小目标！

掌握可折叠的导航栏的实现方法，能够实现可折叠的导航栏页面

6.2.3  实现可折叠的导航栏

# 导航栏折叠功能：考虑到有些网站的导航栏内容比较多，为了避免导航栏在小屏幕下占据大量的空间，Bootstrap提供了导航栏折叠功能。

可折叠的导航栏的作用：能够根据页面的宽度自动调整显示状态，当屏幕过小时，导航栏会折叠起来，并出现一个折叠按钮，用户单击该按钮可以展开导航栏，再次单击该按钮可以折叠导航栏。

实现可折叠的导航栏

6.2.3  实现可折叠的导航栏

# 6.2.3  实现可折叠的导航栏

实现可折叠的导航栏页面，效果如图：

网页在小屏幕下的效果

导航栏效果

# <script src="js/jquery.min.js"></script>
<script src="bootstrap-4.6.0-dist/js/bootstrap.min.js"></script>

6.2.3  实现可折叠的导航栏

修改导航栏页面
修改demo04.html文件，在</head>标签前面引入jQuery文件和bootstrap.min.js核心文件。

# <!-- 小屏幕上水平导航栏会折叠 -->
<nav class="navbar navbar-expand-sm bg-dark navbar-dark">
  <a class="navbar-brand" href="#">Navbar</a>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navtop">
    <span class="navbar-toggler-icon"></span>
  </button>
  <div class="collapse navbar-collapse" id="navtop">
    <!-- 将原来的ul.navbar-nav放到此处 -->
  </div>
</nav>

6.2.3  实现可折叠的导航栏

修改导航栏页面
修改demo04.html文件，添加折叠按钮。

# 6.2.3  实现可折叠的导航栏

在浏览器中访问demo04.html
查看网页在小屏幕下的效果。

# 6.2.3  实现可折叠的导航栏

在浏览器中访问demo04.html
单击折叠按钮即可展开导航栏，查看导航栏展开效果。

# 表单组件

6.3

# 先定一个小目标！

掌握表单控件，能够使用表单控件实现网页中的表单效果

6.3.1  表单控件

# 6.3.1  表单控件

在日常生活中，我们浏览一些网站，例如淘宝网、百度等，注册、登录或者个人设置的界面经常使用表单组件来实现。表单中的每一项需要我们填写的内容通过表单控件来实现。

# 表单中的文本输入框和文本域的作用：用于让用户输入文本信息，文本输入框用于输入单行文本，而文本域用于输入多行文本。

.form-group类：表示表单组，每个表单组对应表单中要填的每一项信息，表单组中存放表单控件。

.form-control类：设置表单控件样式。

文本输入框和文本域

6.3.1  表单控件

# 6.3.1  表单控件

实现文本输入框和文本域的页面效果。

# 6.3.1  表单控件

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link href="bootstrap-4.6.0-dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body class="m-3">
</body>
</html>

实现文本输入框和文本域的页面效果
创建C:\code\chapter06\demo05.html，配置视口并引入依赖文件。

# 6.3.1  表单控件

<form>
    <!-- 实现文本输入框页面效果 -->
    <div class="form-group">
      <label for="email">邮箱地址：</label>
      <input type="text" class="form-control" id="email" placeholder="请输入邮箱地址">
    </div>
    <!-- 实现文本域页面效果 -->
    <div class="form-group">
      <label for="address">家庭住址：</label>
      <textarea class="form-control" id="address" rows="3"></textarea>
    </div>
  </form>

实现文本输入框和文本域的页面效果
实现文本输入框和文本域的页面效果。

# 6.3.1  表单控件

在浏览器中访问demo05.html
文本输入框和文本域的页面效果如图。

# .form-check类：用于为一组单选框或复选框的外层容器设置样式，容器内的排列方式为垂直排列。

.form-check-inline类：功能和.form-check相同，但排列方式为水平排列。

.form-check-input类：用于为单选框或复选框控件设置样式。

.form-check-label类：用于为单选框或复选框对应的<label>标签设置样式。

单选框和复选框

6.3.1  表单控件

# 6.3.1  表单控件

实现单选框和复选框的页面效果。

# 6.3.1  表单控件

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link href="bootstrap-4.6.0-dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body class="m-3">
</body>
</html>

实现单选框和复选框的页面效果
创建C:\code\chapter06\demo06.html，配置视口并引入依赖文件。

# 6.3.1  表单控件

<form>
    <!-- 实现单选框页面效果 -->
    <div>性别</div>
    <div class="form-check">
      <input class="form-check-input" type="radio" name="gender" value="0" id="male">
      <label class="form-check-label" for="male">男</label>
    </div>
    <div class="form-check">
      <input class="form-check-input" type="radio" name="gender" value="1" id="female">
      <label class="form-check-label" for="female">女</label>
    </div>
</form>

实现单选框和复选框的页面效果
在</body>标签结束前添加以下代码。

# 6.3.1  表单控件

<!-- 实现复选框页面效果 -->
    <div>爱好</div>
    <div class="form-check">
      <input class="form-check-input" type="checkbox" name="hobby[]" value="0" id="sing">
      <label class="form-check-label" for="sing">唱歌</label>
    </div>
    <div class="form-check">
      <input class="form-check-input" type="checkbox" name="hobby[]" value="1" id="swim">
      <label class="form-check-label" for="swim">游泳</label>
     </div>

实现单选框和复选框的页面效果
在</form>标签结束前添加以下代码。

# 6.3.1  表单控件

在浏览器中访问demo06.html
单选框和复选框页面效果如图。

# .form-group类：表示表单组

.form-control类：设置表单控件样式

下拉列表

6.3.1  表单控件

实现下拉列表的页面效果。

下拉列表页面效果

下拉列表展开效果

# 6.3.1  表单控件

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link href="bootstrap-4.6.0-dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body class="m-3">
</body>
</html>

实现下拉列表的页面效果
创建C:\code\chapter06\demo07.html，配置视口并引入依赖文件。

# 6.3.1  表单控件

<form>
    <!-- 实现下拉列表页面效果 -->
    <div class="form-group">
      <label for="select">请选择</label>
      <select class="form-control" id="select">
        <option>1</option>
        <option>2</option>
        <option>3</option>
        <option>4</option>
        <option>5</option>
      </select>
    </div>
</form>

实现下拉列表的页面效果
在</body>标签结束之前添加以下代码。

# 6.3.1  表单控件

在浏览器中访问demo07.html
下拉列表页面效果如图。

# 6.3.1  表单控件

在浏览器中访问demo07.html
单击下拉列表，即可显示展开后的下拉列表。

# Bootstrap提供了.form-control-*类用于更改表单控件的大小，*的可选值有sm和lg，分别表示小和大，如果没有设置.form-control-*，则表单控件为中等大小。

下面以文本输入框为例进行演示，示例代码如下。

6.3.1  表单控件

<!-- 较小的文本输入框 -->
<input type="text" class="form-control form-control-sm" placeholder="小">
<!-- 中等的文本输入框 -->
<input type="text" class="form-control" placeholder="中">
<!-- 较大的文本输入框 -->
<input type="text" class="form-control form-control-lg" placeholder="大">

多学一招：更改表单控件的大小

# 6.3.1  表单控件

3种大小文本输入框显示效果如图。

多学一招：更改表单控件的大小

# 先定一个小目标！

掌握表单布局，能够实现不同的表单布局页面

6.3.2  表单布局

# 在日常生活中，不同网站的登录或注册页面布局方式也不同，利用Bootstrap提供的样式类可以实现多种表单布局。

6.3.2  表单布局

# 6.3.2  表单布局

垂直布局是将表单中的每个表单控件都放到一个<div>标签中，利用div元素是块级元素的特点实现垂直排列。

垂直布局

创建垂直布局表单页面，效果如图：

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link href="bootstrap-4.6.0-dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body class="m-3">
</body>
</html>

创建垂直布局表单页面
创建C:\code\chapter06\demo08.html，配置视口并引入依赖文件。

6.3.2  表单布局

# <form>
    <div class="form-group">
      <label for="email">邮箱地址：</label>
      <input type="email" class="form-control" id="email">
    </div>
    <div class="form-group">
      <label for="password">密码：</label>
      <input type="password" class="form-control" id="password">
    </div>
  </form>

创建垂直布局表单页面
修改demo08.html，创建两个表单组，并按照垂直布局的方式进行布局。

6.3.2  表单布局

# 在浏览器中访问demo08.html
垂直布局表单页面显示效果如图。

6.3.2  表单布局

# 6.3.2  表单布局

表单的行内布局是将表单中的<div>标签、<label>标签和表单控件都转换为行内元素进行显示，为<form>标签添加form-inline类名即可实现行内布局。

行内布局

创建行内布局表单页面，效果如图：

# 6.3.2  表单布局

修改demo08.html文件，为<form>标签添加form-inline类名，然后在浏览器中访问demo08.html，行内布局表单页面显示效果如图。

# 6.3.2  表单布局

水平布局的实现思路：将<label>和<input>标签在同一行显示，每个表单组单独占一行，这样就避免了一行显示太多的内容。

实现方法：Bootstrap的栅格系统来实现水平布局，为表单组添加.row类，并为<label>和<input>标签添加col-*类名，即可让<label>和<input>标签水平排列。

Bootstrap还为表单中的<label>标签提供了.col-form-label类，用于使<label>标签的文字内容与其关联的表单控件垂直居中。

水平布局

# 6.3.2  表单布局

创建水平布局表单页面，效果如图：

# 6.3.2  表单布局

<form>
  <div class="form-group row">
    <label for="email" class="col-sm-2 col-form-label">邮箱地址：</label>
    <input type="email" class="form-control col-sm-10" id="email">
  </div>
  <div class="form-group row">
    <label for="password" class="col-sm-2 col-form-label">密码：</label>
    <input type="password" class="form-control col-sm-10" id="password">
  </div>
</form>

创建水平布局表单页面
修改C:\code\chapter06\demo08.html，实现表单的水平布局。

# 6.3.2  表单布局

在浏览器中访问demo08.html
水平布局表单页面显示效果如图。

# 先定一个小目标！

掌握表单验证，能够实现表单的验证功能

6.3.3  表单验证

# 6.3.3  表单验证

日常生活中，我们浏览网站时需要注册账户。在注册页面，根据提示输入相应的信息，但是信息有一定的规范，例如输入的手机号应是11位数字，当我们输入汉字或输入的
数字小于11时，页面中会提示输入的信息有误，这种提示效果是如何实现的呢？

# 6.3.3  表单验证

HTML5中的表单验证功能：用来对用户输入的内容进行验证，如邮箱地址格式验证、
必填项验证等。

HTML5表单验证的样式效果是浏览器默认设置的，用户体验欠佳。为了提高用户的体验，Bootstrap提供了.needs-validation、.invalid-feedback类，用来更好地传达表单验证的结果，并可以结合JavaScript实现自定义消息。

.needs-validation类：表示需要进行表单验证

.invalid-feedback类：表示验证后的反馈结果

# 6.3.3  表单验证

实现表单验证的页面，效果如图：

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link href="bootstrap-4.6.0-dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body class="m-3">
</body>
</html>

实现表单验证的页面
创建C:\code\chapter06\demo09.html，实现填写邮箱地址和密码的表单。

6.3.3  表单验证

# <form class="needs-validation" novalidate>
    <!-- 实现文本输入框页面效果 -->
    <div class="form-group">
      <label for="email">邮箱地址</label>
      <input type="email" class="form-control" id="email" required>
      <div class="invalid-feedback">
        请输入邮箱地址！
      </div>
    </div>
</form>

实现表单验证的页面
修改demo09.html，在</body>标签结束之前添加以下代码。

6.3.3  表单验证

# <div class="form-group">
      <label for="password">密码</label>
      <input type="password" class="form-control" id="pssword" required>
      <div class="invalid-feedback">
        请输入密码！
      </div>
    </div>
    <button type="submit" class="btn btn-primary">提交</button>
</div>

实现表单验证的页面
修改demo09.html，在</form>标签结束之前添加以下代码。

6.3.3  表单验证

# <script>
  (function () {
    'use strict';
    window.addEventListener('load', function () {
      var forms = document.getElementsByClassName('needs-validation');
      var validation = Array.prototype.filter.call(forms, function (form) {
        form.addEventListener('submit', function (event) {
          if (form.checkValidity() === false) {
            event.preventDefault();
            event.stopPropagation();
          }
          form.classList.add('was-validated');
        }, false);
      });
    }, false);
  })();
</script>

实现表单验证的页面
修改demo09.html，在</body>结束标签前添加表单验证的JavaScript代码。

6.3.3  表单验证

# 在浏览器中访问demo09.html
表单验证的页面效果如图。

6.3.3  表单验证

# 按钮组件

6.4

# 按钮组件

按钮是页面中常用的组成部分，当用户单击了页面中的按钮后，可以根据不同的按钮实现不同的功能。网页中常见的功能如用户登录、视频播放、文件上传等，都需要通过按钮来触发。Bootstrap按钮组件提供了一些样式类，用来制作各式各样的按钮。

# 先定一个小目标！

掌握按钮样式，能够实现网页中不同样式的按钮效果

6.4.1  按钮样式

# 6.4.1  按钮样式

Bootstrap中的基础按钮使用<a>标签、<button>标签或<input>标签定义，给这3种标签添加按钮样式类即可设置成Bootstrap提供的按钮效果。

| 类 | 描述 | 类 | 描述 |
|---|---|---|---|
| .btn | 按钮的基础样式类 | .btn-danger | 危险按钮 |
| .btn-lg | 大号按钮 | .btn-warning | 警示按钮 |
| .btn-sm | 小号按钮 | .btn-info | 信息按钮 |
| .btn-primary | 主要按钮 | .btn-light | 亮色按钮 |
| .btn-secondary | 次要按钮 | .btn-dark | 暗色按钮 |
| .btn-success | 成功按钮 | .btn-link | 链接按钮 |

# 6.4.1  按钮样式

实现不同种类按钮页面，效果如图：

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link rel="stylesheet" href="bootstrap-4.6.0-dist/css/bootstrap.min.css">
</head>
<body>
</body>
</html>

实现不同种类按钮的页面
创建C:\code\chapter06\demo10.html，配置视口并引入依赖文件。

6.4.1  按钮样式

# <button type="button" class="btn btn-primary">主要按钮</button>
  <button type="button" class="btn btn-secondary">次要按钮</button>
  <button type="button" class="btn btn-success">成功按钮</button>
  <button type="button" class="btn btn-danger">危险按钮</button>
  <button type="button" class="btn btn-warning">警示按钮</button>

实现不同种类按钮的页面
修改demo10.html，在</body>标签结束前，添加以下代码。

6.4.1  按钮样式

# <button type="button" class="btn btn-info">信息按钮</button>
  <button type="button" class="btn btn-light">亮色按钮</button>
  <button type="button" class="btn btn-dark">暗色按钮</button>
  <button type="button" class="btn btn-link">链接按钮</button>
  <br>
  <button type="button" class="btn btn-primary btn-lg">大号按钮</button>
  <button type="button" class="btn btn-primary btn-sm">小号按钮</button>

实现不同种类按钮的页面
修改demo10.html，在</body>标签结束前，继续添加以下代码。

6.4.1  按钮样式

# 在浏览器中访问demo10.html
不同种类按钮页面效果如图。

6.4.1  按钮样式

# 先定一个小目标！

掌握按钮组的使用，能够实现按钮组页面效果

6.4.2  按钮组

# 什么是按钮组？

按钮组：是将同一类功能的按钮组合在一行上进行展示，不同种类功能的按钮则分开单独展示，方便按钮的管理。

按钮组的实现：Bootstrap提供了.btn-group类，可以快速实现按钮组页面效果。

6.4.2  按钮组

# 实现按钮组页面，效果如图：

6.4.2  按钮组

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link href="bootstrap-4.6.0-dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
  <div class="btn-group">
    <button type="button" class="btn btn-primary">主要按钮</button>
    <button type="button" class="btn btn-secondary">次要按钮</button>
  </div>
</body>
</html>

实现按钮组页面
创建C:\code\chapter04\demo11.html，将主要按钮、次要按钮组合。

6.4.2  按钮组

# 在浏览器中访问demo11.html
按钮组页面效果如图。

6.4.2  按钮组

# 先定一个小目标！

掌握按钮工具条的使用，能够实现按钮工具条页面效果

6.4.3  按钮工具条

# 6.4.3  按钮工具条

什么是按钮工具条？

按钮工具条：是将多个不同的按钮组分开展示。

Bootstrap提供了.btn-toolbar类，可以快速实现按钮工具条页面效果。

实现按钮工具条页面，效果如图：

# <!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link href="bootstrap-4.6.0-dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
</body>
</html>

实现按钮工具条页面
创建C:\code\chapter04\demo12.html，配置视口并引入依赖文件。

6.4.2  按钮组

# <div class="btn-toolbar">
    <div class="btn-group mr-2">
      <button type="button" class="btn btn-secondary">1</button>
      <button type="button" class="btn btn-secondary">2</button>
      <button type="button" class="btn btn-secondary">3</button>
      <button type="button" class="btn btn-secondary">4</button>
    </div>
    <div class="btn-group mr-2">
      <button type="button" class="btn btn-secondary">5</button>
      <button type="button" class="btn btn-secondary">6</button>
      <button type="button" class="btn btn-secondary">7</button>
    </div>
    <div class="btn-group">
      <button type="button" class="btn btn-secondary">8</button>
    </div>
  </div>

实现按钮工具条页面
修改demo12.html，使用.btn-toolbar类实现按钮工具条页面效果。

6.4.2  按钮组

# 在浏览器中访问demo12.html
按钮工具条页面如图。

6.4.2  按钮组

# 轮播图组件

6.5

# 轮播图组件

电商网站中的页面包括商城首页、商品列表页面等。商品列表页面展示了不同商品图片的信息，如手机、家电等，用户可以很容易地找到自己喜欢的商品图片进行查看。

当商城中的商品有大型促销活动、商城优惠券活动时，我们使用轮播图来展示相关活动的图片信息，它能够引起用户的注意，帮助用户了解活动等信息。

# 先定一个小目标！

掌握轮播图页面结构，能够实现网页中的轮播图页面结构

6.5.1  轮播图页面结构

# 6.5.1  轮播图页面结构

轮播图组件的作用：可以让图像、内嵌框架、视频或者其他想要放置的任何类型的内容之间进行自动循环播放，也可以手动切换下一张或上一张图片，还可以查看当前图片的位置，即轮播图指示器功能。

实现轮播图页面样式的类：

.carousel类：定义轮播图页面的最外层容器
.slide类：实现轮播图滑动的过渡效果
.carousel-inner类：定义轮播图页面中每一项内容的外层结构
.carousel-item类：定义轮播图页面中的每一项内容
.active类：表示活动状态

# 6.5.1  轮播图页面结构

实现轮播图页面，效果如图：

# 实现轮播图页面
创建C:\code\chapter06\demo13.html，具体代码如下。

6.5.1  轮播图页面结构

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link href="bootstrap-4.6.0-dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
</body>
</html>

# 实现轮播图页面
修改demo13.html，在</body>标签结束之前，添加以下代码。

6.5.1  轮播图页面结构

<!-- 轮播图页面结构 -->
  <div id="carouselExampleSlidesOnly" class="carousel slide">
    <div class="carousel-inner">
    </div>
  </div>

# <div class="carousel-item active">
        <img src="images/slide_01_2000x410.jpg" class="d-block w-100" alt="...">
      </div>
      <div class="carousel-item">
        <img src="images/slide_02_2000x410.jpg" class="d-block w-100" alt="...">
      </div>
      <div class="carousel-item">
        <img src="images/slide_03_2000x410.jpg" class="d-block w-100" alt="...">
      </div>
      <div class="carousel-item">
        <img src="images/slide_04_2000x410.jpg" class="d-block w-100" alt="...">
      </div>

实现轮播图页面
修改demo13.html，在类名为carousel-inner的<div>标签下方添加代码。

6.5.1  轮播图页面结构

# 在浏览器中访问demo13.html
轮播图页面效果如图。

6.5.1  轮播图页面结构

# 先定一个小目标！

掌握轮播图切换的实现方法，能够实现轮播图的切换效果

6.5.2  实现轮播图切换效果

# 6.5.2  实现轮播图切换效果

轮播图切换效果的实现

Bootstrap提供了data-ride="carousel"属性，用于在页面加载时实现轮播图的切换效果。

需要注意的是，如果不使用data-ride="carousel"来初始化carousel，则需要使用$('.carousel').carousel()方法进行初始化。

Tip

# <script src="js/jquery.min.js"></script>
<script src="bootstrap-4.6.0-dist/js/bootstrap.js"></script>

实现轮播图切换页面
修改demo13.html文件，在6.5.1小节的STEP 01中</head>标签结束前，引入实现轮播图的依赖文件。

6.5.2  实现轮播图切换效果

# <div id="carouselExampleSlidesOnly" class="carousel slide" data-ride="carousel">
  <!-- 源代码 -->
</div>

实现轮播图切换页面
修改demo13.html文件，为6.5.1小节的STEP 02中，class为"carousel slide"的标签，添加data-ride="carousel"属性。

6.5.2  实现轮播图切换效果

# 在浏览器中访问demo13.html
轮播图切换页面效果如图。

6.5.2  实现轮播图切换效果

# 修改轮播图切换默认延迟时间
修改demo13.html文件，具体代码如下。

6.5.2  实现轮播图切换效果

<div id="carouselExampleSlidesOnly" class="carousel slide" data-ride="carousel" data-interval="2000">
  <!-- 源代码 -->
</div>

需要注意的是，如果设置data-interval属性的值为false，轮播图carousel将不会自动循环。

Tip

# 先定一个小目标！

掌握轮播图指示器功能的实现方法，能够实现轮播图指示器功能

6.5.3  轮播图指示器功能

# 6.5.3  轮播图指示器功能

Bootstrap扩展了一些预定义的实现轮播图指示器页面样式的类，主要包括：

.carousel-indicators类：定义轮播图指示器页面的最外层容器。

.active类：表示活动状态.

实现轮播图指示器页面，效果如图：

# <div id="carouselExampleIndicators" class="carousel slide" data-ride="carousel" data-interval="2000">
  <!-- 源代码 -->
</div>

实现轮播图指示器页面
打开demo13.html文件，修改6.5.2小节的STEP 04中class为"carousel slide"的标签 id为carouselExampleIndicators，具体代码如下。

6.5.3  轮播图指示器功能

# 实现轮播图指示器页面
在步骤STEP 01的源代码处，实现轮播图指示器页面效果，具体代码如下。

6.5.3  轮播图指示器功能

<!-- 轮播图指示器 -->
<ol class="carousel-indicators">
  <li data-target="#carouselExampleIndicators" class="active"></li>
  <li data-target="#carouselExampleIndicators"></li>
  <li data-target="#carouselExampleIndicators"></li>
  <li data-target="#carouselExampleIndicators"></li>
</ol>

# 在浏览器中访问demo13.html
轮播图指示器页面效果如图。

6.5.3  轮播图指示器功能

# 刷新浏览器，自行查看指示器效果
修改步骤STEP 02的代码，使用data-slide-to= "*"属性，控制轮播图的位置，具体代码如下。

6.5.3  轮播图指示器功能

<!-- 轮播图指示器 -->
<ol class="carousel-indicators">
  <li data-target="#carouselExampleIndicators" data-slide-to="0" class="active"></li>
  <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
  <li data-target="#carouselExampleIndicators" data-slide-to="2"></li>
  <li data-target="#carouselExampleIndicators" data-slide-to="3"></li>
</ol>

# 先定一个小目标！

掌握轮播图左右手动切换的实现方法，能够手动切换轮播图

6.5.4  实现轮播图左右手动切换效果

# 6.5.4  实现轮播图左右手动切换效果

Bootstrap扩展了一些预定义的实现轮播图左右手动切换按钮的页面样式的类，主要包括：

.carousel-control-prev类：定义轮播图左侧按钮的最外层容器

.carousel-control-prev-icon类：定义轮播图左侧按钮图标

.carousel-control-next类：定义轮播图右侧按钮的最外层容器

.carousel-control-next-icon类：定义轮播图右侧按钮图标

# 6.5.4  实现轮播图左右手动切换效果

实现轮播图左右手动切换页面，效果如图：

# <!-- 查看上一张 -->
<a class="carousel-control-prev" href="#carouselExampleIndicators" role="button" >
  <span class="carousel-control-prev-icon"></span>
</a>
<!-- 查看下一张 -->
<a class="carousel-control-next" href="#carouselExampleIndicators" role="button"
  <span class="carousel-control-next-icon"></span>
</a>

实现轮播图左右手动切换页面
打开demo13.html文件，在6.5.3小节的STEP 04中</ol>标签后添加以下代码。

6.5.4  实现轮播图左右手动切换效果

# 在浏览器中访问demo13.html
轮播图左右手动切换页面效果如图。

6.5.4  实现轮播图左右手动切换效果

# <!-- 查看上一张 -->
<a class="carousel-control-prev" href="#carouselExampleIndicators" role="button" data-slide="prev">
  <span class="carousel-control-prev-icon"></span>
</a>
<!-- 查看下一张 -->
<a class="carousel-control-next" href="#carouselExampleIndicators" role="button" data-slide="next">
  <span class="carousel-control-next-icon"></span>
</a>

刷新浏览器，自行查看手动切换效果
修改STEP 01中的代码，使用data-slide属性控制轮播图切换。

6.5.4  实现轮播图左右手动切换效果

# 本章小结

本章主要讲解了如何使用Bootstrap常用组件实现页面中的导航、导航栏、表单、按钮等页面效果。最后，重点讲解了什么是轮播图以及如何使用Bootstrap常用组件来实现页面中的轮播图效果。通过学习本章内容，希望读者能够使用Bootstrap提供的组件完成页面的制作。

本

章

小

结
# HTML5+CSS3网页设计任务教程

单元7 Bootstrap响应式网站基础

# CONTANTS

任务7-1 掌握Bootstrap基础知识

任务7-2 制作栅格化布局页面

任务7-3 制作响应式导航栏

任务7-4 制作响应式banner图片

任务7-5 制作响应式文字列表

任务7-6 制作响应式缩略图

任务7-7 制作响应式图文混排列表

任务7-8 制作响应式图文混排内容

任务7-9 制作响应式表格

任务7-10 制作响应式表单

任务7-11 制作响应式提示框

任务7-12 制作完整的响应式网站

# 1

掌握Bootstrap基础知识

任务7-1

1

本地使用下载的Bootstrap框架。

远程使用服务器的Bootstrap框架。

响应式网站是指网站能够自动切换分辨率、图片尺寸及相关脚本功能等，以适应不同设备。 Bootstrap是Twitter推出的一个用于前端开发的开源工具包，主要用来开发响应式网站。

# 2

掌握Bootstrap基础知识

任务7-1

从bootstrap中文网http://v3.bootcss.com可以下载到bootstrap的包，解压缩后包含了三个子文件夹：css, fonts 和 js。在网站文件夹根目录下新建bootstrap文件夹，将这三个子文件夹复制到 bootstrap文件夹中。再从https://cdn.bootcss.com/jquery/2.1.1/jquery.min.js下载jquery.min.js文件，复制到bootstrap/js文件夹下。

# 3

掌握Bootstrap基础知识

任务7-1

# 4

掌握Bootstrap基础知识

任务7-1

<head>
<meta charset="utf-8" />
<title>本地下载使用响应式网站</title>
<link href="bootstrap/css/bootstrap.min.css" rel="stylesheet" />
<link href="bootstrap/css/bootstrap-theme.min.css" rel="stylesheet" />
<script type="text/javascript" src="bootstrap/js/jquery.min.js"></script>
<script type="text/javascript" src="bootstrap/js/bootstrap.min.js"></script>
</head>

# 5

掌握Bootstrap基础知识

任务7-1

<head>
<meta charset="utf-8" />
<title></title>
<!-- 最新版本的 Bootstrap 核心 CSS 文件 -->
<link rel="stylesheet" href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
<!-- 可选的 Bootstrap 主题文件（一般不用引入） -->
<link rel="stylesheet" href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap-theme.min.css" integrity="sha384-rHyoN1iRsVXV4nD0JutlnGaslCJuC7uwjduW9SVrLvRYooPp2bWYgmgJQIXwl/Sp" crossorigin="anonymous">
<!-- 最新的 Jquery 核心 JavaScript 文件 -->
<script src="http://code.jquery.com/jquery-3.2.1.min.js" integrity="sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4=" crossorigin="anonymous"></script>
<!-- 最新的 Bootstrap 核心 JavaScript 文件 -->
<script src="https://cdn.bootcss.com/bootstrap/3.3.7/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>
</head>

# 6

掌握Bootstrap基础知识

任务7-1

<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
这段代码的几个参数解释：
width=device-width：宽度等于当前设备的宽度
height=device-height：高度等于当前设备的高度
initial-scale：初始的缩放比例（默认设置为1.0）  
minimum-scale：允许用户缩放到的最小比例（默认设置为1.0）    
maximum-scale：允许用户缩放到的最大比例（默认设置为1.0）   
user-scalable：用户是否可以手动缩放（默认设置为no，因为我们不希望用户放大缩小页面）

# 7

制作栅格化布局页面

任务7-2

Bootstrap使用了四种栅格选项来形成栅格系统，他们分别是col-xs、col-sm、col-md、col-lg，lg是large的缩写(大屏幕大桌面显示器≥1200px)，md是mid的缩写(中等屏幕桌面显示器≥992px)，sm是small的缩写(小屏幕平板≥768px)，xs是xteram small的缩写(超小屏幕手机<768px)。这样命名就体现了这几种class适应的屏幕宽度不同。下面我们分别介绍这几种class的特点。

# 8

制作响应式导航栏

任务7-3

创建一个默认的导航栏的步骤如下：
向 <nav> 标签添加 class .navbar、.navbar-default。
向上面的元素添加 role="navigation"，有助于增加可访问性。
向 <div> 元素添加一个标题 class .navbar-header，内部包含了带有 class navbar-brand 的 <a> 元素。这会让文本看起来更大一号。
为了向导航栏添加链接，只需要简单地添加带有 class .nav、.navbar-nav 的无序列表即可。

# 9

制作响应式banner图片

任务7-4

1、插入<div>标签，给<div>标签添加class.carousel slide，id# myCarousel，data-ride="carousel" data-interval="2000"。其中，data-ride="carousel" 就可以实现自动播放，data-interval="2000"设置图片轮转的时间间隔为2000毫秒。
2、插入<ol>标记，实现设置图片下端的小圆点。三个小圆点分别对应0、1、2，用data-slide-to参数进行控制。data-target="#myCarousel"，data-slide-to="2" 将把滑块移动到一个特定的索引，索引从0开始计数。
3、插入<div>标签，给<div>标签添加 class . item，其中，class . active代表开始显示的图片，背景色background和所在图片的底色一致，以便为了更好地保持美观。
4、class . carousel-control left是向前播放控制器，class . carousel-control right是向后播放的控制器，分别对应轮播（Carousel）导航上部左右箭头，data-slide 接受关键字 prev 或 next，用来改变要显示的图片相对于当前位置的位置。也可以使用转义字符&lsaquo;（<）和&rsaquo;（>）进行人为翻页。

# 10

制作响应式文字列表

任务7-5

<ul class="list-group">
    <li class="list-group-item">免费域名注册</li>
    <li class="list-group-item">免费 Window 空间托管</li>
    <li class="list-group-item">图像的数量</li>
    <li class="list-group-item">24*7 支持</li>
    <li class="list-group-item">每年更新成本</li>
</ul>

# 11

制作响应式缩略图

任务7-6

<div class="row">
    <div class="col-sm-6 col-md-3">
        <a href="#" class="thumbnail">
            <img src="/wp-content/uploads/2014/06/kittens.jpg"
                 alt="通用的占位符缩略图">
        </a>
    </div>
</div>

# 12

制作响应式图文混排列表

任务7-7

# 13

制作响应式图文混排列表

任务7-7

1、.img-rounded：添加 border-radius:6px 来获得图片圆角
2、.img-circle：添加 border-radius:50% 来让整个图片变成圆形
3、.img-thumbnail：添加一些内边距（padding）和一个灰色的边框
4、.img-responsive 类可以让图片支持响应式布局（将很好地扩展到父元素），其实质是为图片设置了 max-width: 100%;、 height: auto; 和 display: block; 属性，从而让图片在其父元素中更好的缩放。如果需要让使用了 .img-responsive 类的图片水平居中，请使用 .center-block 类，不要用 .text-center。

# 14

制作响应式表格

任务7-9

1、.table 为表格添加基本的样式（只有横向的分隔线）
	.table-striped：斑马线表格
	.table-bordered：带边框的表格
	.table-hover：鼠标悬停高亮的表格
	.table-condensed：紧凑型表格
	.table-responsive：响应式表格
2、tr，th和td类样式
          .active 将表示悬停的颜色用在目标的行或者单元格
	.success 表示成功的操作（绿色）
	.info 表示信息变化的操作（蓝色）
	.warning 表示一个警告的操作（黄色）
	.danger表示一个危险的操作（红色）

# 15

制作响应式表单

任务7-10

1、垂直或基本表单：
基本的表单结构是 Bootstrap 自带的，个别的表单控件自动接收一些全局样式。
	向父 <form> 元素添加 role=”form”。 
	把标签和控件放在一个带有 class .form-group 的 <div> 中。这是获取最佳间距所必需的。 
	向所有的文本元素 <input>、<textarea> 和 <select> 添加 class .form-control。

# 16

制作响应式表单

任务7-10

2、内联表单：
	如果需要创建一个表单，它的所有元素是内联的，向左对齐的，标签是并排的，可以向 <form> 标签添加 class .form-inline。
	默认情况下，Bootstrap 中的 <input>、<select> 和< textarea >有 100% 宽度。在使用内联表单时，您需要在表单控件上设置一个宽度。
	使用 class .sr-only，您可以隐藏内联表单的标签。

# 17

制作响应式表单

任务7-10

3、水平表单：
水平表单与其他表单不仅标记的数量上不同，而且表单的呈现形式也不同。如需创建一个水平布局的表单：
	向父 <form> 元素添加 class .form-horizontal。 
	把标签和控件放在一个带有 class .form-group 的 <div> 中。 
	向标签添加 class .control-label。

# 18

制作响应式提示框

任务7-11

1、插入<div>标签，给<div>标签添加 class . alert、alert-success，class . alert、alert-info，class . alert、alert-warning，class . alert、alert-danger，分别代表成功，提示，警告，错误。
2、如果需要有关闭按钮，需要给上述<div>添加样式class.alert-dismissable。
3、在<div>里面插入<button>标签，加上属性class="close" data-dismiss="alert" aria-hidden="true"。
4、给<button>里面加上内容转义字符&times;，用来显示X。

# 19

制作完整的响应式网站

任务7-12

# 20

制作完整的响应式网站

任务7-12

# HTML5+CSS3网页设计任务教程

单元7 Bootstrap响应式网站基础
# 第7章  Bootstrap常用样式

# 学习目标/Target

# 学习目标/Target

# 章节概述/ Summary

Bootstrap的核心是轻量的CSS基础代码库，它重置了浏览器的默认样式，并提供了常用的样式类，用来对页面进行美化。例如，通过.text-info类、.text-success类可以设置文本颜色，通过.text-left类、.text-right类可以设置文本格式。这些样式类都是预定好的，只要引入了bootstrap.min.css样式文件就可使用。

本章将针对Bootstrap常用样式进行讲解。

# 目录/Contents

# 目录/Contents

# 标题样式

7.1

# 先定一个小目标！

掌握<h1>~<h6>标签，能够完成标题的设置

7.1.1  使用<h1>~<h6>标签设置标题

# 标题在网页中显示时通常用大字体放在网页最显眼的位置。在传统网站开发中，通常使用HTML标题标签（<h1>~<h6>）定义标题部分。

标题的重要性

7.1.1  使用<h1>~<h6>标签设置标题

新闻的标题

# Bootstrap中对所有的HTML标题标签（<h1>~<h6>）的样式进行了定义，将所有标题的默认样式设置为margin-top: 0;、margin-bottom: 0.5rem (8px);。其中，rem是CSS3新增的一个相对单位，它相对于HTML根元素的文字大小。
在Bootstrap 4中，<html>标签的font-size为16px，也就是说1rem等于16px。

使用<h1>~<h6>标签设置标题

7.1.1  使用<h1>~<h6>标签设置标题

# <h1>~<h6>标题标签

7.1.1  使用<h1>~<h6>标签设置标题

| 标题标签 | 描述 | 字体大小 |
|---|---|---|
| <h1> | 一级标题 | 2.5rem（40px） |
| <h2> | 二级标题 | 2rem（32px） |
| <h3> | 三级标题 | 1.75rem（28px） |
| <h4> | 四级标题 | 1.5rem（24px） |
| <h5> | 五级标题 | 1.25rem（20px） |
| <h6> | 六级标题 | 1rem（16px） |

# 使用<h1>~<h6>标题标签设置标题，效果如图：

7.1.1  使用<h1>~<h6>标签设置标题

# 演示<h1>~<h6>标题标签在页面中的展示效果
在C:\code\chapter07\demo01.html文件中，编写代码。

<body>
  <h1>一级标题</h1>
  <h2>二级标题</h2>
  <h3>三级标题</h3>
  <h4>四级标题</h4>
  <h5>五级标题</h5>
  <h6>六级标题</h6>
</body>

STEP  01

7.1.1  使用<h1>~<h6>标签设置标题

# 测试网页程序
运行demo01.html程序，演示标题标签页面效果。

STEP  02

7.1.1  使用<h1>~<h6>标签设置标题

一级标题到六级标题，数字越大所代表的文本字体越小

# 先定一个小目标！

掌握.h1~.h6标题类，能够完成标题的设置

7.1.2  使用.h1~.h6标题类设置标题

# 7.1.2  使用.h1~.h6标题类设置标题

Bootstrap中定义了.h1~.h6标题类来让非标题元素实现标题效果。
.h1~.h6标题类与<h1>~<h6>标题标签的字体大小和换算方式相同。
.h1~.h6标题类与<h1>~<h6>标题标签不同之处在于，使用.h1~.h6标题类的文本段不会视作HTML的标题元素，没有标题的含义。

使用.h1~.h6标题类设置标题

# 使用.h1~.h6标签设置标题，效果如图：

7.1.2  使用.h1~.h6标题类设置标题

# 7.1.2  使用.h1~.h6标题类设置标题

演示.h1~.h6标题类在页面中的展示效果
在C:\code\chapter07\demo02.html文件中，编写代码。

<body>
  <p class="h1">一级标题</p>
  <p class="h2">二级标题</p>
  <p class="h3">三级标题</p>
  <p class="h4">四级标题</p>
  <p class="h5">五级标题</p>
  <p class="h6">六级标题</p>
</body>

STEP  01

# 7.1.2  使用.h1~.h6标题类设置标题

测试网页程序
运行demo02.html程序，演示标题类页面效果。

STEP  02

一级标题到六级标题，数字越大所代表的文本字体越小

# 先定一个小目标！

掌握.display标题类，能够完成标题的设置

7.1.3  使用.display标题类设置标题

# 传统的HTML标题（<h1>~<h6>）的样式中，<h1>用于设置最大的标题字号40px。如果想要设置字号更大、更醒目的标题，以迎合网页内容的显示，这时可以使用Bootstrap中提供了一系列.display标题类设置标题样式。
.display标题类与<h1>~<h6>标题标签字体的换算方式相同，1rem=16px。

使用.display标题类设置标题

7.1.3  使用.display标题类设置标题

# .display标题类

7.1.3  使用.display标题类设置标题

| 标题类 | 字体大小 |
|---|---|
| .display-1 | 6rem（96px） |
| .display-2 | 5.5rem（88px） |
| .display-3 | 4.5rem（72px） |
| .display-4 | 3.5rem（56px） |

# 演示.display标题类在页面中的展示效果
在C:\code\chapter07\demo03.html文件中，编写代码。

<body>
  <h1 class="display-1">一级标题</h1>
  <h1 class="display-2">二级标题</h2>
  <h1 class="display-3">三级标题</h3>
  <h1 class="display-4">四级标题</h4>
</body>

STEP  01

7.1.3  使用.display标题类设置标题

# 测试网页程序
运行demo03.html程序，演示.display标题类页面效果。

STEP  02

display-{1|2|3|4}
一级标题到四级标题，数字越大所代表的文本越小

7.1.3  使用.display标题类设置标题

# 先定一个小目标！

掌握<small>标签，能够完成副标题的设置

7.1.4  使用<small>标签设置副标题

# 在Web开发中常常会遇到标题后跟一行小的副标题的布局形式。
在Bootstrap中也考虑到了这种布局形式，使用<small>标签（通常与.text-muted类一起使用）创建字号更小、颜色更浅的文本实现副标题效果。

使用<small>标签设置副标题

7.1.4  使用<small>标签设置副标题

# 使用<small>标签设置副标题
在C:\code\chapter07\demo04.html文件中，编写代码通过对<small>标签添加.text-muted类查看标题效果。

<body>
  <h1>一级标题<small>我是副标题</small></h1>
  <h1>一级标题<small class="text-muted">我是副标题</small></h1>
</body>

STEP  01

7.1.4  使用<small>标签设置副标题

# 测试网页程序
运行demo04.html程序，演示副标题页面效果。

STEP  02

副标题加上类名text-muted后，字体颜色变浅了

7.1.4  使用<small>标签设置副标题

# 文本样式

7.2

# 先定一个小目标！

掌握内联标签，能够通过内联标签强调文本

7.2.1  使用内联标签强调文本

# HTML中常用的内联标签

7.2.1  使用内联标签强调文本

| 标签 | 描述 | 标签 | 描述 |
|---|---|---|---|
| <b>和<strong> | 文本加粗 | <mark> | 标记，高亮显示 |
| <del>和<s> | 删除线 | <address> | 表示地址 |
| <ins>和<u> | 下画线 | <footer> | 定义文档或小节的页脚 |
| <em>和<i> | 斜体 | <cite> | 表示它所包含的文本对某个参考文献的引用，比如书籍或者杂志的标题 |
| <blockquote> | 引用块，长引用 | <abbr> | 缩略语，鼠标指针悬停在该文本上时，显示title的属性值 |

# 内联标签解释说明

7.2.1  使用内联标签强调文本

<b>和<strong>默认情况下是加粗字体，前者是给其包裹的文本设置为bold粗体效果，而后者用于强调文本，强调的程度更强一些。

<del>和<s>都可以实现删除效果，但是<del>更具有语义化，能更形象地描述删除的意思。

<strong>和<em>具有强调作用，有利于SEO。

<ins>和<u>都可以实现下画线效果，但是前者通常与<del>删除线一起使用，用来定义带有已删除部分和新插入部分的文本（如：1+1=<del>4</del><ins>2</ins>），而后者表示为文本添加下画线。

<cite>通常表示所包含的文本对某个参考文献的引用，引用的文本将以斜体显示。

# 使用HTML中常用的内联标签强调文本，效果如图：

7.2.1  使用内联标签强调文本

# 使用内联标签强调文本
在C:\code\chapter07\demo05.html文件中，编写代码使用HTML中常用的内联标签演示对应的效果。

<p>
    <b>b 文本加粗</b>
    <strong>strong 文本加粗</strong>
  </p>
  <p>
    <del>del 删除</del>
    <s>s 删除</s>
  </p>

STEP  01

7.2.1  使用内联标签强调文本

<p>
    1+1=<del>4</del>
    <ins>2</ins>ins 下画线
  </p>
    <u>u 下画线</u>
<p>
    <em>em 斜体</em>
    <i>i 斜体</i>
  </p>

# 使用内联标签强调文本
在C:\code\chapter07\demo05.html文件中，编写代码使用HTML中常用的内联标签演示对应的效果。

STEP  01

7.2.1  使用内联标签强调文本

<blockquote>blockquote 引用块</blockquote>
  <mark>mark 高亮显示</mark>
  <address>address 表示地址</address>
  <footer>定义文档或小节的页脚</footer>
  <cite>表示它所包含的文本对某个参考文献的引用，比如书籍或者杂志的标题</cite>
  <p><abbr title="我是提示信息">abbr 缩略语</abbr></p>

# 测试网页程序
运行demo05.html程序，演示内联标签页面效果。

STEP  02

<mark>标签显示为黄色背景有且一定的边距，<abbr>标签会在文本底部显示一条虚线边框，并且当鼠标指针悬停在<abbr>标签上时会出现提示性文字

7.2.1  使用内联标签强调文本

# 先定一个小目标！

掌握文本类，能够使用文本类强调文本

7.2.2  使用文本类强调文本

# 7.2.2  使用文本类强调文本

在实际项目中，对于一些重要的文本，开发者往往希望对这些文本进行特殊的样式设置，以突显其重要性。

除了使用HTML中常用的内联标签外，还可以通过给标签添加类名的方式来实现同样的标签效果。

使用文本类强调文本

# 7.2.2  使用文本类强调文本

常见的文本类

| 类 | 描述 |
|---|---|
| .lead | 段落突出 |
| .small | 指定更小文本 |
| .mark | 标记，高亮显示 |
| .blockquote | 引用块，长引用 |

# 使用<blockquote>标签结合.blockquote类设置引述内容，效果如图：

7.2.2  使用文本类强调文本

# 7.2.2  使用文本类强调文本

使用文本类强调文本
在C:\code\chapter07\demo06.html文件中，编写代码以<blockquote>标签结合.blockquote类为例，演示其在页面中的展示效果。

<body class="text-center">
  <blockquote class="blockquote">
    <p>朝辞白帝彩云间</p>
    <p>千里江陵一日还</p>
    <p>两岸猿声啼不住</p>
    <p>轻舟已过万重山</p>
    <footer class="blockquote-footer">
      出自李白《早发白帝城》
    </footer>
  </blockquote>
</body>

STEP  01

# 7.2.2  使用文本类强调文本

测试网页程序
运行demo06.html程序，演示引述内容运行效果。

STEP  02

底部备注来源

# 先定一个小目标！

掌握.text-*类设置文本颜色，能够完成文本颜色的设置

7.2.3  使用.text-*类设置文本颜色

# Bootstrap定义了一套.text-*类，用于设置文本颜色来强调文本的重要性，例如前面在讲解使用<small>标签设置副标题时用到的.text-muted类。*取值为primary、secondary、success、muted、danger、info、warning、dark、light、white、body。

使用.text-*类设置文本颜色

7.2.3  使用.text-*类设置文本颜色

# 常见的文本颜色类

7.2.3  使用.text-*类设置文本颜色

| 类 | 描述 |
|---|---|
| .text-primary | 首选文本颜色，重要的文本 |
| .text-secondary | 副标题文本 |
| .text-success | 执行成功的文本 |
| .text-muted | 柔和的文本 |
| .text-danger | 危险操作文本 |
| .text-info | 代表一些提示信息的文本 |
| .text-warning | 警告文本 |
| .text-dark | 深灰色文本 |
| .text-light | 浅灰色文本 |
| .text-white | 白色文本 |
| .text-body | 默认主体颜色 |

# 演示常见的文本颜色类在页面中的展示效果，如图：

7.2.3  使用.text-*类设置文本颜色

# 使用.text-*类设置文本颜色
在C:\code\chapter07\demo07.html文件中，编写代码演示常见的文本颜色在页面中的展示效果。

<body>
  <p class="text-primary">.text-primary效果（重要的文本）</p>
  <p class="text-secondary">text-secondary效果（副标题文本）</p>
  <p class="text-success">.text-success效果（执行成功的文本）</p>
  <p class="text-muted">.text-muted效果（柔和的文本）</p>
  <p class="text-danger">.text-danger效果（危险操作文本）</p>
  <p class="text-info">.text-info效果（代表一些提示信息的文本）</p>
  <p class="text-warning">.text-warning效果（警告文本）</p>

STEP  01

7.2.3  使用.text-*类设置文本颜色

# 使用.text-*类设置文本颜色
在C:\code\chapter07\demo07.html文件中，编写代码演示常见的文本颜色在页面中的展示效果。

<p class="text-dark">.text-dark效果（深灰色文本）</p>
  <p class="text-body">.text-body效果（默认主体颜色）</p>
  <p class="text-light bg-dark">.text-light效果（浅灰色文本）</p>
  <p class="text-white bg-dark">.text-white效果（白色文本）</p>
  <p class="text-white-50 bg-dark">.text-white-50效果（透明度为0.5的白色文本）</p>
  <p class="text-black-50">.text-black-50效果（透明度为0.5的黑色文本）</p>
</body>

STEP  01

7.2.3  使用.text-*类设置文本颜色

# 测试网页程序
运行demo07.html程序，演示常见的文本颜色效果。

STEP  02

7.2.3  使用.text-*类设置文本颜色

# 7.2.3  使用.text-*类设置文本颜色

我们可以通过为文本设置类名text-*指定特殊意义的文本颜色。这些类名除了可以给普通文本设置颜色外，还可以给超链接文本设置颜色，并且超链接的hover和focus状态的效果也会改变。

多学一招：实现超链接文本颜色效果

# 演示超链接文本颜色效果，如图：

7.2.3  使用.text-*类设置文本颜色

# 7.2.3  使用.text-*类设置文本颜色

演示超链接文本的鼠标悬停效果
在C:\code\chapter07\demo08.html文件中，编写代码实现效果。

<body>
  <p><a href="#" class="text-primary">.text-primary链接效果（重要的文本）</a></p>
  <p><a href="#" class="text-secondary">text-secondary链接效果（副标题文本）</a></p>
  <p><a href="#" class="text-success">.text-success链接效果（执行成功的文本）</a></p>
  <p><a href="#" class="text-muted">.text-muted链接效果（柔和的文本）</a></p>
  <p><a href="#" class="text-danger">.text-danger链接效果（危险操作文本）</a></p>
  <p><a href="#" class="text-info">.text-info链接效果（代表一些提示信息的文本）</a></p>
  <p><a href="#" class="text-warning">.text-warning链接效果（警告文本）</a></p>

STEP  01

# 7.2.3  使用.text-*类设置文本颜色

演示超链接文本的鼠标悬停效果
在C:\code\chapter07\demo08.html文件中，编写代码实现效果。

<p><a href="#" class="text-dark">.text-dark链接效果（深灰色文本）</a></p>
  <p><a href="#" class="text-body">.text-body链接效果（默认主体颜色）</a></p>
  <p><a href="#" class="text-light bg-dark">.text-light链接效果（浅灰色文本）</a></p>
  <p><a href="#" class="text-white bg-dark">.text-white链接效果（白色文本）</a></p>
  <p><a href="#" class="text-white-50 bg-dark">.text-white-50链接效果（透明度为0.5的白色文本）</a></p>
  <p><a href="#" class="text-black-50">.text-black-50链接效果（透明度为0.5的黑色文本）</a></p>
</body>

STEP  01

# 7.2.3  使用.text-*类设置文本颜色

STEP  02

测试网页程序
运行demo08.html程序，在浏览器中查看类名为text-muted的超链接文本的鼠标悬停效果。

# 先定一个小目标！

掌握.text-*类设置文本格式，能够完成文本格式的设置

7.2.4  使用.text-*类设置文本格式

# 在进行网页布局时，经常需要设置文本的对齐方式，如使用text-align属性设置文本对齐方式。

为了方便开发者使用，Bootstrap提供了一系列的.text-*类用于设置文本格式，*取值left、right、center、justify、nowrap、uppercase、lowercase、capitalize。

使用.text-*类设置文本格式

7.2.4  使用.text-*类设置文本格式

# 常见的文本格式类

7.2.4  使用.text-*类设置文本格式

| 类 | 描述 |
|---|---|
| .text-left | 左对齐，默认由浏览器决定 |
| .text-right | 右对齐 |
| .text-center | 居中对齐 |
| .text-justify | 两端文本对齐 |
| .text-nowrap | 段落中文本不会换行 |
| .text-uppercase | 设置文本大写 |
| .text-lowercase | 设置文本小写 |
| .text-capitalize | 设置单词首字母大写 |

# 演示常见的文本格式类在页面中的效果，如图：

7.2.4  使用.text-*类设置文本格式

# 使用.text-*类设置文本格式
在C:\code\chapter07\demo09.html文件中，实现文本对齐效果和文本大小写效果。

<body>
  <p class="text-left">左对齐效果</p>
  <p class="text-right">右对齐效果</p>
  <p class="text-center">居中对齐效果</p>
  <P>这段是没有使用类名text-justify的效果</P>
  <p>hello bootstrop ... （省略多个hello bootstrop）</p>
  <P>这段是使用类名text-justify的效果</P>
  <p class="text-justify">hello bootstrop ...（省略多个hello bootstrop）</p>

STEP  01

7.2.4  使用.text-*类设置文本格式

# 使用.text-*类设置文本格式
在C:\code\chapter07\demo09.html文件中，实现文本对齐效果和文本大小写效果。

<p class="text-nowrap">使用类名text-nowrap的效果，文本不换行hello bootstrop hello 
    bootstrop hello bootstrop hello bootstrop</p>
  <p class="text-uppercase">text-uppercase 文本大写</p>
  <p class="text-lowercase">text-lowercase 文本小写</p>
  <p class="text-capitalize">text-capitalize 单词首字母大写</p>
</body>

STEP  01

7.2.4  使用.text-*类设置文本格式

# 测试网页程序
运行demo09.html程序，查看文本格式效果。

STEP  02

7.2.4  使用.text-*类设置文本格式

# 列表样式

7.3

# 先定一个小目标！

掌握.list-unstyled类，能够完成列表的初始化

7.3.1  使用.list-unstyled类设置列表初始化

# Bootstrap中无序列表<ul>和有序列表<ol>默认是带有项目符号的，但在实际开发中，大多数情况下，列表是不需要带有项目符号的。

考虑到这种情况，Bootstrap中提供了.list-unstyled类用于对列表进行初始化，删除浏览器的默认列表样式。

.list-unstyled类仅适用于直接子列表项，如果需要移除嵌套的列表项默认样式，需要在嵌套的列表中使用.list-unstyled类。

使用.list-unstyled类设置列表初始化

7.3.1  使用.list-unstyled类设置列表初始化

# 使用.list-unstyled类设置列表初始化，效果如图：

7.3.1  使用.list-unstyled类设置列表初始化

# 7.3.1  使用.list-unstyled类设置列表初始化

使用.list-unstyled类实现嵌套的列表初始化效果
在C:\code\chapter07\demo10.html文件中，编写代码初始化效果。

<body>
  <!-- 嵌套的无序列表初始化 -->
  <ul>
    <li>无序项目列表
      <ul class="list-unstyled"><li>不带项目符号</li><li>不带项目符号</li></ul>
    </li>
  </ul>

STEP  01

# 7.3.1  使用.list-unstyled类设置列表初始化

使用.list-unstyled类实现嵌套的列表初始化效果
在C:\code\chapter07\demo10.html文件中，编写代码初始化效果。

<!-- 嵌套的有序列表初始化 -->
  <ol>
    <li>有序项目列表
      <ol class="list-unstyled"><li>不带项目编号</li><li>不带项目编号</li></ol>
    </li>
  </ol>
</body>

STEP  01

# 7.3.1  使用.list-unstyled类设置列表初始化

测试网页程序
运行demo10.html程序，演示列表初始化效果。

STEP  02

# 先定一个小目标！

熟悉.list-inline类，能够说明如何实现内联列表效果

7.3.2  使用.list-inline类设置内联列表

# Bootstrap中可以通过给列表设置.list-inline类，并将列表的直接子级列表项设置为.list-inline-item类实现内联列表效果（所有列表项放置在同一行），即将垂直列表转换为水平列表，并且删除项目符号或项目编号，保持水平显示。

使用.list-inline类设置内联列表

7.3.2  使用.list-inline类设置内联列表

# 使用.list-inline类设置内联列表，效果如图：

7.3.2  使用.list-inline类设置内联列表

# 演示如何在无序列表中使用.list-inline类实现内联列表布局
在C:\code\chapter07\demo11.html文件中，编写代码实现内联列表效果。

<style>
  li {background-color: black;color: #fff;}
</style>

STEP  01

7.3.2  使用.list-inline类设置内联列表

<body>
  <p class="text-center">内联列表</p>
  <ul class="list-inline text-center">
    <li class="list-inline-item">Item1</li>
    <li class="list-inline-item">Item2</li>
    <li class="list-inline-item">Item3</li>
    <li class="list-inline-item">Item4</li>
    <li class="list-inline-item">Item5</li>
  </ul>
</body>

# 测试网页程序
运行demo11.html程序，演示内联列表效果。

STEP  02

7.3.2  使用.list-inline类设置内联列表

# 先定一个小目标！

熟悉水平定义列表的设置，能够说明如何实现水平定义列表效果

7.3.3  设置水平定义列表

# 在Bootstrap中可以使用<dl>结合栅格系统的预定义类设置定义列表内容，实现内容的水平对齐显示效果。

对于较长的文本内容可以使用.text-truncate类省略溢出部分，并使用省略号“…”来代替。

设置水平定义列表

7.3.3  设置水平定义列表

# 设置水平定义列表，效果如图：

7.3.3  设置水平定义列表

# 演示如何设置水平定义列表
在C:\code\chapter07\demo12.html文件中，实现定义列表的水平对齐效果。

<body>
  <div class="container">
    <dl class="row">
      <dt class="col-sm-4">标题一：</dt>
      <dd class="col-sm-8 text-truncate">用于描述列表标题内容，对列表标题部分进行介绍的</dd>
    </dl>
  </div>
</body>

STEP  01

7.3.3  设置水平定义列表

# 测试网页程序
运行demo12.html程序，演示水平定义列表效果。

STEP  02

7.3.3  设置水平定义列表

# 代码样式

7.4

# 先定一个小目标！

熟悉代码样式的设置，能够区分常见的代码标签

7.4 代码样式

# 常见的代码标签

7.4 代码样式

| 标签 | 描述 |
|---|---|
| <code> | 计算机代码，用来显示单行内联代码 |
| <pre> | 预格式化文本，保留所有格式，显示多行代码 |
| <kbd> | 键盘输入文本，显示用户输入代码 |
| <var> | 定义变量 |
| <samp> | 程序输出文本 |

# 使用<code>、<pre>、<kbd>、<var>和<samp>标签设置代码风格，效果如图：

7.4 代码样式

# 7.4 代码样式

演示代码标签在页面中的展示效果
在C:\code\chapter07\demo13.html文件中，编写代码。

<body>
  <div>单行内联代码：<code>&lt;html&gt;&lt;/html&gt;</code></div>
  <div>键盘输入：<kbd>Ctrl+S</kbd>保存代码</div>
  <div>预格式化文本：
    <pre class="pre-scrollable">
      &lt;dl&gt;
        &lt;dt&gt;...&lt;/dt&gt;
        &lt;dd&gt;...&lt;/dd&gt;
      &lt;/dl&gt;
    </pre>
  </div>

STEP  01

# 7.4 代码样式

演示代码标签在页面中的展示效果
在C:\code\chapter07\demo13.html文件中，编写代码。

<div>定义变量：<var>y</var> = <var>a</var><var>x</var> +  
  <var>b</var></div>
  <samp>计算机输出文本</samp>
</body>

STEP  01

# 7.4 代码样式

测试网页程序
运行demo13.html程序，查看常见的代码标签效果。

STEP  02

# 图文样式

7.5

# 先定一个小目标！

掌握.img-fluid类，能够实现响应式图像效果

7.5.1  使用.img-fluid类设置响应式图像

# 常见的图像样式类

7.5.1  使用.img-fluid类设置响应式图像

| 类 | 描述 |
|---|---|
| .img-fluid | 设置响应式图片，主要应用于响应式设计中 |
| .img-thumbnail | 缩略图片，给图片设置一个空心边框 |
| .rounded | 给元素添加圆角边框 |
| .rounded-circle | 设置元素形状（圆形或者椭圆形） |

# 使用.rounded-*设置圆角边框

7.5.1  使用.img-fluid类设置响应式图像

| 类 | 描述 |
|---|---|
| .rounded-top | 给元素上方位添加圆角边框 |
| .rounded-right | 给元素右方位添加圆角边框 |
| .rounded-bottom | 给元素下方位添加圆角边框 |
| .rounded-left | 给元素左方位添加圆角边框 |
| .rounded-0 | 去掉元素圆角样式 |

# 使用.img-fluid类设置响应式图像，效果如图：

7.5.1  使用.img-fluid类设置响应式图像

# 使用.img-fluid类演示响应式图像的展示效果
在C:\code\chapter07\demo14.html文件中，编写代码演示响应式图像效果。

<body>
  <!-- 响应式 -->
  <img src="images/banner.jpg" class="img-fluid mb-1" alt="响应式图像">
  <!-- 非响应式 -->
  <img src="images/banner.jpg" alt="非响应式图像">
</div>
</body>

STEP  01

7.5.1  使用.img-fluid类设置响应式图像

# 测试网页程序
运行demo14.html程序，查看响应式图像效果。

STEP  02

7.5.1  使用.img-fluid类设置响应式图像

# 7.5.1  使用.img-fluid类设置响应式图像

<picture>标签是HTML5新增的标签元素，可以实现图像的响应式效果，即在不同的设备上显示不同的图像。

<picture>标签常适用于在固定的区域下使用固定的图像尺寸，例如在大屏幕下使用大尺寸图像，在小屏幕下使用小尺寸图像，这样可以减少流量的使用。

多学一招：使用<picture>标签设置响应式图像

# 使用<picture>标签设置响应式图像，效果如图：

屏幕宽度不超过500px时

7.5.1  使用.img-fluid类设置响应式图像

屏幕宽度大于500px时

# 7.5.1  使用.img-fluid类设置响应式图像

演示响应式图像的展示效果
在C:\code\chapter07\demo15.html文件中，编写代码实现响应式图像效果。

<body>
  <picture>
    <source srcset="images/banner1.jpg" media="(max-width:500px)">
    <img src="images/banner.jpg" class="img-fluid" alt="响应式大图">
  </picture>
</body>

STEP  01

# 7.5.1  使用.img-fluid类设置响应式图像

测试网页程序
运行demo15.html程序，演示当屏幕宽度不超过500px时图片的效果。

STEP  02

# 7.5.1  使用.img-fluid类设置响应式图像

测试网页程序
当屏幕超过500px时使用banner.jpg图片。

STEP  03

# 先定一个小目标！

掌握图像布局模式，能够实现图像或文字布局

7.5.2  设置图文布局模式

# 常见的图像或文字布局模式类

7.5.2  设置图文布局模式

| 类 | 描述 |
|---|---|
| .float-left | 设置元素左浮动 |
| .float-right | 设置元素右浮动 |
| .clearfix | 清除浮动 |

# 使用常见的图像样式结合图像或文字布局模式，设置图像的显示位置，效果如图：

7.5.2  设置图文布局模式

# 演示图文布局模式类在页面中的展示效果
在C:\code\chapter07\demo16.html文件中，编写代码使用常见的图像样式结合图像或文字布局模式，设置图像的显示位置。

<body style="background-color:#666">
  <div class="clearfix">
    <img src="images/load-pic1.jpg" class="float-left" alt="缩略图">
    <img src="images/load-pic2.jpg" class="rounded float-right">
  </div>
  <img src="images/load-pic4.jpg" class="img-thumbnail mx-auto d-block">
</body>

STEP  01

7.5.2  设置图文布局模式

# 测试网页程序
运行demo16.html程序，演示图像显示效果。

STEP  02

7.5.2  设置图文布局模式

# 7.5.2  设置图文布局模式

Bootstrap通过给<img>图像添加两个公用的类.mx-auto和.d-block实现图像的居中显示。

除此之外，考虑到<img>本身是内联标签，还可以给图像包裹一层外部容器，并给该容器添加.text-center类设置图像居中对齐。

多学一招：使用.text-center类设置图像居中对齐

# 使用.text-center类设置图像居中对齐，效果如图：

7.5.2  设置图文布局模式

# 7.5.2  设置图文布局模式

演示图文布局模式类在页面中的展示效果
在C:\code\chapter07\demo16.html文件中，编写代码给图像外部<div>容器添加类名text-center，实现图片居中显示。

<div class="text-center">
  <img src="images/load-pic3.jpg" class="rounded-circle">
</div>

STEP  01

# 7.5.2  设置图文布局模式

测试网页程序
运行demo16.html程序，演示图像居中对齐效果。

STEP  02

# 先定一个小目标！

掌握图文组合的设置，能够使用<figure>和<figcaption>标签实现图文组合效果

7.5.3  图文组合

# 使用<figure>和<figcaption>标签设置图像和文字组合效果，如图：

7.5.3  图文组合

# 演示图像和文字在页面中的展示效果
在C:\code\chapter07\demo17.html文件中，编写代码使用<figure>和<figcaption>标签演示图像和文字组合效果。

<body>
  <div class="text-center">
    <figure class="figure">
      <img src="images/load-pic4.jpg" class="img-fluid figure-img">
      <figcaption class="figure-caption">我是一张笑脸</figcaption>
    </figure>
  </div>
</body>

STEP  01

7.5.3  图文组合

# 测试网页程序
运行demo17.html程序，查看图文组合效果。

STEP  02

7.5.3  图文组合

# 表格样式

7.6

# 先定一个小目标！

掌握表格样式的设置，能够实现美观的表格

7.6 表格样式

# 常见的作用于<table>元素的表格样式类

7.6 表格样式

| 类 | 描述 |
|---|---|
| .table | 基类，也就是表格的基本样式 |
| .table-dark | 设置颜色反转对比效果 |
| .table-striped | 条纹表格，设置斑马线效果，实现隔行换色 |
| .table-bordered | 带边框表格 |
| .table-borderless | 无边框表格 |
| .table-hover | 鼠标悬停效果，鼠标移动到行或单元格上，表格行变色 |
| .table-sm | 紧凑型表格 |
| .table-responsive | 响应式表格 |

# 常见的作用于<thead>的表头样式类

7.6 表格样式

Bootstrap 中还提供了作用于<tr> 行、<td> 标准单元格或<th> 表头单元格的样式类，用来设置指定意义的颜色。

Tip

| 类 | 描述 |
|---|---|
| .thead-light | 设置表头灰色背景 |
| .thead-dark | 设置表头黑色背景 |

# 常见的作用于<tr>、<td>或<th>元素的样式类

7.6 表格样式

| 类 | 描述 |
|---|---|
| .table-primary | 蓝色，首选颜色，指定这是一个重要的操作 |
| .table-secondary | 灰色，指定这是一个次重要的操作 |
| .table-success | 绿色，指定这是一个执行成功的操作 |
| .table-active | 灰色，指定鼠标悬停的效果 |
| .table-danger | 红色，指定这是一个危险的操作 |
| .table-info | 浅蓝色，指定这是一个提示信息的操作 |
| .table-warning | 橘色，指定这是一个警告的操作 |
| .table-dark | 深灰色 |
| .table-light | 浅灰色 |

# 使用表格样式，编写一个5行5列的表格，并使用.table-striped类实现表格隔行换色效果，如图：

7.6 表格样式

# 演示表格的隔行换色效果
在C:\code\chapter07\demo18.html文件中，编写一个5行5列的表格，并使用.table-striped类实现表格隔行换色效果。

<body>
  <table class="table table-striped table-bordered">
    <thead class="thead-dark">
      <tr><th>姓名</th><th>学号</th><th>语文</th><th>数学</th><th>英语</th></tr>
    </thead>
    <tbody>
      <tr><td>李四</td><td>01</td><td>70</td><td>69</td><td>84</td></tr>
      <!-- ...此处省略多个tr -->
    </tbody>
  </table>
</body>

STEP  01

7.6 表格样式

# 测试网页程序
运行demo18.html程序，查看表格隔行换色效果。

STEP  02

7.6 表格样式

# 辅助样式

7.7

# 先定一个小目标！

熟悉.bg-*类，能够根据需要的背景颜色选择合适的类

7.7.1  使用.bg-*类设置背景颜色

# 常见的元素背景颜色类

7.7.1  使用.bg-*类设置背景颜色

| 类 | 描述 |
|---|---|
| .bg-primary | 重要的背景颜色 |
| .bg-secondary | 副标题背景颜色 |
| .bg-success | 成功背景颜色 |
| .bg-danger | 危险提示背景颜色 |
| .bg-info | 一般提示信息背景颜色 |
| .bg-warning | 警告信息背景颜色 |
| .bg-dark | 深灰色背景 |
| .bg-light | 浅灰色背景 |
| .bg-white | 白色背景 |
| .bg-transparent | 透明背景 |

# 使用常见的元素背景颜色类设置元素背景颜色，效果如图：

7.7.1  使用.bg-*类设置背景颜色

# 7.7.1  使用.bg-*类设置背景颜色

演示常见的元素背景颜色在页面中的展示效果
在C:\code\chapter07\demo19.html文件中编写代码。

<body style="background-color: #f3f3f3;">
  <p class="bg-primary">.bg-primary效果（重要的背景颜色）</p>
  <p class="bg-secondary">.bg-secondary效果（副标题背景颜色）</p>
  <p class="bg-success">.bg-success效果（成功背景颜色）</p>
  <p class="bg-danger">.bg-danger效果（危险提示背景颜色）</p>
  <p class="bg-info">.bg-info效果（一般提示信息背景颜色）</p>
  <p class="bg-warning">.bg-warning效果（警告信息背景颜色）</p>
  <p class="bg-dark text-light">.bg-dark效果（深灰色背景）</p>
  <p class="bg-light">.bg-light效果（浅灰色背景）</p>
  <p class="bg-white">.bg-white效果（白色背景）</p>
  <p class="bg-transparent">.bg-transparent效果（透明背景色）</p>
</body>

STEP  01

# 7.7.1  使用.bg-*类设置背景颜色

STEP  02

测试网页程序
运行demo19.html程序，查看元素背景颜色效果。

# 先定一个小目标！

熟悉边框样式，能够根据需要实现元素边框的添加或移除，以及边框颜色的修改

7.7.2  设置边框样式

# 7.7.2  设置边框样式

添加或移除边框

Bootstrap给元素边框设置了.border基类，如果想要加其他的样式，都要在.border的基础上添加。

边框的样式可以组合使用，多个样式之间只需使用空格隔开即可。

Tip

# 使用.border-*类设置元素边框效果，如图：

7.7.2  设置边框样式

# 7.7.2  设置边框样式

<head>
  <style>
    span {width: 60px;height: 60px;display: inline-block;margin: 5px;}
  </style>
</head>
<body>
  <span class="border">添加四周边框</span>
  <span class="border border-0">移除四周边框</span>
  <span class="border border-top-0">移除上边框</span>
  <span class="border border-right-0">移除右边框</span>
  <span class="border border-bottom-0">移除下边框</span>
  <span class="border border-left-0">移除左边框</span>
</body>

STEP  01

演示常见的元素背景颜色在页面中的展示效果
在C:\code\chapter07\demo20.html文件中，使用.border-*类设置边框效果。

# 7.7.2  设置边框样式

STEP  02

测试网页程序
运行demo20.html程序，查看元素边框效果。

# 7.7.2  设置边框样式

设置边框颜色

Bootstrap 提供的.border 类默认边框颜色是淡灰色。在实际开发中如果想要修改边框颜色，可以使用.border-*类设置想要的场景颜色。

其中，“*”的取值为primary、secondary、success、danger、warning、info、light、dark、white，有兴趣的读者可以一一进行尝试，并在浏览器中查看边框颜色效果。

# 先定一个小目标！

熟悉元素间距的设置，能够使用.m-*和.p-*类设置元素间距大小和某侧边距值

7.7.3  设置元素间距

# 设置元素间距

在传统网站开发中，通常使用CSS中的margin或padding属性设置元素间距，具体如下：

margin用于设置元素的外边距，它影响元素与其相邻外部元素之间的距离；

padding用于设置元素的内边距，它影响元素与其内部子元素之间的距离。

在Bootstrap中同样提供了一组简写的.m-*和.p-*类，设置元素间距大小和某侧的边距值。

7.7.3  设置元素间距

# 设置元素内外边距

7.7.3  设置元素间距

| 类 | 样式设置 |
|---|---|
| .m-0（或.p-0） | 设置边距为0 |
| .m-1（或.p-1） | 设置margin或padding为0.25rem |
| .m-2（或.p-2） | 设置margin或padding为0.5rem |
| .m-3（或.p-3） | 设置margin或padding为1rem |
| .m-4（或.p-4） | 设置margin或padding为1.5rem |
| .m-5（或.p-5） | 设置margin或padding为3rem |
| .m-auto（或.p-auto） | 设置margin或padding为auto |

# 设置元素某侧的边距值

7.7.3  设置元素间距

Bootstrap 4中提供了t、b、l、r、x、y缩写来设置元素某一侧的间距，间距值可以选取0~5和auto ，具体如下：

t代表上边距

b代表下边距

l代表左边距

r代表右边距

x代表x轴的间距（左边距和右边距）

y代表y轴的间距（上边距和下边距）

# 7.7.3  设置元素间距

设置元素某侧内边距的类

| 类 | 等价的样式代码 |
|---|---|
| .pt-5 | { padding-top: 3rem !important; } |
| .pb-5 | { padding-bottom: 3rem !important; } |
| .pl-5 | { padding-left: 3rem !important; } |
| .pr-5 | { padding-right: 3rem !important; } |
| .px-5 | { padding-left: 3rem !important; padding-right: 3rem !important; } |
| .py-5 | { padding-top: 3rem !important; padding-bottom: 3rem !important; } |

# 本章小结

本章重点对Bootstrap所提供的样式风格进行了讲解。首先讲解了Bootstrap的标题样式、文本样式和列表样式的布局风格设计；其次讲解了代码样式和图文样式，包括设置响应式图像、图像布局模式及图文组合；然后讲解了表格样式；最后讲解了Bootstrap中的辅助样式，包括背景颜色、边框样式和设置元素间距。学完本章后，读者应掌握Bootstrap所提供的常用样式，能够实现优雅美观的页面布局效果。

本

章

小

结
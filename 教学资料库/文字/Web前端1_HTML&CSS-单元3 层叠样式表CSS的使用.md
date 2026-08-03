# HTML5+CSS3网页设计任务教程

单元3 层叠样式表CSS的使用

# 任务3-1 使用CSS设置body样式

任务3-2 使用CSS详细设置不同段落内样式

CONTANTS

任务3-3 全局样式和局部样式的使用

任务3-4 样式的并列和从属关系的应用

任务3-5 样式优先级的测试

任务3-6 使用伪类选择器定义超链接的显示效果

任务3-7 创建盒子模型

任务3-8 CSS浮动float属性的使用

任务3-9 常用文本样式属性的使用

任务3-10常用图片样式属性的使用

任务3-11 CSS3图片背景的使用

# 1

使用CSS设置body样式

任务3-1

CSS是Cascading Style Sheets的缩写，即层叠样式表，在标准网页设计中，CSS负责网页内容在浏览器内的显示样式，如文字大小、字体颜色、字体加粗等。
CSS由选择符和声明两部分组成，其中选择符又可称作选择器，是网页中要应用样式的元素；声明由属性和属性值两部分组成，属性与值之间用冒号隔开，每一个属性设置完属性值后，用分号结束，声明部分可以有多组属性和属性值组成，由一对｛｝括起来。例如：
p{
font-size:12px;
    color:red;
 }

# 2

使用CSS设置body样式

任务3-1

由CSS 样式代码插入的形式可以将CSS分为内联式、嵌入式和外部式三种。具体如下：
1、内联式：把CSS代码直接作为标签的style属性的内容写在现有的HTML标签（如p,span...）中，如：
<p style="color:red;font-size:12px;">
表示这个段落中的文字大小是12像素，字体颜色是红色。

# 3

使用CSS设置body样式

任务3-1

2、嵌入式：也称作内部样式表，把CSS样式写在标签
<style type="text/css"></style>之间，并且一般情况下嵌入式CSS样式写在<head></head>之间。

# 4

使用CSS设置body样式

任务3-1

3、外部式：把CSS代码写在一个单独的外部文件中存放在根目录的css文件夹下面，这个CSS样式文件以“.css”为扩展名，在<head>标签内使用<link>标签将CSS样式文件链接到HTML文件内：
 <link href="style.css" rel="stylesheet" type="text/css" />一般外部式的样式文件名字为style.css。

# 5

使用CSS设置body样式

任务3-1

这三种样式是有优先级的，原则上是就近原则，但如果CSS样式在相同权值的情况下，他们的优先级是：
内联式>嵌入式>外部式。

# 6

使用CSS设置body样式

任务3-1

1

2

网页背景颜色、背景图像的设置。

网页字体样式的设置。

3

网页页边距的设置。

# 7

使用CSS设置body样式

任务3-1

1、background-color: 背景颜色，background-image: 背景图像，background-repeat:背景重复，background-position:背景图像位置，background-attachment: 如何设置固定的背景图像，background: #ff0000 url(/i/eg_bg_03.gif) no-repeat fixed center / cover;
这些参数从左到右依次是：background-color、background-image、background-repeat、background-attachment、background-position / background-size。
值得注意的是background-size是CSS3的属性，它要与background-position配合使用，中间有一个斜杠分隔符。

# 8

使用CSS设置body样式

任务3-1

2、margin: 外边距，此处是指页边距，margin:20px;（上、下、左、右各20px），margin:20px 40px;（上、下20px；左、右40px），margin:20px 40px 60px;（上20px；左、右40px；下60px），margin:20px 40px 60px 80px;（上20px；右40px；下60px；左80px）
在css中使用margin可以将margin-top，margin-right，margin-bottom，margin-left，缩写为一个标记，顺序为上右下左（顺时针）。

# 9

使用CSS设置body样式

任务3-1

3、font-size: 字体大小
4、color: 字体颜色，如果采用6位16进制数，前面需要加上“#”。
5、font-family: Comic Sans MS, "微软雅黑";
先写英文字体，再写中文字体，会优先匹配英文字体，但是在英文字体中找不到中文字符，这样中文就会自动使用后写的中文字体了。
6、line-height: 文本行高，一般采用em单位，1em代表一倍行距。

# 10

使用CSS详细设置不同段落内样式

任务3-2

CSS最基本最常用的有三种选择器，分别是标签选择器、ID选择器和类选择器。
1、标签选择器：所谓标签选择器其实就是使用已有的html代码中的标签作为名称的选择器。
例如：p｛ font-size：12px；color：white；｝
就是将p标签设置为字体大小12像素，字体颜色为白色。

# 11

使用CSS详细设置不同段落内样式

任务3-2

2、ID选择器：即标识选择器，为标签设置“id=ID名称”，ID选择器定义时以“#”开头。按照规范ID选择器在一个html文件中只能使用一次。格式为：#ID选择器名称｛CSS样式代码｝
3、类选择器：与ID选择器类似，为标签设置“class=CLASS名称”，类选择器定义时以“.”开头。类选择器可以重复使用，应用最为广泛。格式为：.类选器名称{css样式代码;}

# 12

使用CSS详细设置不同段落内样式

任务3-2

所有的命名最好都小写。

1

2

3

h1到h6的定义，应遵循从大到小的原则，体现文档的结构。

表现与结构完全分离，代码中不涉及任何的表现元素。

4

5

6

7

8

9

10

属性的值一定要用双引号("")括起来。

每个标签都要有开始和结束，要有层次，有规律工整。

空元素要有结束的tag或于开始的tag后加上"/"。

给每一个表格和表单加上一个唯一的、结构标记id。

给图片加上alt标签。

尽量使用英文命名原则。

尽量不缩写，除非一看就明白的单词。

# 13

全局样式和局部样式的使用

任务3-3

全局样式，修饰网页所有标签的样式，一般采用元素选择器进行修饰。

1

2

局部样式，修饰网页部分标签的特殊样式，一般采用id选择器 ，css类选择器进行修饰。

# 14

样式的并列和从属关系的应用

任务3-4

.p1,.p2{
/*并列关系，设置p1和p2具有相同的样式，中间用逗号*/
}

1

2

.p2 span{
/*从属关系,分别设置p1和p2下的span样式，中间用空格*/
}

# 15

样式优先级的测试

任务3-5

CSS样式的优先级关系是：
内联样式>内部样式表>外部样式表
权值越大，优先级越高，在权值相同的情况下，后定义的样式优先级高。具体权值规定如下：
1、内联样式表的权值最高 1000。
2、ID 选择器的权值为 100。
3、Class 类选择器的权值为 10。
4、HTML 标签选择器的权值为 1。

# 16

使用伪类选择器定义超链接的显示效果

任务3-6

超链接<a>标签的常见状态及所代表的含义：
1、a:link：未访问的链接 
2、a:visited：已访问的链接
3、a:hover：鼠标移动到链接上
4、a:active：选定的链接，即鼠标按下去的时候不松开显示的状态

# 17

任务3-6

css选择器

要使用css对HTML页面中的元素实现一对一，一对多或者多对一的控制，这就需要用到CSS选择器。每一条css样式定义由两部分组成，形式如下： [code] 选择器{样式} [/code] 在{}之前的部分就是“选择器”。 “选择器”指明了{}中的“样式”的作用对象，也就是“样式”作用于网页中的哪些元素。

# 18

创建盒子模型

任务3-7

1

2

div默认不占据空间，没有颜色和边框等。

div默认宽度和浏览器一样长。

3

div宽度再小都要占据一整行。

# 19

创建盒子模型

任务3-7

# 20

创建盒子模型

任务3-7

margin是指从自身边框到另一个容器边框之间的距离，就是容器外距离。

1

2

padding是指自身边框到自身内部另一个容器边框之间的距离，就是容器内距离。

# 21

CSS浮动float属性的使用

任务3-8

float的作用，通过css定义float让div样式层块，向左或向右浮动。
float常跟属性值left、right、none。
float:none不使用浮动。
float:left靠左浮动。
float:right靠右浮动。

# 22

常用文本样式属性的使用

任务3-9

text-shadow: 5px 5px 5px #FF0000;
text-shadow属性的第一个值表示水平位移；第二个值表示垂直位移，正值偏右或偏下；负值偏上或偏左；第三个值表示模糊半径，该值可选；第四个值表示阴影的颜色，该值可选。

# 23

常用文本样式属性的使用

任务3-9

1

字体安装到客户机。

2

3

字体拷贝到服务器。

远程调用http://fonts.googleapis.com字体样式，需要联网。

# 24

常用文本样式属性的使用

任务3-9

1

径向渐变：background: radial-gradient(center, shape size, start-color, ..., last-color);

2

线性渐变：background: linear-gradient(direction, color-stop1, color-stop2, ...);

# 25

常用文本样式属性的使用

任务3-9

border-radius圆角属性是一个简写属性，用于设置四个 border-*-radius 属性：
border-radius-top-left          /*左上角*/
border-radius-top-right        /*右上角*/
border-radius-bottom-right    /*右下角*/
border-radius-bottom-left     /*左下角*/
也就是说，四个圆角属性按顺时针方向从左上角开始设置，具体语法格式为：
border-radius: 1-4 length|% / 1-4 length|%;

# 26

常用文本样式属性的使用

任务3-9

CSS3 Filter（滤镜）属性提供了模糊和改变元素颜色的功能，即图片特效功能。CSS3 Fitler 常用于调整图像的渲染、背景或边框显示效果。语法格式如下：
filter: none | <filter-function > [ <filter-function> ]* 
其默认值是none，他不具备继承性，其中filter-function有如下值可选：
grayscale：灰度，值为0-1之间的小数
sepia：褐色，值为0-1之间的小数
saturate：饱和度，值为num
hue-rotate：色相旋转，值为angle（角度）
invert：反色，值为0-1之间的小数
opacity：透明度，值为0-1之间的小数
brightness：亮度，值为0-1之间的小数
contrast：对比度，值为num
blur：模糊，值为length（长度）
drop-shadow 阴影

# 27

常用图片样式属性的使用

任务3-10

1

background-attachment属性使用。

2

3

4

background-position属性使用。

background-origin属性使用。

background-size属性使用。

# 28

CSS3图片背景的使用

任务3-11

background-origin属性用来指定背景图像的定位区域，即规定 background-position 属性相对于什么位置来定位。其语法格式为：
background-origin: padding-box|border-box|content-box;
1、padding-box(padding)：此值为background-origin的默认值，决定background-position起始位置从padding的外边缘（border的内边缘）开始显示背景图片。
2、border-box(border)：此值决定background-position起始位置从border的外边缘开始显示背景图片。
3、content-box(content)：此值决定background-position起始位置从content的外边缘（padding的内边缘）开始显示背景图片。

# 29

CSS3图片背景的使用

任务3-11

background-size属性用来指定背景图像的大小，其语法格式为：
background-size: length|percentage|cover|contain;
在具体使用时，在background-repeat属性值为no-repeat的情况下，如果容器宽高比与图片宽高比不同：
1、cover：图片宽高比不变、铺满整个容器的宽高，而图片多出的部分则会被截掉；
2、contain:图片自身的宽高比不变，缩放至图片自身能完全显示出来，所以容器会有留白区域；
3、background-size:auto：图片默认高度；
4、background-size:100px 50px：背景图片宽度100px，高度50px；
5、background-size:100px：背景图片高度和宽度都为100px；
6、background-size:100% 50%：背景图片宽度100%，高度50%；
7、background-size:50%：背景图片高度和宽度都为50%；

# 30

任务3-11

css重置样式

不同核心的浏览器对CSS的解析效果呈现各异，导致用户所期望的效果跟浏览器的“理解”效果可能会有偏差，CSS reset就是用来重置（复位）元素在不同核心浏览器下的默认值，尽量保证元素在不同浏览器下的同一“起跑线”。
https://www.cnblogs.com/staven/p/4818459.html
这个网站收集了常见网站CSS样式重置。

# HTML5+CSS3网页设计任务教程

单元3 层叠样式表CSS的使用
# <<JSP与Servlet开发技术与典型应用教程>>

JSP and  servlet  development  technology  and  typical application  course

第九章 Java Web应用中的文件操作

大连理工大学出版社

# 01

02

03

掌握文件上传下载功能开发各种应用系统

理解jxl读取Excel文件的方式、验证码的实现

了解使用字节流及字符流读取文件、在线影片观赏、MP3在线播放方法

能力目标

# 01

02

03

培养自主学习的习惯

培养知识迁移的能力

培养团队协作的能力

素质目标

# 9.1  Java  Web应用中的输入流与输出流

# 第九章 Java Web应用中的文件操作

本课任务：

Java  Web应用中的输入流与输出流
使用字节流及字符流读取文件
Java Web应用中的文件上传与下载
文件上传
文件下载
延伸阅读:如何使用jspSmartUpload进行上传下载

掌握：Java Web应用中的文件上传与下载

教学要求：

# Java  Web应用中的输入流与输出流

使用字节流及字符流读取文件

# Java  Web应用中的输入流与输出流

使用字节流及字符流读取文件

网络测试案例

# Java  Web应用中的输入流与输出流

使用字节流及字符流读取文件

网络测试案例

| 文件名 | 功能描述 |
|---|---|
| testing.jsp | 页面，测试题开始的欢迎页面。 |
| exercise.jsp | 页面，显示每一道测试题及选择答案。 |
| timeOut.jsp | 页面，答题30秒时间到达时的转向页面。 |
| UploadTesting.java | JavaBean组件，将文本中的测试题导入程序中的数组变量里保存。 |
| test.txt | 文本文件，网络测试题。 |

# 9.2  Java Web应用中的文件上传与下载

# Java Web应用中的文件上传与下载

文件上传

一般用户通过一个JSP页面上传文件至服务器时，该JSP页面都会包含File的表单类型，且表单必须将enctype的属性设置为multipart/form-data。
表单使用multipart/form-data属性值时，用户提交的数据就不再是以参数的形式提交，浏览器会把所有参数封装，在一个输入流里面进行提交，如果处理程序想要获得提交的数据值可以通过request.getInputStream()来获得。同时，根据HTTP协议文件，表单提交的信息中前4行和后面的5行是表单本身的信息，中间部分才是用户提交的文件的内容。

# Java Web应用中的文件上传与下载

文件下载

在Java Web应用中，用户也可以通过response.getOutputStream()方法来从服务器上下载文件。当用户下载时，根据HTTP协议response对象会向用户浏览器发送报头信息，说明文件的MIME类型，这样，浏览器就会调用相应的外部程序打开下载文件。

# Java Web应用中的文件上传与下载

延伸阅读： 如何使用jspSmartUpload进行上传下载

在Java Web应用中，经常使用第三方的组件来完成上传及下载功能。这里其中之一jspsmartupload组件，是一个免费使用的多功能文件上传下载组件，可以从网上下载直接使用。
        在Servlet2.5中，我们要实现文件上传功能时，一般都需要借助第三方开源组件，例如Apache的commons-fileupload组件，common-fileupload上传组件的jar包可以在apache官网上面下载，也可以在struts的lib文件夹下面找到，struts上传的功能是基于这个实现的。common-fileupload是依赖于common-io包的，需要下载这个包。 
        Servlet3.0中提供了对文件上传的原生支持，我们不需要借助任何第三方上传组件，直接使用Servlet3.0提供的API就能够实现文件上传功能。

# 实战演练

[实战 9-1]尝试使用JavaBean组件修改“例程9-6 uploadCheckDemo.jsp”、“例程9-8   downloadCheckDemo.jsp”、“例程9-10 upload.jsp”、“例程9-12 download.jsp”、“例程9-14   test.jsp”，使其成为一个完整独立的功能模块，以便其他系统使用。

[实战 9-2]尝试使用JavaBean制作一个日志记录组件，记录Java Web应用系统的方法执行情况及异常处理出错情况。例如“2010年9月12日8点38分21秒，LoginServlet类，doGet方法被调用；2021年9月13日7点21分30秒，LoginServlet类，doGet方法产生异常被捕获。

# 9.3  Java Web应用中的Excel文件读取操作

# 第九章 Java Web应用中的文件操作

本课任务：

Java Web应用中的Excel文件读取操作
什么是JXL
Excel文件的读取
Excel文件的写入
一个读取Excel文件的应用程序体验

掌握： jxl读取Excel文件的方式

教学要求：

# Java Web应用中的Excel文件读取操作

什么是JXL

Java Excel API是一开放源码项目， Java开发人员通过使用它可以读取Excel文件的内容、创建新的Excel文件、更新已经存在的Excel文件。而且使用该API非Windows操作系统也可以通过纯Java应用来处理Excel数据表。所以在Java Web应用中经常通过JSP、Servlet来调用此API来实现对Excel数据表的访问。

# Java Web应用中的Excel文件读取操作

Excel文件的读取

Java Excel API能够通过输入流从本地文件系统的一个文件(.xls)读取Excel电子表格。

# Java Web应用中的Excel文件读取操作

Excel文件的读取

读取Excel电子文档通常有以下步骤：使用Excel文件的File对象类型创建输入流InputStream，然后使用jxl包中的Workbook对象创建Excel工作薄，通过Sheet对象从工作薄中获取工作表，最后使用Cell对象在工作表中得到某个单元格。

# Java Web应用中的Excel文件读取操作

Excel文件的写入

在使用jxl生成电子文档时，其主要过程与读取Excel文档类似，也分为以下几步：首先使用OutputStream os=new FileOutputStream("c:\\excel2.xls")语句新建一个Excel文件，然后通过jxl.write.WritableWorkbook wwb = Workbook.createWorkbook(new File(os))语句创建Excel文件的工作簿，最后向Excel文件中写入数据。

# Java Web应用中的Excel文件读取操作

一个读取Excel文件的应用程序体验

Java Excel API也提供了一些工厂方法用于设定写入Excel电子文档中的数据的样式、类型及单元格样式。例如：添加的字体样式jxl.write.WritableFont wf = new jxl.write.WritableFont(WritableFont.TIMES, 18, WritableFont.BOLD, true); 添加Boolean对象jxl.write.Boolean labelB = new jxl.write.Boolean(0, 2, false)等等。具体可参见Java Excel API。

# 实战演练

[实战 9-1] 尝试修改 “例程9-14   test.jsp”，使其将excel.xls中导入的数据存入到数据库对应的表中。数据库表结构如下：

# 9.4  Java Web应用中的动态生成图像

# 第九章 Java Web应用中的文件操作

本课任务：

Java Web应用中的动态生成图像
动态生成图像的技术设计思路
延伸阅读：基于数据库的文件下载系统

掌握：验证码的实现

教学要求：

# 授课任务

动态生成图像的技术设计思路

动态生成图像首先需要创建一个BufferedImage的对象。 
创建BufferedImage对象后，需要获得图像环境对象Graphics或Graphics2D进行绘制。
获得图像环境对象后就可以根据应用需要绘制图像内容了。
最后释放掉图像环境，并将所完成的BufferedImage对象使用ImageIO()类中的函数发送至页面。

# Java Web应用中的动态生成图像

动态生成图像的技术设计思路

验证码是指将一系列随即产生的数字或特殊符号叠加到一幅图像里，同时在图像里加上一些干扰信息，用于防止恶意用户利用机器人程序自动注册、登录、灌水，以达到防止无限申请账号从而破坏服务器或暴力破解密码的目的。

| 文件名 | 功能描述 |
|---|---|
| Image.jsp | 页面，将验证码输出到客户端。 |
| login.jsp | 页面，注册页面，且显示验证码。 |
| handlingLogin.jsp | 页面，注册处理页面，且核对验证码。 |
| image.java | JavaBean组件，产生四位数的随机验证码。 |

# Java Web应用中的动态生成图像

延伸阅读：基于数据库的文件下载系统

在Java Web应用中对文件进行操作保存通常会使用到数据库。一般来说，上传到服务器中的文件信息有两种保存方案：
1．文件路径保存在数据库中，具体文件保存在服务器特定的文件夹中。这种方式文件上传和程序设计都很方便，容易被开发人员掌握，但缺陷是数据备份比较麻烦，不仅需要做文件系统备份，又要做数据库备份，而且两者要同时做，并保持版本一致。
2．文件路径和具体文件都保存在数据库中，且对应数据库中的两个不同字段。这种方式只需要做数据库备份即可，但在程序设计方法和逻辑上具有一定难度，涉及到对数据库进行文件读写。

# 本章小结

本章详细讨论了文件系统操作技术在Java Web应用中的使用方法，包括使用字节流及字符流读取文件、文件的上传与下载、jspSmartUpload插件的使用、Excel文件读取操作及动态图像生成技术。在本章最后“网站常用功能实现案例”中给出了网页中抓取代码、读取注册条款、缩放图片大小等案例。文件系统的这种灵活性应用在Java Web开发中有着极为重要的意义。
本章主要学习外部文件与Java Web代码之间的数据传输与交互、处理过程，这里需要读者站在整体架构的角度看待不同的模块是如何协同工作的，需要更加细致耐心地处理每个接口代码，从而达到运行效果。

# 实战演练

[实战 9-1] 制作一个小案例，能添加学生基本信息至数据库，并能查看每个学生的详细信息（包括照片）。分别采用两种方式保存照片：一种方式将图片保存在数据库中；另一种方式将图片上传到指定文件夹，在数据库中存放地址。数据库表结构如下：

| 班级 | 人数 | 辅导员 | 备注 | 毕业时间 |
|---|---|---|---|---|
| BJ | RS | FDY | BZ | BYSJ |

# <<JSP与Servlet开发技术与典型应用教程>>

感谢观看 THANK YOU!

大连理工大学出版社

第九章 Java Web应用中的文件操作
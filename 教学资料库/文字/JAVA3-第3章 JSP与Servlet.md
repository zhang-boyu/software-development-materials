# <<JSP与Servlet开发技术与典型应用教程>>

JSP and  servlet  development  technology  and  typical application  course

第三章    JSP与Servlet

大连理工大学出版社

# 01

02

03

掌握JDK、Tomcat和Eclipse安装与配置、Tomcat的管理程序

理解JSP与Servlet的关系、Servlet运行机制、JSP运行机制

了解Tomcat的体系结构、Servlet的基本结构

能力目标

# 01

02

03

培养代码规范的意识

培养科学严谨的态度

培养精益求精的工匠精神

素质目标

# 3.1 环境安装与配置

# 第三章   JSP与Servlet

本课任务：

环境安装与配置
JDK的安装与配置
Tomcat的安装与配置
Tomcat的体系结构
Tomcat的管理程序
Eclipse的安装与配置

# 第三章   JSP与Servlet

教学要求
1．掌握：JDK的安装与配置、Tomcat的安装与配置、MyEclipse的安装与配置
2．理解：Tomcat的管理程序
3．了解： Tomcat的体系结构

# 授课任务

JDK的安装与配置

JDK(Java Development Kit)是Sun Microsystems
（已被Oracle公司并购）推出的Java开发者工具包。  JDK是整个Java技术的核心，包括了Java运行环境，Java工具和Java基础的类库，JDK是其它Java开发工具的基础。

JDK的下载安装和运行环境的设置。
1．安装JDK
2．配置JDK
3．测试JDK

# 环境安装与配置

Tomcat的安装与配置

Jakarta Tomcat服务器是在SUN公司的JSWDK（JavaServer Web DevelopmentKit）的基础上发展起来的一个优秀的Servlet/JSP容器。
（1）双击安装程序，阅读使用的许可协议，点击“I Agree”进入下一步。
（2）选择安装的组件，默认是“Normal”，点击“Next”进入下一步。
（3）进行Tomcat的基本设置。
（4）选择已安装的JDK的目录路径。
（5）选择Tomcat的安装路径。
（6）程序开始安装，直至安装完成。

# 环境安装与配置

Tomcat的安装与配置

Tomcat安装后主要包括以下目录：
/bin：主要存放Windows平台以及Linux平台上启动和关闭Tomcat的文件。
/conf：存放Tomcat服务器的各种配置文件，其中最重要的配置文件是server.xml。
/logs：存放Tomcat的日志文件。
/webapps：当发布Web应用时，默认情况下把Web应用文件放于此文件下。
/works：Tomcat把由JSP生成的Servlet放于此目录下。

# 环境安装与配置

Tomcat的体系结构

1．体系结构




2．server.xml配置文件 
    server.xml是Tomcat最重要的配置文件，在其中对Tomcat中的各个组件进行配置，打开server.xml文件，就可以看到元素名和元素之间的嵌套关系，与Tomcat服务器的组件是一一对应的

# 环境安装与配置

Tomcat的管理程序

Tomcat提供了一个管理程序manager，用于管理部署到Tomcat服务器中的Web应用程序。

# 环境安装与配置

Eclipse的安装与配置

Eclipse是一个开放源代码、基于Java的可扩展开发平台，平台为编程人员提供了Java集成开发环境。 Eclipse的本身只是一个框架平台，但是众多插件的支持使得Eclipse拥有其他功能相对固定的IDE软件很难具有的灵活性。可以从官方网站下载Eclipse安装程序，Eclipse不用安装，直接运行eclipse目录下的eclipse.exe就可以运行。
（1）双击eclipse目录下的eclipse.exe。
（2）出现eclipse启动框，选择项目的工作目录，点击“Lanuch”会进入eclipse主界面。

# 环境安装与配置

Eclipse的安装与配置

可以在Eclipse中配置和使用系统中已安装的其他Java Web应用服务器.

# 3.2  Servlet是什么

# 第三章   JSP与Servlet

本课任务：

Servlet是什么
Servlet简介
基于Servlet的Java Web应用程序体验
Servlet配置
Servlet运行机制

掌握：基于Servlet的Java Web应用程序开发方法

教学要求：

# 授课任务

Servlet简介

Servlet即Java服务小程序，是使用应用程序设计接口以及相关类和方法的Java程序。Servlet在本质上就是Java类，编写Servlet需要遵循Java的基本语法，而且必需遵循特殊的规范，使用Servlet几乎可以处理HTTP协议各个方面的内容。

# Servlet是什么

基于Servlet的Java Web应用程序体验

下面使用Eclipse，完成第一个基于Servlet的Java Web应用程序开发

# Servlet是什么

Servlet配置

web.xml是Web应用的配置文件，是Web应用发布描述文件，是在Servlet规范中定义的。

# Servlet是什么

Servlet运行机制

Servlet容器在HTTP通信和Web服务器平台之间实现了一个抽象层。Servlet容器负责把请求传递给Servlet，并把结果返回给客户。

# 3.3 JSP是什么

# 第三章   JSP与Servlet

本课任务：

JSP是什么
JSP简介
基于JSP的Java Web应用程序体验

掌握：基于JSP的Java Web应用程序开发方法

教学要求：

# 授课任务

JSP简介

JSP(Java Server Pages)是基于Java语言的动态网页技术。由于基于Java技术，用JSP开发的Web应用是跨平台的，既能在Windows下运行，也能在其他操作系统上运行。

# JSP是什么

基于JSP的Java Web应用程序体验

下面使用Eclipse，完成一个基于JSP的Java Web应用程序开发

# 3.4 JSP与Servlet

# 第三章   JSP与Servlet

本课任务：

JSP与Servlet
Java Web应用程序介绍
JSP与Servlet的关系

理解： Java Web应用程序组成

教学要求：

# 授课任务

Java Web应用程序介绍

一个Java Web应用程序是由一组Servlet、JSP页面、HTML页面、Java类，以及其他的资源组成的运行在Web服务器上的应用程序。Java Web应用程序以一种结构化的有层次的目录形式存在。

# JSP与Servlet

JSP与Servlet的关系

JSP和Servlet都是动态的Web技术，JSP是以Servlet为基础开发，它被翻译成Servlet再执行，所以在底层运行机制上和Servlet有共同之处。

# 本章小结

Java Web应用的运行需要JDK和Java Web服务器的支持。JDK 是整个Java技术的核心，其中包括了Java运行环境，Java工具和Java基础的类库，JDK是其它Java开发工具的基础。Java Web服务器负责接收用户请求，并调用部署在其上的Java Web应用进行处理。
Tomcat是目前较流行的一种Java Web服务器，是Java Web应用的开发和调试一般使用专业的开发工具。Eclipse是功能丰富的JavaEE集成开发环境，包括了完备的编码、调试、测试和发布功能。
Servlet与JSP是Java Web技术中的两项重要技术。Servlet是使用应用程序设计接口以及相关类和方法的Java程序。它可以作为一种插件，提供诸如HTTP、FTP等协议服务甚至用户自已定制的协议服务，主要用于处理和客户之间的通信。JSP是在传统的HTML文件中插入Java程序段和JSP标记形成JSP文件。JSP是以Servlet为基础开发，它被翻译成Servlet再执行，所以在底层运行机制上和Servlet有共同之处。
在本章首先需明确专业领域内工作岗位和工作内容的社会价值，自觉树立正确的技能观和远大职业理想。提高综合职业素养，作为职业人专注、敬业、责任担当对完成好本职工作，进而促进软件行业整体的高水平。

# 实战演练

[实战 3-1]修改Tomcat的访问端口为2022。

# 实战演练

[实战 3-2]请编写一个Servlet程序和一个JSP程序，使两个程序在页面上显示“神舟十三号载人飞船发射圆满成功”。

# <<JSP与Servlet开发技术与典型应用教程>>

感谢观看 THANK YOU!

大连理工大学出版社

第三章    JSP与Servlet
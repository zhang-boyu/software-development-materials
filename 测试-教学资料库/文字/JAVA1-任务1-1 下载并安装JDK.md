# 无锡职业技术学院内部资料

JAVA程序设计

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

下载并安装Java程序的开发环境JDK21

# *

模块二 知识链接

什么是Java

Java语言特点

Java发展历程

什么是JDK

JDK目录介绍

# 模块二 
知识链接

什么是Java

Java是一种高级计算机语言，它是由SUN公司（已被Oracle公司收购）于1995年5月推出的一种可以编写跨平台应用软件、完全面向对象的程序设计语言。Java语言简单易用、安全可靠,自问世以来,与之相关的技术和应用发展得非常快。在计算机、移动电话、家用电器等领域中,Java技术无处不在。SUN公司将Java划分为三个技术平台，分别是Java SE、Java EE和Java ME。

# 什么是Java

Java SE（Java Platform Standard Edition）是标准版技术平台，它是为开发普通桌面和商务应用程序提供的解决方案。Java SE是三个平台中最核心的部分，Java EE和Java ME都是从Java SE的基础上发展而来的，Java SE平台中包括了Java最核心的类库，如集合、IO、数据库连接以及网络编程等。

Java SE

模块二 
知识链接

# 什么是Java

Java EE(Java Platform Enterprise Edition) 是企业版技术平台，它是为开发企业级应用程序提供的解决方案。Java EE平台用于开发、装配以及部署企业级应用程序，主要包括Servlet、JSP、JavaBean、JDBC、EJB、Web Service等技术。

Java EE

模块二 
知识链接

# 什么是Java

Java ME(Java Platform Micro Edition) 是小型版技术平台，它是为开发电子消费产品和嵌入式设备提供的解决方案。JavaME主要用于小型数字电子设备上软件程序的开发。例如，为家用电器增加智能化控制和联网功能，为手机增加新的游戏和通讯录管理功能。此外，Java ME还提供了HTTP等高级Internet协议，使移动电话能以Client/Server方式直接访问Internet的全部信息，提供高效率的无线交流。

Java ME

模块二 
知识链接

# Java语言特点

跨平台性

简单易用

Java语言安全可靠。Java编译器在编译程序时，不显示存储安排决策，Java程序中的存储是在程序运行时由Java解释程序决定

Java语言是一种相对简单的编程语言，能够通过最基本的方法完成指定的任务。

Java通过JVM（虚拟机）以及字节码实现跨平台。

安全可靠

模块二 
知识链接

# Java语言特点

Java语言是一个纯粹的面向对象程序设计语言，它提供了类、接口和继承等原语。

面向对象

分布式

Java语言支持多线程。多线程简单理解为程序中多个任务可以并发执行，多线程可以在很大程度上提高程序的执行效率。

Java是分布式语言，既支持各种层次的网络连接，又可以通过Socket类支持可靠的流(stream)进行网络连接。

支持多线程

模块二 
知识链接

# Java语言发展历程

模块二 
知识链接

| 时间 | 事件 |
|---|---|
| 1995年5月23日 | Java语言诞生 |
| 1998年12月8日 | Java 1.2企业平台J2EE发布 |
| 1999年6月 | SUN公司发布Java的3个版本：标准版（J2SE）、企业版（J2EE）和微型版（J2ME） |
| 2001年9月24日 | J2EE 1.3发布 |
| 2002年2月26日 | J2SE 1.4发布，自此Java的计算能力有了大幅提升 |
| 2004年9月30日 | J2SE 1.5的发布成为Java语言发展史上的又一里程碑。为了表示该版本的重要性，J2SE 1.5更名为Java SE 5.0 |

# Java语言发展历程

模块二 
知识链接

| 时间 | 事件 |
|---|---|
| 2005年6月 | JavaOne大会召开，SUN公司公开Java SE 6。自此，Java的各种版本进行了更名，取消了名称中的数字2，J2EE更名为Java EE，J2SE更名为Java SE，J2ME更名为Java ME |
| 2009年12月 | SUN公司发布Java EE 6 |
| 2011年7月 | Oracle公司发布Java SE 7 |
| 2014年3月 | Oracle公司发布Java SE 8 |
| 2017年9月 | Oracle公司发布Java SE 9 |
| 2018年3月 | Oracle公司发布Java SE 10 |
| 2018年9月 | Oracle公司发布Java SE 11 |
| 2019年3月 | Oracle公司发布Java SE 12 |

# Java语言发展历程

模块二 
知识链接

| 时间 | 事件 |
|---|---|
| 2019年9月 | Oracle公司发布Java SE 13 |
| 2020年3月 | Oracle公司发布Java SE 14 |
| 2020年9月 | Oracle公司发布Java SE 15 |
| 2021年3月 | Oracle公司发布Java SE 16 |
| 2021年5月 | Oracle公司发布Java SE 17 |
| 2022年3月 | Oracle公司发布Java SE 18 |
| 2023年9月 | Java SE 21Oracle公司发布 |
| 2024年9月 | Oracle公司发布Java SE 23 |
| 2025年3月 | Oracle公司发布Java SE 24 |
| 2025年9月 | Oracle公司发布Java SE 25 |

# 什么是JDK

定义：JDK(Java Development Kit)，是SUN公司提供的一套Java开发环境。
说明：JDK是整个Java的核心，其中包括Java编译器、Java运行工具、Java文档生成工具、Java打包工具等。1996年Sun 公司发布了最早的版本-JDK 1.0，随后相继推出了一系列更新版本,Java SE 25也是截至目前Java的最新版本，当然也不是版本越高越好，比如有的集成开服环境可能并不兼容更高的Java版本。

模块二 
知识链接

# 什么是JDK

Sun 公司除了提供JDK 以外,还提供了JRE(Java  Runtime Environment,Java 运行时环境)工具,它是提供给普通用户使用的Java运行环境。与JDK 相比,JRE 中只包含Java运行工具,不包含Java 编译工具。为了方便使用,Sun 公司在JDK 中封装了JRE,也就是说 Java 开发环境中包含Java运行环境，这样一来,开发人员只需要在计算机上安装JDK,就可以实现Java程序的编译和运行。

模块二 
知识链接

# 什么是JDK

JDK、JRE与JVM之间的主要关系和区别，如图1-1所示：

模块二 
知识链接

图1-1 JDK、JRE、JVM的关系

# JDK目录介绍

JDK安装完毕后，会在磁盘上生成一个目录，该目录被称为JDK安装目录。

存放可执行文件

存放JDK相关配置文件

存放头文件

存放调试文件

存放Java和各类模块的软件许可

存放Java类库或库文件

模块二 
知识链接

# *

过渡页

下载JDK

安装JDK

模块三  任务实现

测试是否安装成功

# 下载JDK

具体去Oracle官方网站下载即可，如图1-2所示：

模块三 
任务实现

图1-2  Windows操作系统JDK-21下载页面

# 安装JDK

模块三 
任务实现

图1-3 JDK安装页面

# 安装JDK

模块三 
任务实现

图1-4 JDK成功安装页面                图1-5  JDK目录页面

# 测试是否安装成功

模块三 
任务实现

在命令提示符窗口运行Javac命令和Java命令会分别出现图1-6和1-7的窗口说明安装正确。

图1-6  Javac命令运行页面               图1-7  Java 命令运行页面

# 感谢关注
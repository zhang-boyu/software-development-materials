# 第1章  Java开发入门

《Java基础入门（第3版）》

# 学习目标/Target

# 学习目标/Target

# 章节概述/ Summary

Java是一门高级程序设计语言，自问世以来，Java就受到了前所未有的关注，并成为计算机、移动电话、家用电器等领域中最受欢迎的开发语言之一。本章将针对Java语言的特点、发展史、开发运行环境、运行机制以及Java程序开发工具等内容进行介绍。

# 目录/Contents

# 目录/Contents

# Java概述

1.1

# 1.1.1  什么是Java

先定一个小目标！

# 1.1.1 什么是Java

Java是一种高级计算机语言，它是由SUN公司（已被Oracle公司收购）于1995年5月推出的一种可以编写跨平台应用软件、完全面向对象的程序设计语言。Java语言简单易用、安全可靠,自问世以来,与之相关的技术和应用发展得非常快。在计算机、移动电话、家用电器等领域中,Java技术无处不在。SUN公司将Java划分为三个技术平台，分别是Java SE、Java EE和Java ME。

什么是Java

# 1.1.1  什么是Java

Java SE

Java SE（Java Platform Standard Edition）是标准版技术平台，它是为开发普通桌面和商务应用程序提供的解决方案。Java SE是三个平台中最核心的部分，Java EE和Java ME都是从Java SE的基础上发展而来的，Java SE平台中包括了Java最核心的类库，如集合、IO、数据库连接以及网络编程等。

# 1.1.1  什么是Java

Java EE

Java EE(Java Platform Enterprise Edition) 是企业版技术平台，它是为开发企业级应用程序提供的解决方案。Java EE用于开发、装配以及部署企业级应用程序，主要包括Servlet、JSP、JavaBean、JDBC、EJB、Web Service等技术。

# 1.1.1  什么是Java

Java ME

Java ME(Java Platform Micro Edition) 是小型版技术平台，它是为开发电子消费产品和嵌入式设备提供的解决方案。JavaME主要用于小型数字电子设备上软件程序的开发。例如，为家用电器增加智能化控制和联网功能，为手机增加新的游戏和通讯录管理功能。此外，Java ME还提供了HTTP等高级Internet协议，使移动电话能以Client/Server方式直接访问Internet的全部信息，提供高效率的无线交流。

# 1.1.2  Java的特点

先定一个小目标！

# 1.1.2  Java的特点

安全性

简单

Java语言是一个纯粹的面向对象程序设计语言，它提供了类、接口和继承等原语。

Java语言是一种相对简单的编程语言，能够通过最基本的方法完成指定的任务。

Java语言安全可靠。Java编译器在编译程序时，不显示存储安排决策，Java程序中的存储是在程序运行时由Java解释程序决定。

面向对象

# 1.1.2  Java的特点

分布式

跨平台性

Java语言支持多线程。多线程简单理解为程序中多个任务可以并发执行，多线程可以在很大程度上提高程序的执行效率。

Java通过JVM（虚拟机）以及字节码实现跨平台。

Java是分布式语言，既支持各种层次的网络连接，又可以通过Socket类支持可靠的流(stream)进行网络连接。

支持多线程

# 1.1.3  Java的发展史

先定一个小目标！

# 1.1.3  Java的发展史

Java的发展史

Java的发展史具体如下表所示。

| 时间 | 事件 |
|---|---|
| 1995年5月23日 | Java语言诞生 |
| 1998年12月8日 | Java 1.2企业平台J2EE发布 |
| 1999年6月 | SUN公司发布Java的3个版本：标准版（J2SE）、企业版（J2EE）和微型版（J2ME） |
| 2001年9月24日 | J2EE 1.3发布 |
| 2002年2月26日 | J2SE 1.4发布，自此Java的计算能力有了大幅提升 |
| 2004年9月30日 | J2SE 1.5的发布成为Java语言发展史上的又一里程碑。为了表示该版本的重要性，J2SE 1.5更名为Java SE 5.0 |

# 1.1.3  Java的发展史

Java的发展史

| 时间 | 事件 |
|---|---|
| 2005年6月 | JavaOne大会召开，SUN公司公开Java SE 6。自此，Java的各种版本进行了更名，取消了名称中的数字2，J2EE更名为Java EE，J2SE更名为Java SE，J2ME更名为Java ME |
| 2009年12月 | SUN公司发布Java EE 6 |
| 2011年7月 | Oracle公司发布Java SE 7 |
| 2014年3月 | Oracle公司发布Java SE 8 |
| 2017年9月 | Oracle公司发布Java SE 9 |
| 2018年3月 | Oracle公司发布Java SE 10 |

# 1.1.3  Java的发展史

Java的发展史

| 时间 | 事件 |
|---|---|
| 2018年9月 | Oracle公司发布Java SE 11 |
| 2019年3月 | Oracle公司发布Java SE 12 |
| 2019年9月 | Oracle公司发布Java SE 13 |
| 2020年3月 | Oracle公司发布Java SE 14 |
| 2020年9月 | Oracle公司发布Java SE 15 |
| 2021年3月 | Oracle公司发布Java SE 16 |
| 2021年5月 | Oracle公司发布Java SE 17 |

# JDK的使用

1.2

# 1.2.1  安装JDK

先定一个小目标！

# 1.2.1  安装JDK

从Oracle官网下载安装文件“jdk-11.0.11-windows-x64-bin.exe” 找到安装文件的所在位置，双击文件，开始安装。

双击文件，进入JDK 11安装界面

JDK安装包

步骤一：下载安装包

# 1.2.1  安装JDK

步骤二：安装JDK

在下图中，单击“下一步”按钮进入JDK自定义安装界面。

# 1.2.1  安装JDK

步骤三：选择功能

在下图左侧有两个功能模块。开发工具和源代码，可以根据自己的需求选择所要安装的模块，本书选择“开发工具”模块。

# 1.2.1  安装JDK

步骤四：更改安装目录

在步骤三中，界面右侧有一个“更改”按钮，可以更改JDK的安装目录。确定安装目录之后，直接单击“确定”按钮即可。

# 1.2.1  安装JDK

步骤五：完成JDK安装

选择安装选项后，在步骤三中，单击“下一步”按钮开始安装。完成后进入如下界面，单击“关闭”按钮，关闭窗口，完成JDK安装。

# 1.2.2  JDK目录介绍

先定一个小目标！

# 1.2.2  JDK目录介绍

JDK安装完毕后，会在磁盘上生成一个目录，该目录被称为JDK安装目录。

JDK目录介绍

# 第一个Java程序

1.3

# 1.3  第一个Java程序

先定一个小目标！

掌握第一个Java程序，能够编写并运行HelloWorld程序

# 1.3  第一个Java程序

STEP  01

编写Java源文件。
在JDK安装目录的bin目录下新建文本文档，重命名HelloWorld.java。

public class HelloWord{
    public static void main(String[] args){
        System.out.println("hello world");
    }
}

# 1.3  第一个Java程序

运行程序。
输入“java HelloWorld”命令，运行编译好的字节码文件。

STEP  02

运行命令

运行结果

进入JDK安装目录的bin目录

编译Java
源文件

1

2

3

4

# 系统环境变量

1.4

# 1.4.1  PATH环境变量

先定一个小目标！

# 1.4.1  PATH环境变量

PATH环境变量介绍

PATH环境变量用于保存一系列命令（可执行程序）的路径，每个路径之间以分号分隔。当在命令行窗口运行一个命令时，操作系统首先会在当前目录下查找是否存在该命令对应的可执行文件，如果未找到，操作系统会继续在PATH环境变量中定义的路径下寻找这个文件，如果仍未找到，系统会报错。配置系统PATH环境变量的步骤如下。

# 1.4.1  PATH环境变量

查看Windows系统属性中的环境变量

右键单击桌面上的计算机→属性，在弹出的系统窗口左边选择“高级系统设置”选项，弹出系统属性对话框，在系统属性对话框的“高级”选项卡下单击“环境变量”按钮，弹出“环境变量”对话框。

# 1.4.1  PATH环境变量

设置PATH系统环境变量

系统变量对话框中，从系统变量区域选中名为PATH的系统变量，单击“编辑”按钮，弹出右侧的编辑环境变量对话框。

# 1.4.1  PATH环境变量

单击“新建”按钮，在弹出的输入框中添加javac命令所在的路径，例如，C:\Program\Files\Java\jdk-11.0.11\bin

# 1.4.1  PATH环境变量

查看PATH系统环境变量

打开命令行窗口,执行set PATH命令，查看设置后的PATH变量的变量值。环境变量中显示出了javac命令的路径信息。

# 1.4.1  PATH环境变量

在命令行窗口中执行javac命令，如果能正常地显示帮助信息，说明系统PATH环境变量配置成功，这样系统就会永久性地保存PATH环境变量的设置。

验证设置的PATH系统环境变量

# 先定一个小目标！

1.4.2  CLASSPATH环境变量

# 1.4.2  CLASSPATH环境变量

CLASSPATH环境变量介绍

CLASSPATH环境变量用于保存一系列类包的路径，它和PATH环境变量的查看与配置方式完全相同。当Java虚拟机需要运行一个类时，会在CLASSPATH环境变量定义的路径下寻找所需的.class文件和类包。

# 1.4.2  CLASSPATH环境变量

CLASSPATH环境变量配置

为了让Java虚拟机能找到所需的class文件，就需要对CLASSPATH环境变量进行设置，保存HelloWorld.class文件路径。在命令行窗口执行下面的命令。

set CLASSPATH=C:\Program Files\Java\jdk-11.0.11\bin

执行完上述命令之后，再次执行java HelloWorld命令运行程序。

# 1.4.2  CLASSPATH环境变量

命令运行结果

执行java HelloWorld命令运行程序，结果如下图所示。

由上图可知，Java HelloWorld命令成功运行，输出了“hello world”结果。在命令窗口中设置CLASSPATH后，程序会根据CLASSPATH的设置，去指定的目录寻找类文件，因此，虽然C盘根目录下没有HelloWorld.class文件，但Java HelloWorld命令仍能正确执行。

# Java的运行机制

1.5

# 1.5 Java程序的运行机制

先定一个小目标！

# 1.5 Java的运行机制

下面以1.3节中的第一个Java程序为例，对Java程序的编译运行过程进行详细地分析，程序从编写到运行的过程如下所示。

（1）编写HelloWorld.java文件。
（2）使用javac HelloWorld.java命令开启Java编译器，编译HelloWorld.java文件。编译结束后，编译器会自动生成一个名为HelloWorld.class的字节码文件。
（3）使用java HelloWorld命令启动Java虚拟机运行程序，Java虚拟机首先将编译好的字节码文件加载到内存，这个过程被称为类加载，由类加载器完成。然后Java虚拟机针对加载到内存中的Java类进行解释执行，输出运行结果。

Java程序的编译运行过程

# 1.5 Java的运行机制

通过上面的分析不难发现，Java程序是由Java虚拟机负责解释执行的，并非操作系统。这样做的好处是可以实现Java程序的跨平台。也就是说，在不同的操作系统上，可以运行相同的Java程序，不同操作系统只需安装不同版本的Java虚拟机即可。不同操作系统安装不同版本Java虚拟机示意图。

Java程序的编译运行过程

# 1.5 Java的运行机制

Java程序的跨平台特性，有效地解决了程序设计语言在不同操作系统编译时产生不同机器代码的问题，大大降低了程序开发和维护的成本。

Java虚拟机示意图

# IntelliJ IDEA开发工具

1.6

# IntelliJ IDEA简称IDEA，IDEA在智能代码助手、代码自动提示、重构、J2EE支持、Ant、JUnit、CVS整合、代码审查、创新的GUI设计等方面的功能是非常完善的。
本书后续章节的Java程序编写及运行都将采用IDEA开发工具。

1.6.  IntelliJ IDEA开发工具

# 先定一个小目标！

1.6.1  IntelliJ IDEA的安装与启动

# 1.6.1  IntelliJ IDEA的安装与启动

步骤一

登录IDEA官网下载IDEA安装包，旗舰版比社区版的组件更全面，因此这里我们选择使用旗舰版。

安装IDEA开发工具步骤

# 1.6.1  IntelliJ IDEA的安装与启动

下载完成后，双击安装包，进入IDEA安装欢迎界面，单击“Next”按钮，进入安装路径设置界面。

步骤二

# 步骤三

IDEA有默认安装路径，读者可以单击“Browser”按钮修改安装路径。设置完安装路径之后，单击“Next”按钮，进入基本安装选项配置界面。

1.6.1  IntelliJ IDEA的安装与启动

# 步骤四

勾选 “64-bit launcher”复选框。勾选了该复选框，IDEA在安装完成后会生成桌面快捷方式。勾选之后，单击“Next”按钮，进入选择开始菜单界面。

1.6.1  IntelliJ IDEA的安装与启动

# 步骤五

单击“Install”按钮开始安装IDEA，IDEA安装界面。

1.6.1  IntelliJ IDEA的安装与启动

# 步骤六

IDEA安装完成之后，会自动进入安装完成界面。

1.6.1  IntelliJ IDEA的安装与启动

# 步骤七

单击“Finish”按钮完成IDEA的安装。

1.6.1  IntelliJ IDEA的安装与启动

# 1.6.1  IntelliJ IDEA的安装与启动

IDEA启动完成后会弹出一个对话框，提示需要购买IDEA。因为IDEA旗舰版有30天免费试用期，所以这里我们可以关闭该对话框，免费使用IDEA。关闭提示购买的对话框之后，进入IDEA界面。

启动IDEA开发工具

# 先定一个小目标！

1.6.2  使用IntelliJ IDEA进行开发

# 1.6.2  使用IntelliJ IDEA进行开发

步骤一：单击“Create New Project”选项创建新项目，单击之后进入New Project界面。

创建Java项目具体步骤

# 1.6.2  使用IntelliJ IDEA进行开发

步骤二：需要设置Java程序开发所需要的JDK。在左侧栏选中Java，在右侧栏顶部Project SDK后面选择下载好的JDK，然后单击“Next”按钮进入选择模板创建项目界面。

# 1.6.2  使用IntelliJ IDEA进行开发

步骤三：需要设置Java程序开发所需要的JDK。在左侧栏选中Java，在右侧栏顶部Project SDK后面选择下载好的JDK，然后单击“Next”按钮进入选择模板创建项目界面

# 1.6.2  使用IntelliJ IDEA进行开发

步骤四：单击“Next”按钮进入项目设置界面。

# 1.6.2  使用IntelliJ IDEA进行开发

左侧栏是chapter01项目的目录结构，其中.idea目录下的所有文件，以及chapter01.iml文件都是IDEA开发工具使用的配置文件，不需要开发者操作。src是source单词的缩写，该目录用于保存程序的源文件。External Libraries是扩展类库，即Java程序编写和运行所依赖的JDK中的类。

# 1.6.2  使用IntelliJ IDEA进行开发

右键单击chapter01项目下的src目录，依次选择“New”→”Java Class”，进入New Java Class选项界面。

编写程序代码

# 1.6.2  使用IntelliJ IDEA进行开发

HelloWorld文件以.java为后缀名，右侧区域显示的是HelloWorld.java文件创建时的默认代码。其中，HelloWorld为类的名称；class为定义类的关键字；public是类的权限修饰符，表示该类是公有类，即所有Java程序均可访问该类；在HelloWorld后面的一对{}中，可以编写类的程序代码。

# 1.6.2  使用IntelliJ IDEA进行开发

我们可以在该文件中编写Java代码。

# 1.6.2  使用IntelliJ IDEA进行开发

单击工具栏中的“   ”按钮运行程序，控制台会显示运行结果。

运行程序

# 先定一个小目标！

1.6.3 IntelliJ IDEA调试工具

# 1.6.3 IntelliJ IDEA调试工具

IDEA自带了调试工具，下面以1.6.2节中的Java程序为例，演示IDEA调试工具的使用。首先在图1-39中的第7行代码设置断点，左键单击行号后面的空白区域，便可插入断点。然后单击“    ”调试按钮进入Dubug模式。

# 1.6.3 IntelliJ IDEA调试工具

常用调试快捷键

可以使用快捷键调试程序，IDEA常用的调试快捷键及含义，具体如下。

| 快捷键 | 操作名称 |
|---|---|
| F8 | 单步调试（不进入函数内部） |
| F7 | 单步调试（进入函数内部） |
| Shift+F7 | 选择要进入的函数 |
| Shift+F8 | 跳出函数 |
| Alt+F9 | 运行到断点 |
| Alt+F8 | 执行表达式查看结果 |
| F9 | 继续执行，进入下一个断点或执行完程序 |

# 本章小结

本章主要介绍Java开发入门的一些知识。首先介绍了Java语言、Java语言的相关特性和Java语言的发展史；其次介绍了JDK的概念，并在Windows 7系统中安装了JDK；然后带领读者编写了一个简单的Java程序，并讲解了环境变量的配置和Java程序的运行机制；最后为读者介绍了常用的Java开发工具IDEA，包括IDEA的特点、下载、安装以及入门程序的编写和调试。通过本章的学习，读者能够对Java语言有一个基础认识，为后面学习Java知识开启了大门。

本

章

小

结
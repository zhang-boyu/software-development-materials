# <<JSP与Servlet开发技术与典型应用教程>>

JSP and  servlet  development  technology  and  typical application  course

第五章   JSP基础

大连理工大学出版社

# 01

02

03

掌握JSP脚本标签的使用方法、JSP常用内置对象的使用方法

掌握JSP指令标签、JSP动作标签

了解JSP页面的基本结构、页面中文乱码问题

能力目标

# 01

02

03

培养观察辨别能力

培养分析与解决问题的能力

提升代码与文档书写规范意识

素质目标

04

培养精益细致的工匠精神

# 5.1  JSP语法

# JSP语法

本课任务：

JSP语法
JSP页面的基本结构 
JSP中的注释 
JSP脚本标签 
JSP指令标签 
JSP动作标签

# JSP语法

教学要求
1．掌握：JSP页面的基本结构
2．理解：JSP脚本标签和JSP动作标签
3．了解：JSP指令标签和JSP中的注释

# JSP语法

JSP页面的基本结构

JSP页面是由HTML、JavaScipt和CSS等静态网页技术代码与JSP动态网页技术代码混合编辑而成。当有用户访问某JSP页面时，其中的JSP动态网页技术代码会被当作Java程序代码解释执行，并动态生成静态网页技术代码与原有的静态代码混合发送到用户的网页浏览器中进行解释执行显示。

# JSP语法

JSP中的注释

1. 采用JSP语法，其形式为<%--注释内容--%>
2. 采用HTML语法，其形式为<!--注释内容-->

# JSP语法

JSP脚本标签

1．声明
声明是用来定义将在JSP页面中使用的变量和方法，在声明标签中声明的变量和方法在整个页面范围内是有效的。其语法如下：
<%!声明内容%> 

2. 代码段
在JSP页面中，Java代码段放在符号<%和%>之间。其语法如下：
<%代码段%>

3. 表达式
在JSP中通过表达式标签可以直接将表达式结果显示在网页中。表达式标签的语法如下：
<%=表达式%>

# JSP语法

JSP指令标签

JSP指令标签为JSP容器编译和执行JSP页面时提供相关信息，不会对当前输出流产生影响。其语法如下：
<%@ 指令名 属性名=”属性值”%>

指令名有三种：page,include和taglib。

# JSP语法

JSP指令标签 
 1. page指令
     page指令定义了一系列与页面相关的属性。其语法如下：
     <%@ page page_directive_attr_list %>

 2. include指令
     在JSP页面中通过include指令插入其他文件包含的文本或代码。其语法如下：
     <%@ include file="relativeURLspec" %>

 3. taglib指令
     在JSP页面设计时，用户可以使用扩展的标签实现相关功能，此时就需要通过taglib指令引入标签所属的标签库。taglib指令的语法如下：
     <%@ taglib (uri=”tagLibraryURI” | tagdir=”tagDir”) prefix=”tagPrefix” %>

# JSP语法

JSP动作标签 

          用户可以使用JSP动作标签向当前输出流输出数据，进行页面定向，也可以通过动作标签使用、修改和创建对象。

# JSP语法

1. <jsp:include>标签和<jsp:param>标签

       <jsp:include>标签将同一个Web应用中静态或动态的资源包含到当前页面中。
       语法如下：
                 <jsp:include page=”urlSpec” flush="true|false"/>
       在<jsp:include>标签中嵌套<jsp:param>标签还可以将参数传递给包含的资源。
       语法如下：
	         <jsp:include page=”urlSpec” flush="true|false">
		           <jsp:param name="name" value="value" />
	         </jsp:include>

JSP动作标签

# JSP语法

2. <jsp:forward>标签

	<jsp:forward>标签能实时的从当前JSP页面跳转到同一个Web应用中的静态资源、JSP页面或servlet，同时有效的终止当前JSP页面的执行。
      语法如下：
	                  <jsp:forward page=”relativeURLspec” />
	
	在<jsp:include>标签中嵌套<jsp:param>标签还可将参数传递给要跳转的页面。语法如下：
	                  <jsp: forward page=”urlSpec” >
		               <jsp:param name="name" value="value" />
	                  </jsp:forward>

JSP动作标签

# 5.2  JSP内置对象

# JSP内置对象

本课任务：

JSP内置对象  
request对象 
reponse对象 
session对象 
application对象
out对象 
config对象
page对象  
exception对象
pageContext对象

# JSP内置对象

教学要求
1．掌握：request对象，reponse对象，session对象和application对象的使用
2．理解：out对象，config对象和page对象 
3．了解：exception对象和pageContext对象

# 授课任务

当JSP页面处理一个用户访问请求时，可以创建或访问Java对象。通常情况下，在JSP页面中需先声明一个变量，然后将变量引用到某个实例化对象后才能使用。在JSP规范中指定了几个内置对象，可以直接使用，而不需要先进行声明和实例化。

# JSP内置对象

request对象
	request对象根据不同的访问协议对应各自的javax.servlet.ServletRequest的子类，对于HTTP协议，request对象的类型是javax.servlet.http.HttpServletRequest。

	request对象在JSP页面中的应用实例 
	1．接收用户表单信息  
	2．获取request对象中所有的参数 
	3．获取HTTP请求信息

# JSP内置对象

reponse对象
     
          reponse对象根据不同的访问协议的对应各自的javax.servlet.ServletResponse的子类，对于HTTP协议，reponse对象的类型是javax.servlet.http.HttpServletResponse。 
	
     reponse对象在JSP页面中的应用实例
	1．自动刷新页面 
	2．页面跳转

# JSP内置对象

session对象

session对象称为会话对象，其类javax.servlet.http.HttpSession，此对象是为发出请求的客户端创建，只对HTTP协议有效。

# JSP内置对象

application对象
    
      application对象代表Web服务器上的一个Web应用，其类型为javax.servlet.ServletContext。

# JSP内置对象

application对象的常用方法

| 方法名称 | 作用 |
|---|---|
| getMajorVersion( ) | 获取当前Web应用Sevlet的大版本号 |
| getMinorVersion( ) | 获取当前Web应用Sevlet的小版本号 |
| getRealPath(String path) | 将指定的虚拟路径转换为实际路径 |
| getServerInfo ( ) | 获取服务器信息 |
| log (String logs) | 将字符串参数写入到日志文件或输出到控制台 |
| setAttribute(String attName,Object obj ) | 将属性对象存放到application对象中 |
| getAttribute (String attName) | 获取当前application中指定的属性对象，返回值为Object类型 |
| getAttributeNames( ) | 获取当前application对象中所有的属性对象名，返回值为Enumeration枚举对象 |
| getInitParameterNames( ) | 获取web.xml文件中<context-param>标签配置的所有参数名，返回值为Enumeration枚举对象 |
| getInitParameter (String paramName) | 获取web.xmL文件中<context-param>标签配置的参数名为paramName指定的参数值 |

# JSP内置对象

out对象

out对象负责字符串信息的输出，其类型是javax.servlet.jsp.JspWriter。out对象的常用方法如下表所示。

| 方法名称 | 作用 |
|---|---|
| write | write方法共有5个重载方法，可以输出字符串、整数、字符数组以及子字符串等。 |
| print | print方法的作用与write方法的作用类似，但可输出的类型更多，其可以输出所有的java基本类型，字符串以及对象。 |
| println | println方法与print方法作用一样，但会在输出的字符串后加上一个换行符“\n”，此换行符只对输出页面的源文件产生效果。 |
| flush( ) | 将缓冲区的内容输出 |
| close( ) | 关闭out对象 |

# JSP内置对象

config对象
	   config对象包含了当前页面的配置信息，其类型为javax.servlet.ServletConfig。config对象的常用方法如下表所示。

| 方法名称 | 作用 |
|---|---|
| getServletContext ( ) | 获取application对象。获取的对象就是JSP内置的application对象。 |
| getInitParameterNames ( ) | 获取当前JSP页面所有初始参数名，返回值为Enumeration枚举对象 |
| getInitParameter (String paraname ) | 获取参数名为paramName指定的初始参数值 |
| getServletName ( ) | 获取servlet的名字 |

# JSP内置对象

page对象
      page代表本页面实现类的一个运行实例，其类型为java.lang.Object。
      page对象、request对象、session对象和application对象都可以在其生存周期内以属性的形式来保存数据对象，因此也可称为作用域对象。

# JSP内置对象

1．page scope：属性对象在当前页面有效，页面执行完毕后，属性变量随page对象被销毁。
	2．request scope：属性对象在同一个request请求内有效，例如使用<jsp:forward>动作标签从一个页面跳转到另一个页面时，这两个页面共有一个request对象，此request对象中的属性对象在两个页面都有效。
	3．session scope：属性对象在一个会话过程中都是有效的。
	4．application scope：属性对象在整个Web应用范围内都是有效的，可以在此Web应用中的所有页面中进行访问处理，直到Web应用停止运行。

# JSP内置对象

exception对象
	exception对象封装了页面执行时发生的异常信息，其类型为java.lang.Throwable。当页面执行发生异常时，相关错误信息会被封装到exception对象中抛出。缺省情况下，此exception对象会由当前页面的运行实例进行处理，并将错误信息显示出来。

# JSP内置对象

pageContext对象
	pageContext对象是当前页面的环境对象，其类型为javax.servlet.jsp.PageContext，通过此对象可以获取其他的JSP内置对象。通过pageContext对象还能够设置和获取4个范围对象中的属性。

# 典型模块应用

案例 5-1 Web直播聊天室
	本节以一个简单的Web直播聊天室功能实现来综合应用本章讲解的知识和技术。
	网页聊天室程序包含的相关文件及功能描述如下表所示。

| 文件名 | 功能描述 |
|---|---|
| login.jsp | 登录页面 |
| auth.jsp | 校验跳转页面 |
| chatframe.jsp | 聊天室框架页面 |
| chat.jsp | 聊天页面 |
| chatlist.jsp | 聊天记录页面 |
| user.jsp | 用户列表页面 |

# 典型模块应用

案例 5-1 网页聊天室

登录页面

聊天室页面

# 本章小结

JSP动态网页技术代码包括JSP脚本标签、JSP指令标签和JSP动作标签等。JSP脚本标签通常用作对象操作和数据运算，从而动态的生成页面内容。脚本标签包括声明，代码段和表达式。JSP指令标签为JSP容器编译和执行JSP页面时提供相关信息，不会对当前输出流产生影响。用户可以使用JSP动作标签向当前输出流输出数据，进行页面定向，也可以通过动作标签使用、修改和创建对象。JSP规范中提供了几种标准的动作标签，这些标签都是以JSP为前缀字符串。
           在JSP规范中指定了request、reponse、session、application、out、config、page、exception和pageContext等内置对象，这些对象在JSP页面设计中可以直接使用，而不需要先进行声明和实例化。

# 实战演练

[实战 5-1] 为本章网站案例Web直播聊天室增加一个聊天室密码校验功能，即在登录页面添加一个聊天室密码输入框，用户登录时应填写正确的聊天室密码--“654321”，否则会出现密码错误提示。

     [实战 5-2] 为本章网站案例Web直播聊天室增加一个新用户欢迎功能，即当一个新用户成功登录后，聊天记录中会显示欢迎该用户进入聊天室的信息。

     [实战 5-3] 为本章网站案例Web直播聊天室增加一个用户退出功能，即在聊天页面添加一个退出聊天室的超链接，当有用户点击此超链接退出时，在聊天记录中显示该用户退出聊天室的信息，同时在用户列表中删除该用户。

# <<JSP与Servlet开发技术与典型应用教程>>

感谢观看 THANK YOU!

大连理工大学出版社

第五章    JSP基础
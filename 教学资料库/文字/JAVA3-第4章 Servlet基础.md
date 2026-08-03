# <<JSP与Servlet开发技术与典型应用教程>>

JSP and  servlet  development  technology  and  typical application  course

第四章    Servlet基础

大连理工大学出版社

# 01

02

03

掌握Form数据的获取、Cookie和Session的使用、Form数据的获取

理解请求和转发的区别

了解Servlet生命周期、HTTP请求响应模型

能力目标

# 01

02

03

培养自主学习的习惯

培养知识迁移的能力

培养团队协作的能力

素质目标

# 4.1  HTTP请求响应模型

# 第四章   Servlet基础

本课任务：

HTTP请求响应模型

理解：HTTP请求响应模型

教学要求：

# 授课任务

当在浏览器中输入某个网址，浏览器就会呈现出这个网址对应的网页内容，在你每天上网浏览网页重复这个过程的时候，你是否想过浏览器是怎样向Web服务器发出请求，而Web服务器接受到请求后是如何处理然后返回响应的？浏览器与Web服务器的通信过程是基于HTTP协议的，HTTP（Hyper Text Transfer Protocol）是超文本传输协议的缩写，采用的是请求/响应模型。

# HTTP请求响应模型

分析HTTP请求响应模型过程如下：
1．连接至Web服务器
2．发送HTTP请求
3．服务端接受请求并返回HTTP响应
4．服务器关闭连接，浏览器解析HTTP响应

HTTP请求响应模型

# 4.2  Servlet实现

# 第四章   Servlet基础

本课任务：

Servlet实现

掌握：Servlet的实现方式

教学要求：

# 授课任务

基于HTTP的请求响应模型，Servlet容器在HTTP通信和Web服务器平台之间实现了一个抽象层。Servlet容器负责把请求传递给Servlet，并把结果响应返回给客户。而JSP则是以Servlet为基础开发，它被翻译成Servlet再执行。

# Servlet实现

其中Servlet API提供了大量的类和接口，熟悉Servlet API常用的类和接口是深入掌握和运用Serlvet技术的基础。

# Servlet实现

Annotation是与一个程序元素相关联信息或者元数据的标注，可以通过反射API获取到这些标注信息，可以在程序运行期间根据标识信息，对程序的执行作出相应的改变。Annotation不影响程序的执行，但是对例如编译器警告或者像文档生成器等辅助工具产生影响。
在Servlet3.0以后，web.xml中对Servlet配置，可以通过@WebServlet注解代替。在Servlet中，设置了@WebServlet注解，当请求该Servlet时，服务器就会自动读取其中的信息,注解@WebServlet("/ServletByHttpServlet")，则表示该Servlet默认的请求路径为“/ ServletByHttpServlet”，这里省略了urlPatterns属性名，完整的写法应该是“@WebServlet(urlPatterns = “/ServletByHttpServlet”)”，如果在@WebServlet中需要设置多个属性，必须给属性值加上属性名称，中间用逗号隔开,否则会报错。若没有设置@WebServlet的name属性，默认值会是Servlet的类完整名称。

# 4.3  Servlet生命周期

# 第四章 Servlet基础

本课任务：

Servlet生命周期

理解：Servlet生命周期

教学要求：

# 授课任务

Servlet部署在Servlet容器中，其生命周期由容器来管理，Servlet的生命周期开始于将它装入Web服务器的时，结束于终止或重新装入Servlet时。Servlet的生命周期通过javax.servlet.Servlet接口中的init()、service()和destroy()方法来表示。 。

# 4.4  Servlet请求处理及响应生成

# 第四章  Servlet基础

本课任务：

Servlet请求处理及响应生成
什么是Form表单数据
如何在Servlet中读取表单数据
 如何在Servlet中读取请求报头
什么是HTTP响应报头及HTTP状态代码
服务器响应的生成：HTTP响应报头及状态代码

# 第四章  Servlet基础

教学要求
1．掌握：如何在Servlet中读取表单数据、如何在Servlet中读取请求报头
2．理解：什么是Form表单数据、服务器响应的生成：HTTP响应报头及状态代码
3．了解：什么是HTTP响应报头及HTTP状态代码

# 授课任务

什么是Form表单数据

Form表单主要用于采集和提交用户输入的信息。

# Servlet请求处理及响应生成

如何在Servlet中读取表单数据

Servlet只需要调用HttpServletRequest的getParameter()方法，在调用参数中提供表单项的名字（大小写敏感）即可读取到表单数据，而且GET请求和POST请求的处理方法完全相同。
1．单个值的读取
使用getParameter(表单项)，getParameter()的返回值是一个字符串。如果指定的表单项存在，但没有值，getParameter()返回空字符串；如果指定的表单项不存在，则返回null。
2．多个值的读取
对于多选框，用户可能会选择多个选项，这个时候需要调用HttpServletRequest中的getParameterValues ()方法来获取值。getParameterValues ()的返回值是字符串数组。

# 4.5 HTTP请求响应模型应用程序体验

# 第四章  Servlet基础

本课任务：

HTTP请求响应模型应用程序体验

掌握： HTTP请求响应模型应用程序

教学要求：

# HTTP请求响应模型应用程序体验

完成一个登录验证功能。输入用户名和密码，提交后后台进行验证（在后台验证时先假设一个正确的用户名和密码），如果验证成功，显示登录成功界面；如果验证失败，回到登录界面重新登陆。在页面进行跳转时用到了设置HTTP头部信息进行页面跳转和通过sendRedirect()进行页面跳转等多种方式。

# 4.6 会话跟踪

# 第四章  Servlet基础

本课任务：

会话跟踪
Cookie的使用
Session的使用

教学要求：

掌握： Cookie的使用、Session的使用

# 授课任务

Cookie的使用

Cookie实际上是一小段的文本信息。客户端请求服务器，如果服务器需要记录该用户状态，就使用response向客户端浏览器颁发一个Cookie，客户端浏览器会把Cookie保存起来。当浏览器再请求该网站时，浏览器把请求的网址连同该Cookie一同提交给服务器，服务器检查该Cookie，以此来辨认用户状态。服务器还可以根据需要修改Cookie的内容。

# 会话跟踪

Cookie的使用

Cookie对象使用key-value属性对的形式保存用户状态，key表示Cookie的名字，名字必须是唯一的；value是Cookie对象中存放的数据，可以是任何对象。一个Cookie对象保存一个属性对，一个request或者response同时使用多个Cookie。
Cookie c = new Cookie(“Name”,str);
response.addCookie(c);

# 会话跟踪

Session的使用

Session是另一种记录客户状态的机制，不同的是Cookie保存在客户端浏览器中，而Session保存在服务器上。Session是一种连接状态变量，客户端浏览器访问服务器的时候，服务器把客户端信息以某种形式记录在服务器上。

HttpSession session = req.getSession(); //获取Session对象
session.setAttribute("loginTime", new Date());//设置Session中的属性

# 会话跟踪

Request、Cookie、Session三种存放会话信息方式比较

# 4.7  Servlet异常

# 第四章  Servlet基础

本课任务：

Servlet异常
ServletException类
ServletException类

教学要求：

理解： Servlet异常

# 授课任务

在javax.servlet包中定义了两个异常类，ServletException和UnavailableException。 
1 ServletException类
ServletException类定义了一个通用的异常，可以被init()、service()等方法抛出。
2 UnavailableException类
UnavailableException类是ServletException类的子类，该异常被Servlet抛出，用于向Servlet容器指示这个Servlet永久地或者暂时地不可用。

# 4.8 请求和转发

# 第四章  Servlet基础

本课任务：

请求和转发
RequestDispatcher接口
sendRedirect()与forward()方法的区别

教学要求：

掌握： sendRedirect()与forward()方法的使用

# 授课任务

RequestDispatcher接口

RequestDispatcher由Servlet容器创建，利用RequestDispatcher对象，可以把请求转发给其他的Servlet或JSP页面。
有三种方法可以用来得到RequestDispatcher对象。
1．利用ServletRequest接口中的getRequestDispatcher()方法：
public RequestDispatcher getRequestDispatcher(java.lang.String path)
2．利用ServletContext接口中的getNamedDispatcher()
public RequestDispatcher getNamedDispatcher (java.lang.String name)
3．利用ServletContext接口中的getRequestDispatcher()方法：
public RequestDispatcher getRequestDispatcher (java.lang.String path)

# 请求和转发

sendRedirect()与forward()方法的区别

# 4.9 Servlet上下文

# 第四章  Servlet基础

本课任务：

Servlet上下文

教学要求：

理解： ServletContext接口

# 授课任务

ServletContext接口定义了运行Servlet的Web应用的servlet视图。ServletContext实例是通过getServletContext()方法获得的。使用ServletContext对象，Servlet可以记录事件日志，获取资源的URL地址，并且设置和保存上下文内可以访问的其他servlet的属性。
ServletContext以web的已知路径为根路径。比如，假定一个Servlet上下文位于http://www.sina.com.cn/news。以/news请求路径开头的所有请求，已知为上下文路径，被路由到和该ServletContext关联的Web应用。

# 典型模块应用

案例 4-1 网上购物
网上购物是网站中一个常见的功能，用户首先在访问登录页面（Login），此页面会判断当前时间是上午还是下午，然后根据时间跳转到商品不同的购物页面（morningShow.html和afternoonShow.html）。在购物页面进行商品选择后，会提交到ShowBuy页面，显示所购买商品，可以回退反复进行选择商品，商品将会以一次排列下来。
网上购物程序中的文件

# 典型模块应用

案例 4-2 使用Cookie保存用户名密码

# 本章小结

Servlet API提供了大量的类和接口，熟悉Servlet API常用的类和接口是深入掌握和运用Serlvet技术的基础。Servlet配置相关的接口javax.servlet.ServletConfig主要用于Servlet容器在Servlet初始化期间传递信息给Servlet。Servlet实现常用到的相关类有javax.servlet.http.HttpServlet。
Servlet部署在Servlet容器中，其生命周期由容器来管理，Servlet的生命周期开始于将它装入Web服务器的时，结束于终止或重新装入Servlet时。
Servlet通过调用HttpServletRequest对象的相关方法读取表单数据和请求报头信息，调用HttpServletResponse对象的相关方法设置HTTP响应报头及状态代码。
HTTP协议是无状态的协议，服务器无法从连接上跟踪会话，因此在Java Web应用设计时通常使用Cookie和Session来跟踪会话，以弥补HTTP协议的不足。Cookie保存在客户端，而Session保存在服务器上。

# 本章小结

HttpServletResponse对象的sendRedirect方法与RequestDispatcher对象的forward方法都可以实现用户请求的转发，sendRedirect方法使客户端浏览器重新跳转到其指定的URL路径，而forward方法在服务器端内部将请求转发给另一个资源。
在编程时需强调代码规范，培养科学严谨、精益求精的工匠精神。工匠精神是一种职业精神，它是职业道德、职业能力和职业品质的体现，是从业者的一种职业价值取向和行为表现。在职位岗位上要保证软件系统运行时正确、稳定，保证客户的需求被精确采集和纳入软件开发计划，保证软件运行时遇到问题能被及时解决。

# 实战演练

[实战 4-1]修改4.5节中的HTTP请求响应模型应用程序，当登录成功后，转入loginOK.html时，需要在将登录者的用户名传入到loginOK.html页面并上显示出。
[实战 4-2] 使用Cookie完成一个基于浏览器的个性化网页设置。对于同一个页面，不同的客户端（不同的电脑）可以对其颜色、字体等进行个性化设置，设置后相互之间不影响。这样每次不同的客户端（不同的电脑）访问同一个页面看到的是自己个性化的网页。
[实战 4-3] 使用Session完成一个购物网站功能。在一个页面中进行购物，购物完成后跳转到另外一个页面显示所购商品的名称和数量，可以回到购物页面进行反复购物，商品数量进行累加。
 [实战 4-4] 选用合适的方式（sendRedirect，forward）完成一下功能。在A页面输入“天问一号”，提交给B页面，B页面自动跳转到C页面，将在A页面上输入的数据在C页面上显示。
[实战 4-5] 统计Web站点上的一个特定页面的访问次数，考虑这样一个场景，在某个新闻网站报道了神舟十二号载人飞船发射圆满成功，希望知道这个新闻每天的访问量。选用合适的方式（Session，Cookie）完成这个功能。

# <<JSP与Servlet开发技术与典型应用教程>>

感谢观看 THANK YOU!

大连理工大学出版社

第四章    Servlet基础
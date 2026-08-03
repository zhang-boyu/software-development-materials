# <<JSP与Servlet开发技术与典型应用教程>>

JSP and  servlet  development  technology  and  typical application  course

第十章    EL与JSTL

大连理工大学出版社

# 01

02

03

掌握EL表达式运算符、EL隐含对象、JSTL核心标签的使用方法

理解JSTL的XML标签、JSTL的格式化标签和JSTL的函数标签的应用

了解EL表达式特点，JSTL国际化标签的使用及在EL中如何定义使用函数

能力目标

# 01

02

培养用发展的观点来看待新技术出现与应用的能力

提升学习新技术的能力

素质目标

# 10.1  JSP2.0表达式语言（EL）

# JSP2.0表达式语言（EL）

本课任务：

JSP2.0表达式语言（EL） 
表达式语言简介 
表达式语言的使用 
访问对象属性和集合 
隐含对象

# JSP2.0表达式语言（EL）

教学要求
1．掌握：EL表达式运算符、EL隐含对象
2．理解：EL中定义使用函数 
3．了解：EL表达式特点

# 授课任务

表达式语言简介

EL（Expression Language）是表达式语言的英文缩写，结合了ECMAScript和XPath 表达式语言的特点，使页面设计者无需掌握复杂的编程语言就可以方便的访问和使用Web应用数据。EL最初是在JSTL 1.0中（基于JSP 1.2）定义的，随着其逐渐被广泛使用，EL成为了JSP规范（JSP 2.0/JSTL 1.1）的一部分，而不仅仅只作为JSTL的属性。

# JSP2.0表达式语言（EL）

表达式语言的使用
	
     EL表示方法很简单，其语法如下：
	${expression}
	JSP容器会对EL语句中的表达式（expression）进行取值，其结果根据EL语句在页面中的位置直接输出或者作为标签的属性值。

# JSP2.0表达式语言（EL）

表达式语言的使用
	1. 算术运算符
	算术运算符用于整数和浮点数的运算。在EL中定义了5个算术运算符，如下表所示。

| 运算符 | 含义 |
|---|---|
| + | 加法 |
| - | 减法 |
| * | 乘法 |
| / 或 div | 除法 |
| % 或 mod | 模运算 |

# JSP2.0表达式语言（EL）

表达式语言的使用
	2. 关系运算符
	关系运算符用于比较两个值之间的关系。在EL中共定义了6个关系运算符，如下表所示。

| 运算符 | 含义 |
|---|---|
| == 或eq | 等于 |
| != 或ne | 不等于 |
| < 或 lt | 小于 |
| > 或 gt | 大于 |
| <= 或 le | 小于等于 |
| >= 或 ge | 大于等于 |

# JSP2.0表达式语言（EL）

表达式语言的使用

3．逻辑运算符
逻辑运算符用于布尔型（Boolean）的值运算。在EL中共定义了3个关系运算符，如下表所示。

| 运算符 | 含义 |
|---|---|
| && 或 and | 逻辑与 |
| || 或 or | 逻辑或 |
| ! 或 not | 逻辑非 |

# JSP2.0表达式语言（EL）

表达式语言的使用
	4．Empty运算符
	Empty运算符是一个前缀运算符，用于判定后面的值是否为null或空，如果是则返回true。变量为null或空有不同的含义：null表示该变量不引用任何对象，而空表示该变量引用对象的内容为空。
	5．条件运算符—A ? B : C
	根据表达式A的结果，EL表达式取值为B或C。表达式A的取值应该为布尔型，如果不是则会进行强制类型转换。当表达式A取值为true时，则EL表达式的值为B，否则EL表达式的值为C。

# JSP2.0表达式语言（EL）

访问对象属性和集合
	  在EL中，使用符号“.”或“[ ]”来访问对象的属性。例如变量student引用类Student的一个实例对象，则可以通过表达式${student.name}或者${student[“name”]}来访问其name属性。当然对于Student类来说，name属性必须存在，而且提供了可访问的getName()方法。除此之外，以上语法还可以访问Map、List、Array中所含的对象，例如表达式${myArray[8]}用来访问myArray数组中的第9个元素。

# JSP2.0表达式语言（EL）

隐含对象
	
    	EL中提供了11个隐含对象，通过这些隐含对象，Web页面设计人员可以采取一种简单的方式获取相关的值和属性。

# JSP2.0表达式语言（EL）

隐含对象
	
     1．JSP隐含对象
	EL中的JSP隐含对象是pageContext，与同名的JSP内置对象是同一个对象。在EL中可以通过pageContext对象获取servletContext、session、request和response等对象，然后通过这些对象得到相关的信息。 
	2．作用域访问隐含对象
	EL中共有4个作用域访问隐含对象，分别是pageScope、requestScope、sessionScope和applicationScope。通过这些隐含对象可以很方便的访问对应作用域中的属性。

# JSP2.0表达式语言（EL）

隐含对象
	
	3．参数访问隐含对象
	在EL中可以通过param和paramValues两个隐含对象获取HTTP请求参数。
	param：获取的参数只有一个值，返回值的类型为String，其作用相当于request.getParameter方法。
	paramValues：获取的参数可能有多个值，返回值的类型为String数组，其作用相当于request.getParameterValues方法。

# JSP2.0表达式语言（EL）

隐含对象
	
     4．头部访问隐含对象
	在EL中通过header、headerValues和cookie隐含对象访问HTTP请求中头部或cookie中的信息。Header与headerValues的不同在于header返回值的类型为String，headerValues返回值的类型为String数组。 
	5．初始化参数访问隐含对象
	Web应用的一些初始化参数通常在Web应用的web.xml文件中进行设置，EL中可以通过初始化参数访问隐含对象iniParam来进行访问。

# JSP2.0表达式语言（EL）

定义使用函数
	
	在设计JSP页面时，可以通过自定义EL函数来实现代码重用的功能，从而提高开发效率。自定义的EL函数对应Java类中定义的静态方法，Java类可以自己设计，也可以直接使用JDK API中提供的类。在这里关键是如何将EL表达式与Java类中的静态方法关联起来。

# 10.2  JSP标准标签库（JSTL）

# JSP标准标签库（JSTL）

本课任务：

JSP标准标签库（JSTL） 
JSTL简介 
JSTL的核心标签 
JSTL的XML标签 
JSTL的格式化/国际化标签 
JSTL的函数标签

# JSP标准标签库（JSTL）

教学要求
1．掌握：JSTL核心标签
2．理解：JSTL的XML标签、JSTL的格式化标签、JSTL的函数标签 
3．了解：JSTL国际化标签

# 授课任务

JSTL简介
	
	   JSTL的全称是JavaServer Pages Standard Tag Library，即JSP标准标签库。它的出现是为了使那些不熟悉Java语法的页面设计者更高效的开发出JSP页面。通过JSTL，页面设计者可以用他们熟悉的标签方式来操纵动态数据。

# JSP标准标签库（JSTL）

JSTL简介

JSTL中的标记对应实现不同的功能，在JSTL 1.1规范中将其分为五类，构成五个子标记库，如下表所示。

| 功能类型 | URI | 前缀 | 例子 |
|---|---|---|---|
| 核心功能 | http://java.sun.com/jsp/jstl/core | c | <c:tagname ...> |
| XML文件处理 | http://java.sun.com/jsp/jstl/xml | x | <x:tagname ...> |
| Web应用国际化 | http://java.sun.com/jsp/jstl/fmt | fmt | <fmt:tagname...> |
| 数据库存取 | http://java.sun.com/jsp/jstl/sql | sql | <sql:tagname ...> |
| 函数 | http://java.sun.com/jsp/jstl/functions | fn | fn:functionName(…) |

# JSP标准标签库（JSTL）

JSTL的核心标签
	核心功能标记库中包含一组最常用的JSTL标签，这些标签按照功能被分为四类，分别是：
普通功能标签：<c:out>、<c:set>、<c:remove>、<c:catch>
流程控制标签：<c:if>、<c:choose>、<c:when>、<c:otherwise>
遍历操作标签：<c:forEach>、<c:forTokens>
URL操作标签：<c:import>、<c:url>、<c:redirect>、<c:param>

# JSP标准标签库（JSTL）

JSTL的XML标签
	JSTL为Web应用设计者提供了对XML格式文件进行基本操作的子标签库。该标签库中的标签按照功能被分为了三类，分别是：
XML核心标签：<x:parse>、<x:out>、<x:set>
XML流控制标签：<x:if>、<x:choose>、<x:when>、<x:otherwise>、<x:forEach>
XML转换标签：<x:transform>、<x:param>

# JSP标准标签库（JSTL）

JSTL的格式化/国际化标签
	
      JSTL提供了格式化/国际化标签库，在该标签库中的标签一共有12个，被分为了两类，分别是：
格式化标签：
    <fmt:timeZone>、<fmt:setTimeZone>、<fmt:formatNumber>、<fmt:parseNumber>、<fmt:formatDate>、<fmt:parseDate>
国际化标签：
    <fmt:setLocale>、<fmt:bundle>、<fmt:setBundle>、<fmt:message>、<fmt:param>、<fmt:requestEncoding>

# JSP标准标签库（JSTL）

JSTL的函数标签
	
	在JSTL中为EL提供了一些实用的函数标签来实现相应的功能。
获取collection接口实例对象的元素个数或字符串的长度：length
字符串大小写转换：toLowerCase、toUpperCase
获取子字符串：substring、substringAfter、substringBefore
去除字符串两端空格：trim
替换字符串中的字符：replace
检查字符串中是否包含指定的字符串：indexOf、startsWith、endsWith、contains、 containsIgnoreCase
分割字符串 (split)到数组, 以及连接数组元素组成数值 (join)
转换字符串中的 XML特殊字符：escapeXml

# 典型模块应用

案例 10-1 用户投票
	用户投票是网站中一个常见的功能，本节以一个简单的用户投票功能实现来综合应用本章讲解的知识和技术。在这个用户投票功能中，用户首先在用户投票页面选择最喜欢的休闲方式，提交后会看到投票统计结果。

用户投票页面

投票统计结果页面

# 典型模块应用

案例 10-2 JSTL数据有效性校验
	使用JSTL技术可以校验用户输入数据的有效性，本案例演示校验用户输入是否为空，密码和确认密码是否一致以及email地址中是否包含有效字符‘@’。

用户注册校验页面

# 本章小结

EL和JSTL使那些不熟悉Java语法的页面设计者能更高效的开发出JSP页面。EL语法简单，提供了多种运算符进行表达式运算，提供了简单的范围变量获取方式，提供了一系列隐含对象增强其数据处理和显示功能，用户还可以通过自定义函数来扩展EL的功能。JSTL提供了功能强大的标签来处理显示数据，其中包括核心标签、XML标签、格式化/国际化标签、数据库存取标签和函数标签。
              JSP技术解决了Servlet输出Web页面代码繁琐复杂的问题，而EL与JSTL技术的出现，通过EL表达式取值，通过JSTL来处理Web页面展示逻辑，使得Web页面设计更为简洁方便。IT技术是不断发展的，因此我们需要培养用发展的观点来看待新技术出现与应用的能力，不断提升学习新技术的能力。

# 实战演练

[实战 10-1]请使用本章学习的EL和JSTL技术设计一个网页四则运算器，用户可以输入两个数字，并选择运算符号，当用户点击等号按钮时，在本网页下方能出现运算结果。运行效果如下：
	



                        四则运算器页面1                                                                       四则运算器页面2

# 实战演练

[实战 10-2]当用户在上面设计的四则运算器页面中输入非数值型字符串进行计算时，页面会显示服务器产生的异常信息，这些信息对普通用户来说是没有意义的，请使用JSTL异常处理标记对此异常进行处理，并给出提示--“运算结果无效，请输入有效的数字！”
	运行效果如下：

# 实战演练

[实战 10-3]设计一个网页加法表达式计算器，可对类似“1+2+3+4”的加法表达式进行计算。提示：可通过<c:forTokens>标签对表达式进行解析。运行效果如下：

# 实战演练

[实战 10-4]使用JSTL中的XML标签对下面的store.xml文件进行解析，将其中所有的食品类别商品显示出来。
	
      store.xml
	 <?xml version="1.0" encoding="UTF-8"?>
	 <store>
		<category name="食品">
			<item name="面包" price="1.00"/>
			<item name="蛋糕" price="1.50"/>
			<item name="薯片" price="5.00"/>
		</category>
		<category name="日用品">
			<item name="牙膏" price="3.00"/>
			<item name="毛巾" price="2.00"/>		
		</category>	
	  </store>

# <<JSP与Servlet开发技术与典型应用教程>>

感谢观看 THANK YOU!

大连理工大学出版社

第十章    EL与JSTL
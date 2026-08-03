# <<JSP与Servlet开发技术与典型应用教程>>

JSP and  servlet  development  technology  and  typical application  course

第六章    Java Web的开发模式

大连理工大学出版社

# 01

02

03

掌握Java Web的两种开发模式、JavaBean的应用

理解共享JavaBean的四种方式、MVC模式

了解JavaBean的涵义、Java Web应用中优化编程的方式

能力目标

# 01

02

03

学会运用扬长避短兼容并收海纳百川的设计思维看待不同的开发模式

培养工程规范意识和高效协作团队精神

培养面对变化能持续成长的内驱力

素质目标

04

培养复用性，模块化思维能力

# 6.1  JavaBean的使用

# 第六章   Java Web的开发模式

本课任务：

JavaBean的使用
什么是JavaBean组件
使用JavaBean的原因
JavaBean的种类
在JSP中使用Bean

# 第六章   Java Web的开发模式

教学要求
1．掌握：JavaBean的应用
2．理解：共享JavaBean的四种方式
3．了解：JavaBean的涵义

# 授课任务

什么是JavaBean组件

一个标准的JavaBean组件具有以下几个特性：
 它是一个公开的（public）类。
 它必须拥有一个零参数的，即默认构造函数。
 它不应该有公开的实例变量。
 它提供setXxx()和getXxx()方法来对属性进行操作。
 对于boolean类型的属性，可以使用is代替get。

/*商品订单bean－－商品订单所有属性及方法*/
package edu.shop.entity;
 
public class ItemOrder {
	private Item item;
	private int numitems;
 
	public ItemOrder() {
	}
	public ItemOrder(Item item) {
		setItem(item);
		setNumitems(1);
	}
	// 获取所买商品
	public Item getItem() {
		return item;
	}
………

# JavaBean的使用

使用JavaBean的原因

为优化程序代码，提高其重复利用性 ,易于管理、易于维护 。

# JavaBean的使用

JavaBean的种类

JavaBean按其功能分类有两种：
1．可视化Bean（Visual  Bean）



2．非可视化Bean（Invisible  Bean） 
    （1）数据Bean（DataBean） 
    （2）功能Bean（ActionBean）

# JavaBean的使用

在JSP中使用Bean

在JSP中使用Bean有两种方式：
1．在JSP页面的代码段中将JavaBean作为一个普通的Java类进行使用 
2．通过JSP动作标签使用JavaBean，与使用JavaBean相关的标签有<jsp:useBean>、<jsp:setProperty>和<jsp:getProperty>。

# JavaBean的使用

在JSP中使用Bean

（1）<jsp:useBean>标签，格式如下：
<jsp:useBean   id= "**"   class= "**"   scope="**"/>
<jsp:useBean>标签在指定范围内获取或创建一个JavaBean。
属性scope设定bean的应用范围，其值有4种：page、request、session、application，默认为page。

scope取值page：JSP引擎分配给每个客户的bean是互不相同的，它们占有不同的内存空间，该bean的有效范围是当前页面，当客户离开这个页面时，JSP引擎取消分配给该客户的bean。
scope取值session：JSP引擎分配给每个客户的bean是互不相同的，该bean的有效范围是客户的会话期间。如果客户在某个页面更改了这个bean的属性，其它页面的这个bean的属性也将发生同样的变化。
scope取值request：JSP引擎分配给每个客户的bean是互不相同的，该bean的有效范围是request期间。JSP引擎对请求做出响应之后，取消分配给客户的这个bean。
scope取值application：所有客户共享这个bean，如果一个客户更改了这个bean的属性，所有客户的这个bean的属性也将发生同样的变化。这个bean直到服务器关闭才被取消。

# JavaBean的使用

在JSP中使用Bean

（2）<jsp:setProperty>标签，格式如下：
<jsp:setProperty  name="**"  property="**"  value='**'/>
<jsp:setProperty>标签用来设置JavaBean的属性值，属性name指定bean对象的变量名，属性property为要设置的对象属性名，属性value为设定的属性值。使用此标签会调用指定属性的set方法，因此在JavaBean类定义中必须有此属性的set方法，且此方法的访问控制符为public，否则执行此标签时会抛出异常。

# JavaBean的使用

在JSP中使用Bean

（3）<jsp:getProperty>标签，格式如下：
<jsp:getProperty  name="**"  property="**"/>
<jsp:getProperty>标签用来获取JavaBean的属性值，属性name指定bean对象的变量名，属性property为要获取的对象属性名。使用此标签会调用指定属性的get方法，因此在JavaBean类定义中必须有此属性的get方法，且此方法的访问控制符为public，否则执行此标签时会抛出异常。
JavaBean在JSP中还有一个很重要的机制：自省机制，即当服务器接收到请求时，它能根据请求的参数名称，自动设定与JavaBean相同属性名称的值。

# 实战演练

[实战 6-1]在网络应用程序中经常需要对字符串进行处理。请设计一个JavaBean，其功能是当用户在JSP页面Form表单的文本域输入的回车和空格转换成为JSP页面中输出的回车和空格，即：“<br>”和“&nbsp;”，运行效果如下：

# 实战演练

[实战 6-2] 请设计一个JavaBean，其功能是当用户在JSP页面Form表单的文本域输入字符串时，对字符串进行检查， 如果用户输入的是一段HTML语言进行显示，对该内容进行转换，显示用户输入的真实内容，运行效果如下：

# 实战演练

[实战 6-3]当开发网站时，会在多个页面的结尾重复地写入网站版权信息的HTML码，不利于维护且费时。请设计一个JavaBean，其功能是将输出版权信息的代码封装，利于代码多次应用及维护，运行效果如下：

# 6.2  JSP两种开发模式

# 第六章   Java Web的开发模式

本课任务：

JSP两种开发模式之一
JSP+JavaBean模式
基于JSP+JavaBean开发模式的应用程序体验

掌握：JSP+JavaBean模式

教学要求：

# 授课任务

JSP+JavaBean模式

在JSP+JavaBean开发模式中，主要使用JSP技术来实现界面设计，用户交互和数据呈现，JavaBean主要用来实现数据处理，数据传递以及数据库访问操作等。这样的开发模式使界面设计师与程序设计师能明确分工，并能同时进行工作，提供项目开发效率。另外实现特定功能的JavaBean可以在不同的JSP页面中进行重用，并且也可以在其他功能相近的项目中进行重用

# JSP开发模式

基于JSP+JavaBean开发模式的应用程序体验

下面通过一个购物结算程序来说明JSP+JavaBean的开发模式。在这个程序中，用户通过购买商品输入页面输入商品的名称，单价和数量，当用户点击提交按钮后页面就会跳转到购买商品清单页面，此页面显示用户购买的所有的商品明细以及应付总金额。

| 文件名 | 功能描述 |
|---|---|
| ItemShopping.java | JavaBean组件，定义了购买商品的相关信息。 |
| ShoppingInfo.java | JavaBean组件，定义了购买商品清单的相关信息。 |
| input.jsp | 页面，为用户提供了输入购买商品信息的界面。 |
| checkout.jsp | 页面，显示购买商品清单。 |

# 实战演练

[实战 6-1] 请设计一个JavaBean，功能是用户在JSP页面Form表单的文本域输入字符串后，对字符串进行检查，如果字符串中的某个字符为英文字母，则将该字符设置为红色。
[实战 6-2]请设计一个基于JSP+JavaBean模式的用户登录模块，当用户登录名为admin，密码为1234，转向至登录成功页面，否则登录失败，运行结果如下：

# 第六章   Java Web的开发模式

本课任务：

JSP两种开发模式之一
MVC模式
基于MVC开发模式的应用程序体验

掌握：MVC模式
理解：MVC模式中M层、V层、C层具体含义

教学要求：

# 授课任务

MVC模式

MVC(Model-View-Controller)模式，即模型-视图-控制器模式，其核心思想是将整个程序代码分成相对独立而又能协同工作的3个组成部分。如图6-11所示：
1．模型(Model)：业务逻辑层.实现具体的业务逻辑，状态管理的功能。
2．视图(View)：表示层.即与用户实现交互的界面，通常实现数据输入和输出功能。
3．控制器(Controller)：控制层.起到控制整个业务流程的作用，实现View和Model部分的协同工作。

# JSP开发模式

基于MVC开发模式的应用程序体验

MVC模式下的购物结算程序包含的相关文件及功能如表所示。

| 文件名 | 功能描述 |
|---|---|
| ItemShopping.java | JavaBean组件，定义了购买商品的相关信息。 |
| ShoppingInfo.java | JavaBean组件，定义了购买商品清单的相关信息。 |
| ConServlet.java | 在整个程序中充当控制器的角色，用于程序转向。 |
| input.jsp | 页面，为用户提供了输入购买商品信息的界面。 |
| checkMVC.jsp | 页面，显示购买商品清单。 |
| web.xml | 配置servlet相关信息。 |

# 典型模块应用

案例 6-1 过滤输入字符串中的危险符号 

案例 6-2 利用JavaBean解决中文乱码问题

案例 6-3 一个基于MVC模式的用户注册模块

# 本章小结

JavaBean在Java Web应用中是一种组件技术。它将内部的动作封装起来，使调用者看不到其运行机制，仅能通过它提供的最小限度的属性接口来完成操作。JavaBean在JSP页面中，既可以像使用普通类一样实例化，调用它的方法；也可以利用JSP技术中提供的动作标签来访问JavaBean，调用它的方法。
        在JSP+JavaBean开发模式中，主要使用JSP技术来实现界面设计，用户交互和数据呈现，JavaBean主要用来实现数据处理，数据传递以及数据库访问操作等。
        在MVC开发模式中，JSP技术主要负责Web应用与用户的交互以及业务数据的呈现等，起着视图的作用，JavaBean技术主要负责业务逻辑处理，数据库访问以及数据信息传递等，起着数据处理模型的作用，Servlet技术主要负责业务流程和数据流的控制，起着控制器的作用。

# 本章小结

在本章读者需要学会协调两个或者两个以上的不同资源或者个体代码，协同一致地完成一个目标的过程或能力。在工作中，协同合作也是非常重要的职业素养，大家都知道一根筷子轻轻被折断，但把更多的筷子放在一起，想要折断是很困难的事。
          团队协作的本质就是共同奉献。制定一个切实可行、具有挑战意义的目标，不分彼此，共同奉献。在一个团队里面，只有大家不断地分享自己的长处优点，不断吸取其它成员的长处优点，遇到问题都及时交流，才能让团队的力量发挥得淋漓尽致。

# 实战演练

[实战 6-1]请设计一个基于MVC模式的用户登录模块，当用户登录名为admin，密码为1234，转向至登录成功页面，否则登录失败，运行结果如下：

# <<JSP与Servlet开发技术与典型应用教程>>

感谢观看 THANK YOU!

大连理工大学出版社

第六章    Java Web的开发模式
# 无锡职业技术学院内部资料

JAVA程序设计

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

定义一个类，输出学生的班级+学号+姓名+年龄，将输出的学生信息分两行书写。

# *

模块二 知识链接

Java程序的基本格式

标识符的定义

关键字的使用

# Java程序的基本格式

Java程序代码必须放在一个类中，我们可以简单地将一个类理解为一个Java程序。类使用class关键字定义，在class前面可以有类的修饰符，修饰符可以是public、private等。类的定义格式如下：

模块二 
知识链接

修饰符 class 类名{
	程序代码
}

# Java程序的基本格式

模块二 
知识链接

编写Java程序的四点注意事项

（1）Java程序代码可分为结构定义语句和功能执行语句，其中，结构定义语句用于声明一个类或方法，功能执行语句用于实现具体的功能。每条功能执行语句的最后必须用分号(;)结束，如下面的语句。

System.out.println("这是第一个Java程序！");

注意：在程序中不要将英文的分号(;)误写成中文的分号（；），如果写成中文的分号，编译器会报告 “illegal character”（非法字符）错误信息。

# Java程序的基本格式

模块二 
知识链接

编写Java程序的四点注意事项

（2）Java语言是严格区分大小写的。在定义类时，不能将class写成Class，否则编译器会报错。程序中定义一个computer类的同时，还可以定义一个Computer类，computer和Computer是两个完全不同的符号，在使用时务必注意。

# Java程序的基本格式

模块二 
知识链接

编写Java程序的四点注意事项

（3）在编写Java程序时，出于可读性的考虑，应该让自己编写的程序代码整齐美观、层次清晰。常用的编排方式是一行只写一条语句，符号“{”与语句同行，符号“}”独占一行。

public class HelloWorld {
	public static void main(String[] args) {
		System.out.println("这是第一个Java程序！");
	}
}

# Java程序的基本格式

模块二 
知识链接

编写Java程序的四点注意事项

（4）Java程序中一个连续的字符串不能分成两行书写。例如，下面的语句在编译时会出错。

System.out.println("这是第一个
	 	Java程序！");

为了便于阅读，需要将一个比较长的字符串分两行书写，可以先将字符串分成两个字符串，然后用加号(+)将这两个字符串连起来，在加号(+)处换行，上面的语句可以修改成如下形式。

System.out.println("这是第一个" + 
 	    "Java程序！");

# 标识符的定义

模块二 
知识链接

在编程过程中，经常需要在程序中定义一些符号，用来标记一些名称，如包名、类名、方法名、参数名、变量名等，这些符号被称为标识符。标识符可以由字母、数字、下画线（_）和美元符号（$）组成，但标识符不能以数字开头，不能是Java中的关键字。

# 标识符的定义

模块二 
知识链接

合法标识符

username
username123
user_name
_userName
$username

123name     //不能以数字开头
  Class	     //不能是关键字
  98.3	     //不能是数字开头也不能包含特殊符号“.”
  Hello World //不能包含空格特殊字符

不合法标识符

标识符书写方式

# 标识符的定义

模块二 
知识链接

标识符书写规范

（1）包名所有字母一律小写。例如：cn.itcast.test。
（2）类名和接口名每个单词的首字母都大写。例如：ArrayList、Iterator。
（3）常量名所有字母都大写，单词之间用下画线连接。例如：DAY_OF_MONTH。
（4）变量名和方法名的第一个单词首字母小写，从第二个单词开始每个单词首字母大写。例如：lineNumber、getLineNumber。
（5）在程序中，应该尽量使用有意义的英文单词定义标识符，使得程序便于阅读。例如，使用userName定义用户名，password定义密码。

# 关键字的使用

模块二 
知识链接

关键字是编程语言里事先定义好并赋予了特殊含义的单词。和其他语言一样，Java中预留了许多关键字，下面列举了Java中所有的关键字。

Java关键字

| abstract | continue | for | new | switch |
|---|---|---|---|---|
| assert | default | goto | package | synchronized |
| boolean | do | if | private | this |
| break | double | implements | protected | throw |
| byte | else | import | public | throws |
| case | enum | instanceof | return | transient |
| catch | extends | int | short | try |
| char | final | interface | static | void |
| class | finally | long | strictfp | volatile |
| const | float | native | super | while |

# 关键字的使用

模块二 
知识链接

（1）所有的关键字都是小写。
（2）不能使用关键字命名标识符。
（3）const和goto是保留的关键字，虽然在Java中还没有任何意义，但在程序中不能
         用来作为自定义的标识符。
（4）true、false和null虽然不属于关键字，但它们具有特殊的意义，也不能作为标识
         符使用。

关键字使用的注意事项

编写Java程序时，关键字的使用需要注意以下几点。

# *

过渡页

定义一个类，输出学生的班级+学号+姓名+年龄，将输出的学生信息分两行书写。

模块三  任务实现

# 代码实现

1  public class Example01 {
2     public static void main(String[] args) {
3	System.out.println("我是软件2401班学号为001的学生，"
4				+ "我叫笑笑今年19岁。");
5	  }
6  }

模块三 
任务实现

文件2-1 Example01.Java

# 输出结果

模块三 
任务实现

图2-1 文件2-1运行结果

# 感谢关注
# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务1：定义一个测试类，创建Pet类（任务7-2中的Pet类）的实例，调用toString()方法并输出其内容。
子任务2：在Pet类（任务7-2中的Pet类）中重写toString()方法；定义一个测试类，创建Pet类的实例，调用toString()方法。

# ..

模块二 知识链接

Object类

Object类中常用方法

# Object类

模块二 
知识链接

Java提供了一个Object类，它是所有类的父类也叫根类，每个类都直接或间接继承了Object类，因此Object类通常被称为超类。当定义一个类时，如果没有使用extends关键字为这个类显式地指定父类，那么该类会默认继承Object类。Object 类为Java中的所有类提供了一些基础且非常重要的功能，比如对象的相等性比较、对象的哈希码生成、对象的字符串表示、以及对象的克隆等。

# Object类中常用方法

模块二 
知识链接

Object类中定义了一些常用方法，具体如表7-2所示。

表7-2 Object类中常用方法

| 方法名称 | 方法说明 |
|---|---|
| Boolean equals() | 判断两个对象是否“相等” |
| Int hashCode() | 返回对象的哈希值 |
| String toString() | 返回对象的字符串表示形式 |

# ，

过渡页

模块三  任务实现

子任务1：定义一个测试类，创建Pet类（任务7-2中的Pet类）的实例，调用toString()方法并输出其内容。

模块三 
任务实现

# 任务源码

子任务1：根据任务描述以及 Object类中常用方法知识点可以得到文件7-17所示的代码：

模块三 
任务实现

文件7-17  Example17

1public class Pet  {
2	 void shout() {
3		 System.out.println("宠物发出叫声");  
4	 }
5}
6public class Example17 {
7	public static void main(String[] args) {
8		Pet pet=new Pet();
9		System.out.println(pet.toString());
10	}
11}

# 运行结果

模块三 
任务实现

文件7-17的运行结果如图7-19所示:

图7-19文件7-17的运行结果

在实际开发中，通常情况下不会直接调用Object类中的方法，因为Object类中的方法并不能适用于所有的子类，这时就需要对Object类中的方法进行重写，以符合实际开发需求。以下子任务2对Object类中的toString()方法进行了重写。

# ，

过渡页

模块三  任务实现

子任务2：在Pet类（任务7-2中的Pet类）中重写toString()方法；定义一个测试类，创建Pet类的实例，调用toString()方法。

模块三 
任务实现

# 任务源码

子任务2：根据任务描述以及 Object类中常用方法知识点可以得到文件7-18所示的代码：

模块三 
任务实现

文件7-18  Example18

1public class Pet  {
2	 void shout() {
3		 System.out.println("宠物发出叫声");  
4	 }
5	 public String toString(){
6		 	return "这是一只宠物";
7		   }
8}
9public class Example18 {
10	public static void main(String[] args) {
11		Pet pet=new Pet();
12		System.out.println(pet.toString());
13	}
14}

# 运行结果

模块三 
任务实现

文件7-18的运行结果如图7-20所示：

图7-20文件7-18的运行结果

# 感谢关注
# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务1：定义一个父类Pet，其中包含name、age及其设置和获取方法；定义一个子类Cat继承于父类Pet;定义测试类输出Cat实例相关属性信息。

子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

# ..

模块二 知识链接

继承的概念

继承的优点

继承的注意事项

# 继承的概念

模块二 
知识链接

现实生活中，说到继承，通常会想到子女继承父辈的财产、事业等。在程序中，继承描述的是事物之间的所属关系，通过继承可以使多种事物之间形成一种关系体系。例如，猫和狗都属于动物，程序中便可以描述为猫和狗继承自动物，同理，波斯猫和巴厘猫继承猫科，而沙皮狗和斑点狗继承自犬科。

# 继承的概念

模块二 
知识链接

在Java中，继承是一种面向对象编程的特性，它允许我们定义一个类（称为子类或派生类）来继承另一个类（称为父类或基类）的属性和方法。通过继承，子类可以重用父类的代码即属性和方法，使得子类具有父类的特征和行为。并且还可以添加或覆盖父类中的方法以提供特定的功能。这种机制促进了代码的复用和模块化。

# 继承的概念

模块二 
知识链接

继承的语法格式：
class 父类{
  ……
 }
class 子类 extends 父类{
  …… 
}

如：
class Pet {  
    String name;  
      void eat() {  
        System.out.println(name + " is eating.");  
    }  
}  
class Cat extends Pet {  
    void hobby() {  
        System.out.println(name + " 喜欢晒太阳.");  
    }

# 继承的优点

模块二 
知识链接

代码复用：通过继承，子类可以重用父类的代码，减少代码冗余。
可扩展性：子类可以添加新的属性和方法，或者覆盖父类的方法来扩展其功能。
多态性基础：继承是多态性实现的基础之一，通过继承可以使得子类对象可以被当作父类对象来处理。

# 继承的注意事项

模块二 
知识链接

1.避免过度使用继承：虽然继承是强大的，但过度使用会导致类层次结构过于复杂，难以理解和维护。
2.注意继承的层次：Java中不支持多重继承（即一个类不能同时继承多个父类）。例如下面这种情况是不合法的。
class A{}
class B{}
class C extends A,B{}  // C类不可以同时继承A类和B类

# 继承的注意事项

模块二 
知识链接

3.多个类可以继承一个父类，例如下面这种情况是允许的。
class A{}
class B extends A{}   //类B继承类A
class C extends A{}   //类C继承类A
支持多层继承（即一个类可以继承一个类，而这个类又可以继承另一个类，以此类推）例如，C类继承自B类，而B类又可以继承自类A，这时，C类也可称作A类的子类。

# 继承的注意事项

模块二 
知识链接

例如下面这种情况是允许的。
class A{}
class B extends A{}   // 类B继承类A，类B是类A的子类
class C extends B{}   // 类C继承类B，类C是类B的子类，同时也是类 A的子类

# ，

过渡页

模块三  任务实现

子任务1：定义一个父类Pet，其中包含name、age及其设置和获取方法；定义一个子类Cat继承于父类Pet;定义测试类输出Cat实例相关属性信息。

模块三 
任务实现

# 任务源码

子任务1：结合任务描述和知识链接中继承知识点可以得到文件7-1所示的代码：

模块三 
任务实现

文件7-1 Example01.Java

1public class Pet {
2	 private String name;         		
3	 private int age;             		
4	 public String getName() {
5	        return name;
6	   }
7	 public void setName(String name) {
8	       this.name = name;
9	    }

10	 public int getAge() {
11	        return age;
12	    }
13	 public void setAge(int age) {
14	        this.age = age;
15    }
16	}

# 任务源码

子任务1：结合任务描述和知识链接中继承知识点可以得到文件7-1所示的代码：

模块三 
任务实现

文件7-1 Example01.Java

17public class Cat extends Pet { 
// 子类未定义任何属性和方法，只是继承于父类
}
18public class Example01 {
19	public static void main(String[] args) {
20		 Cat cat = new Cat(); // 创建并实例化Cat对象

21		 cat.setName("花花");// 访问父类Pet中的方法
22		 cat.setAge(3);       // 访问父类Pet中的方法
23		 System.out.println("这只小猫叫"+cat.getName()+"今年"+cat.getAge()+"岁了");
24	}
25}

# 运行结果

文件7-1的运行结果如图7-1所示:

模块三 
任务实现

图7-1 文件7-1的运行结果

# 任务源码

子任务2：结合任务描述和知识链接中继承知识点可以得到文件7-2所示的代码：

模块三 
任务实现

文件7-2 Example02.Java

1 public class Pet {
2	 private String name;         		
3	 private int age;             		
4	 public String getName() {
5	        return name;
6	   }
7	 public void setName(String name) {
8	       this.name = name;
9	    }

10	 public int getAge() {
11	        return age;
12	    }
13	 public void setAge(int age) {
14	        this.age = age;
15	    }
16	}

# 任务源码

子任务1：结合任务描述和知识链接中继承知识点可以得到文件7-1所示的代码：

模块三 
任务实现

文件7-1 Example01.Java

17 public class Cat extends Pet {
18	 private String color;        // 声明color属性
19	    public String getColor() {
20	        return color;
21	       }
22	   public void setColor(String color) {
23	        this.color = color;
24	   }
25}

26 public class Example02 {
27	public static void main(String[] args) {
28		 Cat cat = new Cat(); // 创建并实例化Cat对象
29		 cat.setName("花花");// 访问父类Pet中的方法
30		 cat.setAge(3);       // 访问父类Pet中的方法
31		 cat.setColor("黑色");// 访问子类Cat中的方法
32	     System.out.println("这只小猫叫"+cat.getName()+"今年"+cat.getAge()+"岁了，"+ "颜色是"+cat.getColor());
33	}
34}

# 运行结果

文件7-2的运行结果如图7-2所示:

模块三 
任务实现

图7-2 文件7-2的运行结果

# 感谢关注
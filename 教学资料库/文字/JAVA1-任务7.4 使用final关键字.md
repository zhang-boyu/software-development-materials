# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务1：使用final关键字修饰类
子任务2：使用final关键字修饰成员方法
子任务3：使用final关键字修饰变量

# ..

模块二 知识链接

final关键字修饰类

final关键字修饰成员方法

final关键字修饰变量

# final关键字

模块二 
知识链接

Java中的final关键字是一个非常重要的修饰符，它可以用于变量、方法和类。使用final关键字可以指示某个变量、方法或类的不可变性，即一旦被赋值（对于变量）、定义（对于方法）或创建（对于类），就不能再被改变。下面分别介绍final在这三种情况下的使用：

# final关键字

模块二 
知识链接

1.final关键字修饰类
当final修饰一个类时，这个类就不能被继承,也就是不能派生子类。这通常用于那些你确信不需要被扩展的类，或者出于安全考虑，防止类被恶意扩展。Java中使用final关键字修饰的类不可以被继承。

# final关键字

模块二 
知识链接

2.当一个类的方法被final关键字修饰后，该类的子类将不能重写该方法。

3.final关键字修饰变量

当final修饰一个变量时，这个变量就变成了常量，常量只能在声明时被赋值一次，其值一旦被初始化之后就不能再被改变。final变量必须在声明时或者在构造方法中被初始化。如果再次对final修饰的常量赋值，则程序会在编译时报错。

# final关键字

模块二 
知识链接

3.final关键字修饰变量

当final修饰一个变量时，这个变量就变成了常量，常量只能在声明时被赋值一次，其值一旦被初始化之后就不能再被改变。final变量必须在声明时或者在构造方法中被初始化。如果再次对final修饰的常量赋值，则程序会在编译时报错。

基本类型变量：final修饰的基本类型变量的值在初始化后不能被改变。
引用类型变量：final修饰的引用类型变量不能指向新的对象，但是对象本身的状态是可以被修改的（除非对象本身也是不可变的）。

# final关键字

模块二 
知识链接

3.final关键字修饰变量

final关键字在Java中用于表示不可变性，它可以用于变量、方法和类。通过final，你可以确保你的变量不会被意外修改，你的方法不会被子类覆盖，以及你的类不会成为其他类的基类。这些特性在增强代码的可读性、安全性和维护性方面都非常有用。

# ，

过渡页

模块三  任务实现

子任务1：使用final关键字修饰类

模块三 
任务实现

# 任务源码

结合任务描述和知识链接中使用final关键字修饰类知识点可以得到文件7-6所示的代码：

模块三 
任务实现

文件7-6 Example06.Java

1public final class Pet {
2	String name = "花花";
3   void shout() {
4        System.out.println("宠物发出叫声");
5}
6    }

7public class Cat extends Pet {
8		 }
9public class Example06 {
10	public static void main(String[] args) {
11		Cat cat = new Cat();  
12	}
13}

# 运行结果

模块三 
任务实现

文件7-6运行结果如图7-9所示：

图7-9文件7-6的运行结果

从上图可以看出，编译器报“无法从最终类Pet进行继承”错误，说明Cat类不能继承使用final修饰的Pet类。由此可见，被final关键字修饰的类不能被其他类继承。

# ，

过渡页

模块三  任务实现

子任务2：使用final关键字修饰成员方法

模块三 
任务实现

# 任务源码

结合任务描述和知识链接中使用final关键字修饰成员方法识点可以得到文件7-7所示的代码：

模块三 
任务实现

文件7-7 Example07.Java

1public  class Pet {
2	String name = "花花";
3    public final void shout() {
4        System.out.println("宠物发出叫声");
5}
6    }

7public class Cat extends Pet {
8	public void shout() {
9        System.out.println("喵喵……"); 
10	}
11	}
12public class Example07 {
13	Cat cat = new Cat();
14}

# 运行结果

模块三 
任务实现

文件7-7运行时会出现以下错误提示：
main" Java.lang.IncompatibleClassChangeError: class chpter7.Cat overrides final method chpter7.Pet.shout()
  由此可见，使用final关键字修饰父类Pet中的shout()方法，在子类Cat类中重写shout()方法时，编译报“Cat中的shout()无法覆盖Pet中的shout()被覆盖的方法为final”错误。这是因为Pet中的shout()方法被final关键字修饰，而子类不能对final关键字修饰的方法进行重写。

# ，

过渡页

模块三  任务实现

子任务3：使用final关键字修饰变量

模块三 
任务实现

# 任务源码

结合任务描述和知识链接中final关键字修饰变量识点可以得到文件7-8所示的代码：

模块三 
任务实现

文件7-8 Example08.Java

1public class Example08 {
2	public static void main(String[] args) {
3		  final int AGE = 6; 
4        AGE = 7;     
5	}
6}

# 运行结果

文件7-8运行结果如图7-10所示：

模块三 
任务实现

图7-10文件7-8的运行结果
从上图可以看出，程序编译时报错“无法为最终变量AGE分配值”，这是因为使用final定义的常量本身不可被修改。
注意：在使用final声明变量时，变量的名称要求全部的字母大写。如果一个程序中的变量使用public static final声明，则此变量将成为全局常量，如下面代码所示。
public static final String NAME="花花";

# 感谢关注
# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务1：定义一个接口Pet，接口中包括方法void eat()、void sleep()；定义类Cat,通过Cat类实现该接口并进行测试。
子任务2：在任务1的基础上定义一个抽象类Action,其中包括抽象方法shout();类Cat继承于Action类并实现Pet接口,定义一个测试类。

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务3：定义一个接口Pet，其中包括全局变量NAME和抽象方法void show()；定义一个接口Color,包括方法void color()；定义一个接口Action，包括抽象方法void shout()并且该接口继承于Pet、Color；定义Cat类用于实现接口Action；定义一个测试类。

# ..

模块二 知识链接

接口的概念

接口的特性

接口的用途

接口的定义

实现接口并继承抽象类

接口继承接口

# 接口的概念

模块二 
知识链接

在Java中，接口（Interface）是一种引用类型，是一种抽象的类型，它是方法声明的集合。接口中所有的方法都是隐式抽象的，即它们都没有方法体。接口是由抽象类衍生出来的一个概念，并由此产生了一种编程方式，可以称这种编程方式为面向接口编程。面向接口编程就是将程序的业务逻辑进行分离，以接口的形式去对接不同的业务模块。接口中不实现任何业务逻辑，业务逻辑由接口的实现类来完成。当业务需求变更时，只需要修改实现类中的业务逻辑，而不需要修改接口中的内容，以减少需求变更对系统产生的影响。在Java中，接口扮演着非常重要的角色，特别是在实现多态性和解耦方面。

# 接口的特性

模块二 
知识链接

抽象性：接口中的所有方法都是抽象方法，不能直接被实例化。
继承性：Java中的接口支持多继承，即一个接口可以继承多个其他接口。
实现性：一个类可以通过使用implements关键字实现一个或多个接口，从而必须提供接口中所有方法的实现（除了默认方法和静态方法，这些方法有默认实现，但也可以被覆盖）。
类型安全：接口可以作为引用类型，确保实现了该接口的类的实例能够按照接口的约定来执行操作，从而实现类型安全。
常量池：在Java 9之前，接口中的字段默认为public static final，这些字段在编译时就已经确定其值，并被放置在常量池中。从Java 9开始，接口可以包含私有字段和静态非final字段。

# 接口的用途

模块二 
知识链接

在Java中，使用接口的目的是为了克服单继承的限制，因为一个类只能有一个父类，而一个类可以同时实现多个父接口。在JDK 8之前，接口是由全局常量和抽象方法组成的。JDK 8对接口进行了重新定义，接口中除了抽象方法外，还可以定义默认方法和静态方法，默认方法使用default关键字修饰，静态方法使用static关键字修饰，且这两种方法都允许有方法体。

# 接口的用途

模块二 
知识链接

定义标准：接口定义了一组方法，但不实现它们。这些方法由实现接口的类来具体实现。这有助于定义一组公共的标准或协议。
解耦：通过接口，我们可以将类的实现与接口分开，这有助于降低类之间的耦合度，提高系统的可维护性和可扩展性。
多态性：通过接口引用，我们可以实现多态性，即可以使用接口类型的变量来引用实现了该接口的类的实例，并调用接口中定义的方法。

# 接口的定义

模块二 
知识链接

接口使用interface关键字声明，语法格式如下：
[public] interface 接口名 [extends 接口1,接口2...] {
	[public] [static] [final] 数据类型 常量名 = 常量;
	[public] [abstract] 返回值的数据类型 方法名(参数列表);
	[public] static 返回值的数据类型 方法名(参数列表){}
	[public] default 返回值的数据类型 方法名(参数列表){}
}

上述语法格式中,extends接口1,接口2,…”表示一个接口可以有多个父接口，父接口之间使用逗号分隔。接口中的变量默认使用public static final 进行修饰,即全局变量。接口中定义的抽象方法默认使用public abstract进行修饰。

# 接口的定义

模块二 
知识链接

例如：
interface Pet {  
    void eat();  
    void sleep();  
} 
注意：在很多的Java程序中，经常看到编写接口中的方法时省略了public ，有很多读者认为它的访问权限是default，这实际上是错误的。不管写不写访问权限，接口中方法的访问权限永远是public。

# 接口的实现

模块二 
知识链接

定义接口的实现类，语法格式如下：
修饰符 class 类名 implements 接口1,接口2,...{
    ...
}

# 接口的实现

模块二 
知识链接

例如：
Class Cat implements Pet {  
    public void eat() { 
        System.out.println("猫咪爱吃鱼");  
    }  
  public void sleep() {  
        System.out.println("猫咪喜欢中午睡觉");  
    }  
}

# 实现接口并继承抽象类

模块二 
知识链接

如果在开发中一个子类既要实现接口又要继承抽象类，则可以按照以下语法格式定义子类。
修饰符class 类名 extends 父类名 implements 接口1,接口2,... {
    ...
}

# 接口继承接口

模块二 
知识链接

在Java中，接口是不允许继承抽象类的，但是允许接口继承接口，并且一个接口可以同时继承多个接口。接口继承接口的方法可以参考前面接口定义的语法格式。

# ，

过渡页

模块三  任务实现

子任务1：定义一个接口Pet，接口中包括方法void eat()、void sleep()；定义类Cat,通过Cat类实现该接口并进行测试。

模块三 
任务实现

# 任务源码

子任务1：结合任务描述和知识链接中接口的定义和实现方法相关知识点可以得到文件7-10所示的代码：

模块三 
任务实现

文件7-10 Example10

//定义接口
1public interface Pet {
2	   void eat();  
3	   void sleep();  
}
//实现接口
4public class Cat implements Pet{
5	public void eat() {  
6        System.out.println("猫咪爱吃鱼");  
7    }  
8  public void sleep() {  
9        System.out.println("猫咪喜欢中午睡觉");  
10    }  
11}

//定义测试类
12public class Example10 {
13	public static void main(String[] args) {
14		Cat cat = new Cat();  
15		cat.eat();
16		cat.sleep();
17	}
18 }

# 运行结果

模块三 
任务实现

文件7-10的运行结果如图7-12所示：

图7-12文件7-10的运行结果

注意：接口的实现类，必须实现接口中的所有抽象方法，否则程序编译报错。

# ，

过渡页

模块三  任务实现

子任务2：在任务1的基础上定义一个抽象类Action,其中包括抽象方法shout();类Cat继承于Action类并实现Pet接口,定义一个测试类。

模块三 
任务实现

# 任务源码

结合任务描述和知识链接中接口的定义和实现方法、实现接口并继承抽象类相关知识点可以得到文件7-11所示的代码：

模块三 
任务实现

文件7-11  Example11

1 public interface Pet { 
2 void eat(); 
3 void sleep(); 
4 } 
5 public class Cat extends Action implements Pet{ 
仅供作者通读核对
131 
6 public void eat() { 
7 System.out.println("猫咪爱吃鱼"); 
8 } 
9 public void sleep() { 
10 System.out.println("猫咪喜欢中午睡觉"); 
11 } 
12 public void shout() { 
13 System.out.println("喵喵……"); 
14 } 
15 }

16 //定义测试类
17 public abstract class Action { 
18 public abstract void shout(); 
19 } 
20 public class Example11 { 
21 public static void main(String[] args) { 
22 Catcat = new Cat(); 
23 cat.eat(); 
24 cat.sleep(); 
25 cat.shout(); 
26 } 
27 }

# 运行结果

模块三 
任务实现

文件7-11的运行结果如图7-13所示：

图7-13 文件7-11的运行结果

由图7-12输出可知，Cat类成功重写了接口中的eat()和sleep()方法，也重写了抽象类中的shout()方法，这说明Cat类的实例化对象可以访问该类实现的接口和抽象类的方法。

# ，

过渡页

模块三  任务实现

子任务3：定义一个接口Pet，其中包括全局变量NAME和抽象方法void show()；定义一个接口Color,包括方法void color()；定义一个接口Action，包括抽象方法void shout()并且该接口继承于Pet、Color；定义Cat类用于实现接口Action；定义一个测试类。

模块三 
任务实现

# 任务源码

结合任务描述和知识链接中接口的定义和实现方法、实现接口并继承抽象类相关知识点可以得到文件7-12所示的代码：

模块三 
任务实现

文件7-12 Example12

1public interface Pet {
2	  public String NAME="花花";
3	  void show();
4}
5public interface Color {
6  void color();
7}
8public interface Action extends Pet,Color {
9void shout();
10}
11public class Cat implements  Action {
12  public void show() {  
13        System.out.println("这只猫叫"+NAME);  
14    }

15  public void color(){
16	  System.out.println("白色");
17  }
18  public void shout() {
19	  System.out.println("喵喵......"); 
20  }
21}
22public class Example12 {
23	public static void main(String[] args) {
24		Cat cat = new Cat();  
25		cat.show();
26		cat.color();
27		cat.shout();
28	}
29}

# 运行结果

模块三 
任务实现

文件7-12的运行结果如图7-14所示：

图7-14文件7-12的运行结果

由以上运行结果可知，Action接口继承了父接口 Pet和Color，在Cat类中实现了接口Action的方法void shout()和父接口 Pet的void show()方法和父接口Color的void color()方法。

# 感谢关注
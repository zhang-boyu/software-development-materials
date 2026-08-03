# 第3章  面向对象(上)

Java基础入门（第3版）

# 学习目标/Target

# 学习目标/Target

# 章节概述/ Summary

前面学习的知识都属于Java的基本程序设计范畴，属于结构化的程序开发，若使用结构化方法开发软件，其稳定性、可修改性和可重用性都比较差。在软件开发过程中，用户的需求随时都有可能发生变化，为了更好地适应用户需求的变化，Java语言采用了面向对象的程序设计思想。在接下来的章节中，将为读者详细讲解Java语言面向对象的特性。

# 目录/Contents

# 目录/Contents

# 面向对象的思想

3.1

# 3.1 面向对象的思想

先定一个小目标！

# 3.1 面向对象的思想

面向对象是一种符合人类思维习惯的编程思想。现实生活中存在各种形态不同的事物，这些事物之间存在着各种各样的联系。在程序中使用对象映射现实中的事物，使用对象的关系描述事物之间的联系，这种思想就是面向对象。面向对象是把构成问题的事物按照一定规则划分为多个独立的对象，然后通过调用对象的方法来解决问题。当然，一个应用程序会包含多个对象，通过多个对象的相互配合实现应用程序的功能，这样当应用程序功能发生变动时，只需要修改个别的对象就可以了，从而使代码维护起来更加方便。

面向对象思想

# 3.1 面向对象的思想

1．封装性

封装是面向对象的核心思想，它有两层含义，第一层含义是指把对象的属性和行为看成是一个密不可分的整体，将这两者“封装”在一起（即封装在对象中）；另外一层含义指“信息隐藏”，将不想让外界知道的信息隐藏起来。例如，驾校的学员学开车，只需要知道如何操作汽车，无需知道汽车内部是如何工作的。

# 3.1 面向对象的思想

2．继承性

继承性主要描述的是类与类之间的关系，通过继承，可以在原有类的基础上，对原有类的功能进行扩展。例如，有一个汽车类，该类描述了汽车的普通特性和功能。进一步再产生轿车类，而轿车类中不仅应该包含汽车的特性和功能，还应该增加轿车特有的功能，这时，可以让轿车类继承汽车类，在轿车类中单独添加轿车特性和方法就可以了。继承不仅增强了代码的复用性、提高了开发效率，还降低了程序产生错误的可能性，为程序的维护以及扩展提供了便利。

# 3.1 面向对象的思想

3．多态性

多态性是指在一个类中定义的属性和方法被其他类继承后，它们可以具有不同的数据类型或表现出不同的行为，这使得同一个属性和方法在不同的类中具有不同的语义。例如，汽车和飞机同样作为交通工具，汽车在陆地上行驶，而飞机在天空中飞行，所以不同的对象，所表现的行为是不一样的。多态的特性使程序更抽象、便捷，有助于开发人员设计程序时分组协同开发。

# 类与对象

3.2

# 3.2.1 类的定义

先定一个小目标！

# 3.2.1 类的定义

在面向对象的思想中最核心的就是对象，创建对象的前提是需要定义一个类，类是Java中一个重要的引用数据类型，也是组成Java程序的基本要素，所有的Java程序都是基于类的。
类是对象的抽象，用于描述一组对象的共同特征和行为。类中可以定义成员变量和成员方法，其中，成员变量用于描述对象的特征，成员变量也被称作对象的属性；成员方法用于描述对象的行为，可简称为方法。

类的定义

# 3.2.1 类的定义

类的语法格式定义

类的定义格式如下所示：

class 类名{
   成员变量；
   成员方法；
}

# 3.2.1 类的定义

class Student {
    String name;    	// 声明String类型的变量name
    int age;        	// 声明int类型的变量age
    String  sex;    	// 声明String类型的变量sex
	// 定义 read () 方法
	void read() {  
		System.out.println("大家好，我是" + name + ",我在看书!");
	}
}

以上代码中定义了一个学生类。其中，Student是类名，name、age、sex是成员变量，read()是成员方法，在成员方法read()中可以直接访问成员变量name。

根据上述格式定义一个学生类，成员变量包括姓名（name）、年龄（age）、性别（sex）；成员方法包括读书read()。学生类定义的示例代码如下所示。

# 脚下留心

局部变量与成员变量的不同

在Java中，定义在类中的变量被称为成员变量，定义在方法中的变量被称为局部变量。如果在某一个方法中定义的局部变量与成员变量同名，这种情况是允许的，此时，在方法中通过变量名访问到的是局部变量，而并非成员变量。请阅读下面的示例代码：

# 脚下留心

局部变量与成员变量的不同

class Student {
	int age = 30;    // 类中定义的变量被称作成员变量
	void read() {  
	     int age = 50;  // 方法内部定义的变量被称作局部变量
	     System.out.println("大家好，我" + age + "岁了,我在看书!");
	}
}

上述代码中，在Student类的read ()方法中有一条打印语句，打印了变量age，此时打印的是局部变量age，也就是说当有另外一个程序调用read()方法时，输出的age值为50，而不是30。

# 3.2.2 对象的创建与使用

先定一个小目标！

# 3.2.2 对象的创建与使用

上一节定义了一个Student类，要想使用一个类则必须要创建该类的对象。在Java程序中可以使用new关键字创建对象，使用new关键字创建对象的具体格式如下：

对象的创建格式

类名 对象名称 = null;
对象名称 = new 类名();

# 3.2.2 对象的创建与使用

上述格式中，创建对象分为声明对象和实例化对象两步，也可以直接通过下面的方式创建对象，具体格式如下：

类名 对象名称 = new 类名();

例如，创建Student类的实例对象，示例代码如下：

Student stu = new Student();

# 3.2.2 对象的创建与使用

class Student {
	String name;       							// 声明姓名属性
	void read() {  
	      System.out.println("大家好，我是" + name + ",我在看书!");
	}
}
public class Test {
    public static void main(String[] args[]) {  
	      Student stu = new Student();         //创建并实例化对象
	}
}

创建对象示例代码

了解对象的创建之后，就可以使用类创建对象，示例代码如下。

# 3.2.2 对象的创建与使用

上述代码在main()方法中实例化了一个Student对象，对象名称为stu。使用new关键字创建的对象是在堆内存分配空间。stu对象的内存分配如下图所示。

示例代码内存分析

# 3.2.2 对象的创建与使用

创建对象后，可以使用对象访问类中的某个属性或方法，对象属性和方法的访问通过“.”运算符实现，具体格式如下。

对象属性和方法的访问方式

对象名称.属性名
对象名称.方法名

# 3.2.2 对象的创建与使用

案例演示

下面通过一个案例学习对象属性的访问和方法的访问。具体代码如下所示。

1class Student {
 2	String name;       			// 声明姓名属性
 3	void read() {  
 4		System.out.println("大家好，我是" + name);
 5	}
 6}
 7public class Example01 {
 8	public static void main(String[] args) {
 9		Student stu1 = new Student(); // 创建第一个Student对象
 10	Student stu2 = new Student(); 		// 创建第二个Student对象
 11	stu1.name = "小明";                 	// 为stu1对象的name属性赋值
 12	stu1.read();                  			// 调用对象的方法
 13	stu2.name = "李华";
 14	stu2.read();
 15	}
 16}

# 3.2.2 对象的创建与使用

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 3.2.2 对象的创建与使用

由上图所示的运行结果分析可知，stu1对象和stu2对象在调用read()方法时，打印的name值不相同。这是因为stu1对象和stu2对象在系统内存中是两个完全独立的个体，它们分别拥有各自的name属性，对stu1对象的name属性进行赋值并不会影响到stu2对象name属性的值。

案例运行结果分析

# 3.2.2 对象的创建与使用

stu1对象和stu2对象的内存变化如下图所示。

由图可知，程序分别实例化了两个Student对象stu1和stu2，stu1和stu2分别指向各自的堆内存空间。

对象运行后内存变化分析

# 3.2.3 对象的引用传递

先定一个小目标！

# 3.2.3 对象的引用传递

类属于引用数据类型，引用数据类型就是指内存空间可以同时被多个栈内存引用。下面通过一个案例详细讲解对象的引用传递，具体代码如下所示。

1class Student {
 2	String name;       	// 声明姓名属性
 3     int age;           		// 声明年龄属性
 4	void read() {  
 5		System.out.println("大家好，我是"+name+"，年龄"+age);
 6	}
 7}
 8class Example02 {
 9	public static void main(String[] args) {

案例演示

# 3.2.3 对象的引用传递

10		Student stu1 = new Student();  //创建stu1对象并实例化
 11		Student stu2 = null; //创建stu2对象，但不对其进行实例化
 12		stu2 = stu1;              //stu1给stu2分配空间使用权
 13		stu1.name = "小明"; //为stu1对象的name属性赋值
 14		stu1.age = 20;
 15		stu2.age = 50;
 16		stu1.read();               //调用对象的方法
 17		stu2.read();
 18	}
 19}

案例演示

# 3.2.3 对象的引用传递

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 3.2.3 对象的引用传递

由上图所示的运行结果分析可知，stu1对象和stu2对象输出的内容是一致的，这是因为stu2对象获得了stu1对象的堆内存空间的使用权。在文件3-2中，第14行代码对stu1对象的age属性赋值之后，第15行代码通过stu2对象对age属性值进行了修改。实际上所谓的引用传递，就是将一个堆内存空间的使用权给多个栈内存空间使用，每个栈内存空间都可以修改堆内存空间的内容。

案例运行结果分析

# 3.2.3 对象的引用传递

stu1对象和stu2对象引用传递的内存分配如下图所示。

对象引用传递内存分配

# 3.2.3 对象的引用传递

# 第一步声明对象stu1和stu2，并使用new创建Student对象赋值给stu1，使用new创建对象时会开辟一个堆内存空间，对象stu1指向开辟的堆内存地址0x001；
第二步通过对象stu1给对象stu2分配内存空间使用权，对象stu2指向堆内存地址0x001；第三步由于对象stu1指向堆内存地址0x001，所以对象stu1修改属性值时，就是修改堆内存中对象的值，堆内存中name的值修改为“小明”，age的值修改为20；
第四步与第三步类似，对象stu2也指向堆内存地址0x001，堆内存中age的值修改为50，最终结果对象stu1的age属性值也是50。

注意：一个栈内存空间只能指向一个堆内存空间，如果想要再指向其他堆内存空间，就必须先断开已有的指向才能分配新的指向。

3.2.3 对象的引用传递

# 3.2.4 访问控制权限

先定一个小目标！

# 3.2.4 访问控制权限

在Java中，针对类、成员方法和属性，Java提供了4种访问控制权限，分别是private、default、protected和public。下面通过一张图将这4种访问控制权限按级别由小到大依次列出，如下图所示。

访问控制权限级别排序

# 3.2.4 访问控制权限

（1）private：private属于私有访问权限，用于修饰类的属性和方法，也可以修饰内部类。类的成员一旦使用了private关键字修饰，则该成员只能在本类中进行访问。

（2）default：default属于默认访问权限，如果一个类中的属性或方法没有任何的访问权限声明，则该属性或方法就是默认的访问权限，默认的访问权限可以被本包中的其他类访问，但是不能被其他包的类访问。

访问控制权限介绍

# 3.2.4 访问控制权限

（3）protected：protected属于受保护的访问权限。如果一个类中的成员使用了protected访问权限，则只能被本包及不同包的子类访问。

（4）public：public属于公共访问权限。如果一个类中的成员使用了public访问权限，则该成员可以在所有类中被访问，不管是否在同一包中。

访问控制权限介绍

# 3.2.4 访问控制权限

下面通过一张表总结上述访问控制权限，如下表所示。

访问控制权限的访问范围

| 访问范围 | private | default | protected | public |
|---|---|---|---|---|
| 同一类中 | √ | √ | √ | √ |
| 同一包中的类 |  | √ | √ | √ |
| 不同包的子类 |  |  | √ | √ |
| 全局范围 |  |  |  | √ |

# 3.2.4 访问控制权限

下面通过一段代码演示4种访问控制权限修饰符的用法，示例代码如下。

public class Test {
    public int aa;	//aa可以被所有的类访问
    protected boolean bb; //bb可以被所有子类以及本包的类访问
    void cc() { 	//默认访问权限，能在本包范围内问
        System.out.println("包访问权限");
    }
    //private权限的内部类，即这是私有的内部类，只能在本类中访问
    private class InnerClass {
    }
}

访问控制权限使用示例代码

# 3.2.4 访问控制权限

注意：外部类的访问权限只能是public或default，所以Test类只能使用public修饰或者不写修饰符。局部成员是没有访问权限控制的，因为局部成员只在其所在的作用域内起作用，不可能被其他类访问到，如果在程序中这样编写代码，编译器会报错。

访问控制权限使用注意

# 3.2.4 访问控制权限

public class Test {
    void cc() { 		      //默认访问权限，能在本包范围内使用
    	public int aa;                 //错误，局部变量没有访问权限控制
    	protected boolean bb; //错误，局部变量没有访问权限控制
        	System.out.println("包访问权限");
    }
    //private权限的内部类，即这是私有的内部类，只能在本类使用
    private class InnerClass {
    }
}

访问控制权限使用错误示例代码

错误示例代码如下所示。

# 3.2.4 访问控制权限

错误示例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 如果一个Java源文件中定义的所有类都没有使用public修饰，那么这个Java源文件的文件名可以是一切合法的文件名；如果一个源文件中定义了一个public修饰的类，那么这个源文件的文件名必须与public修饰的类名相同。

3.2.4 访问控制权限

小提示：Java程序的文件名

# 封装性

3.3

# 3.3.1 为什么要封装

先定一个小目标！

# 3.3.1 为什么要封装

在Java面向对象的思想中，封装是指一种将类的实现细节包装、隐藏起来的方法。封装可以被认为是一个保护屏障，防止本类的代码和数据被外部类定义的代码随机访问。下面通过一个例子具体讲解什么是封装，具体代码如下所示。

封装

# 3.3.1 为什么要封装

1class Student{
 2	String name;       // 声明姓名属性
 3              int age;               // 声明年龄属性
 4	void read() {  
 5	         System.out.println("大家好，我是"+name+"，年龄"+age);
 6	}
 7}
 8public class Example03 {
 9	public static void main(String[] args) {
 10		Student stu = new Student();	// 创建学生对象
 11		stu.name = "张三";// 为对象的name属性赋值
 12		stu.age = -18;// 为对象的age属性赋值
 13		stu.read();	              // 调用对象的方法
......

示例代码

# 3.3.1 为什么要封装

从上述代码中看，第12行代码将age（年龄）属性赋值为-18岁，这在程序中是不会有任何问题的，因为int的值可以取负数。但在现实中，-18明显是一个不合理的年龄值。为了避免这种错误的发生，在设计Student类时，应该对成员变量的访问作出一些限定，不允许外界随意访问，这就需要实现类的封装。

示例代码分析

# 3.3.2 如何实现封装

先定一个小目标！

# 3.3.2 如何实现封装

类的封装是指将对象的状态信息隐藏在对象内部，不允许外部程序直接访问对象的内部信息，而是通过该类提供的方法实现对内部信息的操作访问。封装的具体实现过程是，在定义一个类时，将类中的属性私有化，即使用private关键字修饰类的属性，私有属性只能在它所在的类中被访问。如果外界想要访问私有属性，需要提供一些使用public修饰的公有方法，其中包括用于获取属性值的getXxx()方法（也称为getter方法）和设置属性值的setXxx()方法（也称为setter方法）。

类的封装

# 3.3.2 如何实现封装

修改之前的案例，使用private关键字修饰name属性和age属性以及其对应的getter/setter方法，演示如何实现类的封装，只展示新增代码。

1     public String getName() {
 2        return name;
 3     }
 4     public void setName(String name) {
 5       this.name = name;
 6     }
 7  public int getAge() {
 8    return age;
 9  }
 10 public void setAge(int age) {
 11    if(age < 0){
 12       System.out.println("您输入的年龄有误！");
 13    } else {
 14    this.age = age;
 15    }
 16 }

案例演示

# 3.3.2 如何实现封装

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 构造方法

3.4

# 3.4.1 定义构造方法

先定一个小目标！

# 3.4.1 定义构造方法

构造方法是一个特殊的成员方法，在定义时，有以下几点需要注意。
     （1）构造方法的名称必须与类名一致。
     （2）构造方法名称前不能有任何返回值类型的声明。
     （3）不能在构造方法中使用return返回一个值，但可以单独写
             return语句作为方法的结束。

# 3.4.1 定义构造方法

下面通过一个案例演示构造方法的定义，具体代码如下所示。

1class Student{
 2	public Student() {  
 3		System.out.println("调用了无参构造方法");
 4	}
 5}
 6public class Example05 {
 7	public static void main(String[] args) {
 8             System.out.println("声明对象...");
 9             Student stu = null;         //声明对象
 10        System.out.println("实例化对象...");
 11        stu = new Student();     	//实例化对象
 12	}
 13}

案例演示

# 3.4.1 定义构造方法

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 由上图所示的运行结果分析可知，当调用关键字new实例化对象时，程序调用了Student类的无参构造方法。
一个类中除了定义无参的构造方法外，还可以定义有参的构造方法，通过有参的构造方法可以实现对属性的赋值。通过下面一个案例演示有参构造方法的定义与调用。

3.4.1 定义构造方法

案例运行结果分析

# 3.4.1 定义构造方法

1class Student{
 2    private String name;
 3    private int age;
 4    public Student(String n, int a) {
 5       name = n;
 6       age = a;
 7       System.out.println("调用了有参构造");
 8   }
 9   public void read(){
 10        System.out.println("我是:"+name+",年龄:"+age);
 11}
 12}
 13public class Example06 {
 14     public static void main(String[] args) {
 15         Student stu = new Student("张三",18); // 实例化Student对象
 16         stu.read();
......

案例演示

# 3.4.1 定义构造方法

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 3.4.2 构造方法的重载

先定一个小目标！

# 3.4.2 构造方法的重载

与普通方法一样，构造方法也可以重载，在一个类中可以定义多个构造方法，但是需要每个构造方法的参数类型或参数个数不同。在创建对象时，可以通过调用不同的构造方法为不同的属性赋值。

# 3.4.2 构造方法的重载

下面通过一个案例学习构造方法的重载，具体代码如下所示。

1class Student{
 2    private String name;
 3    private int age;
 4    public Student() { }
 5    public Student(String n) {
 6          name = n;
 7          System.out.println("调用了一个参数的构造方法");
 8    }
 9    public Student(String n,int a) {
 10          name = n;
 11          age = a;
 12          System.out.println("调用了两个参数的构造方法");
 13}

案例演示

# 3.4.2 构造方法的重载

14public void read(){
 15     System.out.println("我是:"+name+",年龄:"+age);
 16}
 17}
 18public class Example07 {
 19      public static void main(String[] args) {
 20         Student stu1 = new Student("张三");
 21         Student stu2 = new Student("张三",18);   // 实例化Student对象
 22         stu1.read();
 23         stu2.read();
 24      }
 25}

案例演示

# 3.4.2 构造方法的重载

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 多学一招

默认构造方法

在Java中的每个类都至少有一个构造方法，如果在一个类中没有定义构造方法，系统会自动为这个类创建一个默认的构造方法，这个默认的构造方法没有参数，方法体中没有任何代码，所以Java中默认的构造方法在程序运行时什么也不做。

# 多学一招

默认构造方法

下面程序中Student类的两种写法，效果是完全一样的。
第一种写法：


第二种写法：

class Student {
}

class Student {
   public Student(){
   }
}

# 多学一招

默认构造方法

由于系统提供的默认构造方法往往不能满足需求，因此，通常需要程序员自己在类中定义构造方法，一旦为类定义了构造方法，系统就不再提供默认的构造方法了，具体代码如下所示。

class Student {
     int age;
     public Student(int n) {
	age = n;
     }
}

# 多学一招

默认构造方法

1public class Example08 { 
 2	public static void main(String[] args) {
 3	     Student stu = new Student(); // 实例化 Student对象
 4	}
 5}

下面再编写一个测试程序调用上面的Student类，具体代码如下所示。

案例演示

# 多学一招

默认构造方法

案例运行结果

运行代码，控制台显示的运行结果如右图所示。

# 多学一招

默认构造方法

从上图可以看出，编译器提示“无法将com.itheima.Student类中构造器Student应用到给定类型”，原因是使用new Student ()创建Student类的实例对象时，需要调用无参构造方法，而Student类中定义了一个有参的构造方法，系统不再提供无参的构造方法。为了避免上面的错误，在一个类中如果定义了有参的构造方法，最好再定义一个无参的构造方法。
注意：构造方法通常使用public进行修饰。

运行结果分析

# this关键字

3.5

# 3.5.1 使用this关键字调用本类中的属性

先定一个小目标！

# 在实际开发中，如果成员变量和局部变量的名称设置成一样的，会导致成员变量和局部变量的名称冲突。下面通过一个案例进行验证，具体代码如下所示。

3.5.1 使用this关键字调用本类中的属性

1class Student {
 2     private String name;
 3     private int age;
 4   // 定义构造方法
 5    public Student(String name,int age) {
 6           name = name;
 7           age = age;
 8     }
 9    public String read(){
 10        return "我是:"+name+",年龄:"+age;
 11    }
 12}
 13public class Example09 {
 14     public static void main(String[] args) {
 15         Student stu = new Student("张三", 18);
 16         System.out.println(stu.read());
 17     }
 18 }

案例一

# 3.5.1 使用this关键字调用本类中的属性

由上图可知，stu对象姓名为null，年龄为0，这表明构造方法中的赋值并没有成功，这是因为构造方法参数名称与对象成员变量名称相同，编译器无法确定哪个名称是当前对象的属性。

案例一运行结果

运行代码，控制台显示的运行结果如下图所示。

# 为了解决这个问题，Java提供了关键字this指代当前对象，通过this可以访问当前对象的成员。修改案例一，使用this关键字指定当前对象属性，具体代码如下所示。

3.5.1 使用this关键字调用本类中的属性

1class Student {
 2     private String name;
 3     private int age;
 4     public Student(String name,int age) {// 定义构造方法
 5       this.name = name;
 6       this.age = age;
 7     }
 8    public String read(){
 9         return "我是:"+name+",年龄:"+age;
 10    }
 11}
 12public class Example10 {
 13     public static void main(String[] args) {
 14         Student stu = new Student("张三", 18);
 15         System.out.println(stu.read());
 16     }
 17 }

案例二

# 3.5.1 使用this关键字调用本类中的属性

案例二运行结果

运行代码，控制台显示的运行结果如下图所示。

由上图所示的运行结果分析可知，案例二成功调用构造方法完成了stu对象的初始化。这是因为在构造方法之中，使用this关键字明确标识出了类中的两个属性“this.name”和“this.age”，在进行赋值操作时不会产生歧义。

# 3.5.2 使用this关键字调用成员方法

先定一个小目标！

# 3.5.2 使用this关键字调用成员方法

通过this关键字调用成员方法，具体示例代码如下。

上述代码中，在read()方法中使用this关键字调用了openMouth()方法。需要注意的是此处的this关键字也可以省略不写。

class Student {
	public void openMouth() {
		...
	}
	public void read() {
		this.openMouth();
	}
}

# 3.5.3 使用this关键字调用构造方法

先定一个小目标！

# 构造方法是在实例化对象时被Java虚拟机自动调用，在程序中不能像调用其他成员方法一样调用构造方法，但可以在一个构造方法中使用“this(参数1,参数2…)”的形式调用其他的构造方法。
下面通过一个案例演示使用this关键字调用构造方法，具体代码如下所示。

3.5.3 使用this关键字调用构造方法

1class Student {
 2	private String name;
 3	private int age;
 4	public Student () {
 5		System.out.println("调用了无参的构造方法");
 6	}

# 3.5.3 使用this关键字调用构造方法

7	public Student (String name,int age) {
 8		this();                  // 调用无参的构造方法
 9         		this.name = name;
 10    		this.age = age;
 11	}
 12	public String read(){
 13        		return "我是:"+name+",年龄:"+age;
 14	}
 15}
 16public class Example11 { 
 17	public static void main(String[] args) {
 18	    Student stu = new Student("张三",18);    // 实例化 Student对象
 19         	    System.out.println(stu.read());
 20	}
 21}

# 3.5.3 使用this关键字调用构造方法

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 使用this调用类的构造方法时，应注意以下三点。
     （1）只能在构造方法中使用this调用其他的构造方法，不能在成员方法中
              通过this调用构造方法。
     （2）在构造方法中，使用this调用其他构造方法的语句必须位于第一行，
             且只能出现一次。下面程序的写法是错误的。

3.5.3 使用this关键字调用构造方法

public Student(String name) {
   System.out.println("有参的构造方法被调用了。");
   this(name); 						//不在第一行，编译错误！
}

# 3.5.3 使用this关键字调用构造方法

（3）不能在一个类的两个构造方法中使用this互相调用，下面程序的写法
         是错误的。

class Student {
	public Student () {
         		this("张三");  	// 调用有参构造方法
		System.out.println("无参的构造方法被调用了。");
	}
	public Student (String name) {
		this();                  	// 调用无参构造方法
		System.out.println("有参的构造方法被调用了。");
	}
}

# 代码块

3.6

# 3.6 代码块

代码块，简单来讲，就是用{}括号括起来的一段代码，根据位置及声明关键字的不同，代码块可以分为4种：普通代码块、构造块、静态代码块、同步代码块。本节将针对普通代码块和构造块进行讲解。静态代码块将在下一节的static关键字中进行讲解，同步代码块将在多线程部分进行讲解。

# 3.6.1 普通代码块

先定一个小目标！

# 3.6.1 普通代码块

普通代码块就是直接在方法或是语句中定义的代码块，具体示例如下。

public class Example12 { 
	public static void main(String[] args) {
	          {
         		int age = 18;
         		System.out.println("这是普通代码块。age:"+age);
        	          } 
         	          int age = 30;
         	          System.out.println("age:"+age);
	}
}

# 在上述代码中，每一对“{}”括起来的代码都称为一个代码块。Example12是一个大的代码块，在Example12代码块中包含了main()方法代码块，在main()方法中又定义了一个局部代码块，局部代码块对main()方法进行了“分隔”，起到了限定作用域的作用。
上述代码中的局部代码块中定义了变量age，main()方法代码块中也定义了变量age，但由于两个变量处在不同的代码块，作用域不同，因此并不相互影响。

3.6.1 普通代码块

示例代码分析：

# 3.6.2 构造块

先定一个小目标！

# 3.6.2 构造块

构造代码块是直接在类中定义的代码块。下面通过一个案例演示构造代码块的使用，具体代码如下所示。

1 class Student{
 2    String name;    		//成员属性
 3    {
 4        System.out.println("我是构造代码块");       //与构造方法同级
 5    }
 6    //构造方法
 7    public Student(){
 8        System.out.println("我是Student类的构造方法");
 9    }
 10}
 11public class Example12  {
 12    public static void main(String[] args) {
 13        Student stu1 = new Student();
 14        Student stu2 = new Student();
......

案例演示

# 3.6.2 构造块

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 由上图可以得出以下两点结论。
（1）在实例化Student类对象stu1、stu2时，构造块的执行顺序大于构造方法（这里和构造块写在前面还是后面没有关系）。
（2）每当实例化一个Student类对象，都会在执行构造方法之前执行构造块。

3.6.2 构造块

案例运行结果分析

# static关键字

3.7

# 3.7.1 静态属性

先定一个小目标！

# 3.7.1 静态属性

静态属性访问格式

如果在Java程序中使用static修饰属性，则该属性称为静态属性（也称全局属性），静态属性可以使用类名直接访问，访问格式如下。

类名.属性名

# 3.7.1 静态属性

学习静态属性之前，先来看一个案例，，具体代码如下所示。

1class Student {
 2    String name;                    		// 定义name属性
 3    int age;                         		// 定义age属性
 4    String school = "A大学";    		// 定义school属性
 5    public Student(String name,int age){
 6        this.name = name;
 7        this.age = age;
 8    }
 9    public void info(){
 10   System.out.println("姓名:" + this.name+"，年龄:" +this. age+"，学
 11                          校:" + school);  
 12  }
 13}

案例一演示

# 3.7.1 静态属性

14public class Example13 {
 15    public static void main(String[] args) {
 16        Student stu1 = new Student("张三",18);    // 创建学生对象
 17        Student stu2 = new Student("李四",19);
 18        Student stu3 = new Student("王五",20);
 19        stu1.info();
 20        stu2.info();
 21        stu3.info();
 22        //修改stu1对象的school的值
 23        stu1.school = "B大学";
 24        System.out.println("修改stu1学生对象的学生信息为B大学后");
 25        stu1.info();
 26        stu2.info();
 27        stu3.info();
 28    }
 29}

# 3.7.1 静态属性

案例一运行结果

运行代码，控制台显示的运行结果如下图所示。

# 3.7.1 静态属性

案例一运行结果分析

由上图可知，张三的学校信息由A大学修改为了B大学，而李四和王五的大学信息没有变化，表明非静态属性是对象所有，改变当前对象的属性值，不影响其他对象的属性值。

# 3.7.1 静态属性

下面，考虑一种情况：假设A大学改名成了B大学，而此时Student类已经产生了10万个学生对象，那么意味着，如果要修改这些学生对象的学校信息，则要把这10万个对象中的学校属性全部修改，共修改10万遍，这样肯定是非常麻烦的。

# 3.7.1 静态属性

为了解决上述问题，可以使用static关键字修饰school属性，将其变为公共属性。这样，school属性只会分配一块内存空间，被Student类的所有对象共享，只要某个对象进行了一次修改，全部学生对象的school属性值都会发生变化。
修改案例一，使用static关键字修饰school属性，具体代码如下所示。

# 3.7.1 静态属性

1class Student {
 2    String name;                          		// 声明name属性
 3    int age;                               		// 声明age属性
 4    static String school = "A大学";       	// 定义school属性
......
 14public class Example14 {
 15    public static void main(String[] args) {
 16        Student stu1 = new Student("张三",18);        // 创建学生对象
 17        Student stu2 = new Student("李四",19);
 18        Student stu3 = new Student("王五",20);
 19        stu1.info();
 20        stu2.info();
 21        stu3.info();
 22        stu1.school = "B大学";
 23        stu1.info();
 24        stu2.info();
 25        stu3.info();
......

案例二演示

修改案例一，使用static关键字修饰school属性，具体代码如下所示。

# 3.7.1 静态属性

案例二运行结果

运行代码，控制台显示的运行结果如下图所示。

# 3.7.1 静态属性

案例二的内存分配，如下所示。

school属性修改前

案例二的内存分配图

(b)school属性修改后

# 3.7.1 静态属性

static关键字只能修饰成员变量，不能修饰局部变量，否则编译器会报错。例如，下面的代码是非法的。

public class Student {
         public void study() {
              // 这行代码是非法的，编译器会报错
             static int num = 10;	
         }
}

小提示：static不能修饰局部变量

# 3.7.2 静态方法

先定一个小目标！

# 3.7.2 静态方法

静态方法访问格式

如果想要使用类中的成员方法，就需要先将这个类实例化。而在实际开发时，开发人员有时希望在不创建对象的情况下，通过类名就可以直接调用某个方法，这时就需要使用静态方法，要实现静态方法只需要在成员方法前加上static关键字。
同静态变量一样，静态方法也可以通过类名和对象访问，具体如下所示。

类名.方法

或

实例对象名.方法

# 3.7.2 静态方法

下面通过一个案例学习静态方法的使用，具体代码如下所示。

class Student {
    private String name;                        // 声明name属性
    private int age;                            // 声明age属性
    private static String school = "A大学";   // 定义school属性
	     ...
public static String getSchool() {                 
           return school;
}
 public static void setSchool(String s) {
    school = s;
}

案例演示

# 3.7.2 静态方法

...
class Example15 {
    public static void main(String[] args) {
        Student stu1 = new Student("张三",18);      // 创建学生对象stu1
        Student stu2 = new Student("李四",19);      // 创建学生对象stu2
        Student stu3 = new Student("王五",20);      // 创建学生对象stu3
        System.out.println("----修改前----");
        stu1.info();
	    ...
        System.out.println("----修改后----");
	    Student.setSchool("B大学");              //为静态属性school重新赋值
        stu1.info();
	    ...

案例演示

# 3.7.2 静态方法

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

注意：静态方法只能访问静态成员，因为非静态成员需要先创建对象才能访问，即随着对象的创建，非静态成员才会分配内存。而静态方法在被调用时可以不创建任何对象。

# 3.7.3 静态代码块

先定一个小目标！

# 3.7.3 静态代码块

在Java类中，用static关键字修饰的代码块称为静态代码块。当类被加载时，静态代码块就会执行，由于类只加载一次，所以静态代码块只执行一次。在程序中，通常使用静态代码块对类的成员变量进行初始化。

静态代码块

# 3.7.3 静态代码块

下面通过一个案例学习静态代码块的使用，具体代码如下所示。

1class Student{
 2    String name;    		//成员属性
 3    {
 4        System.out.println("我是构造代码块");
 5    }
 6    static {
 7        System.out.println("我是静态代码块");
 8    }
 9    public Student(){      		//构造方法
 10   System.out.println("我是Student类的构造方法");
 11}
 12}
 13class Example16{
 14    public static void main(String[] args) {
 15        Student stu1 = new Student();
 16        Student stu2 = new Student();
 17        Student stu3 = new Student();
......

案例演示

# 3.7.3 静态代码块

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 本章小结

本章详细介绍了面向对象的基础知识。首先介绍了面向对象的思想；其次介绍了类与对象之间的关系，包括类的定义、对象的创建与使用、对象的引用传递和访问控制；接着介绍了类的封装，包括为什么要封装以及如何实现封装；接着介绍了构造方法，包括构造方法的定义与重载；然后介绍了this关键字的使用，包括使用this关键字调用本类中的属性、成员变量和构造方法；最后介绍了代码块的使用以及static关键字的使用。通过本章的学习，读者已经对Java中面向对象的思想有了初步的认识，熟练掌握好这些知识，有助于学习下一章的内容。深入理解面向对象的思想，对以后的实际开发也是大有裨益的。

本

章

小

结
# 第4章  面向对象(下)

Java基础入门（第3版）

# 学习目标/Target

# 学习目标/Target

# 章节概述/ Summary

在上一章中，介绍了面向对象的基本用法，并对面向对象的三大特征之一的封装特性进行了详细地讲解。本章将继续讲解面向对象中与继承和多态相关的知识。

# 目录/Contents

# 目录/Contents

# 继承

4.1

# 4.1.1 继承的概念

先定一个小目标！

# 4.1.1 继承的概念

现实生活中，说到继承，通常会想到子女继承父辈的财产、事业等。在程序中，继承描述的是事物之间的所属关系，通过继承可以使多种事物之间形成一种关系体系。例如，猫和狗都属于动物，程序中便可以描述为猫和狗继承自动物，同理，波斯猫和巴厘猫继承猫科，而沙皮狗和斑点狗继承自犬科。

# 4.1.1 继承的概念

上述动物继承关系如下图所示。

继承关系图谱

# 4.1.1 继承的概念

在Java中，类的继承是指在一个现有类的基础上构建一个新的类，构建出来的新类被称作子类，现有类被称作父类。子类会自动继承父类的属性和方法，使得子类具有父类的特征和行为。

Java中类的继承

# 4.1.1 继承的概念

在Java程序中，如果想声明一个类继承另一个类，需要使用extends关键字，其语法格式如下所示。

class 父类{
  ……
 }
class 子类 extends 父类{
  …… 
}

类的继承语法格式

# 4.1.1 继承的概念

下面通过一个案例学习子类是如何继承父类的，具体代码如下所示。

1// 定义Animal类
 2class Animal {
 3    private String name;         		// 声明name属性
 4    private int age;             		// 声明age属性
 ......//省略getter/setter方法
 18}
 19// 定义Dog类继承Animal类
 20class Dog extends Animal {
 21    //此处不写任何代码
 22}

案例一演示

# 4.1.1 继承的概念

23// 定义测试类
 24 public class Example01 {
 25    public static void main(String[] args) {
 26       Dog dog = new Dog();    // 创建一个Dog类的对象
 27       dog.setName("牧羊犬");   // 此时调用的是父类Animal中的setter方法
 28       dog.setAge(3);           // 此时调用的是父类Animal中的setter方法
 29       System.out.println("名称："+dog.getName()+",年龄："+dog.getAge()
 30                              +",颜色："+dog.COLOR);
 31    }
 32}

# 4.1.1 继承的概念

案例一运行结果

运行代码，控制台显示的运行结果如下图所示。

# 子类除了可以继承父类的属性和方法，也可以定义自己的属性和方法。修改案例一，在子类Dog中增加属性color和相应的getter和setter方法，具体代码如下所示。

4.1.1 继承的概念

1// 定义Animal类
 2class Animal {
 	......//省略案例一中Animal类的书写
 17}
 18// 定义Dog类继承Animal类
 19class Dog extends Animal {
 20    private String color;        // 声明color属性
 21    public String getColor() {
 22       return color;
 23    }
 24    public void setColor(String color) {
 25       this.color = color;
 26    }
 27}

案例二演示

# 4.1.1 继承的概念

28// 定义测试类
 29 public class Example02 {
 30    public static void main(String[] args) {
 31      Dog dog = new Dog();     // 创建并实例化dog对象
 32      dog.setName("牧羊犬");    // 此时访问的是父类Animal中的setter方法
 33      dog.setAge(3);            // 此时访问的是父类Animal中的setter方法
 34      dog.setColor("黑色");    // 此时访问的是Dog类中的setter方法
 35      System.out.println("名称："+dog.getName()+",年龄："+dog.getAge()+",
 36      颜色："+dog.getColor());
 37   }
 38}

# 4.1.1 继承的概念

案例二运行结果

运行代码，控制台显示的运行结果如下图所示。

注意：子类虽然可以通过继承访问父类的成员和方法，但不是所有的父类属性和方法都可以被子类访问。子类只能访问父类中public和protected修饰的属性和方法，父类中被private修饰的属性和方法不能被子类访问，如果父类和子类不在同一个包中，那么被默认修饰符default修饰的属性和方法也不能被子类访问。

# 4.1.1 继承的概念

类的继承注意事项

（1）在Java中，类只支持单继承，不允许多继承。也就是说一个类只能有一个直接父类。例如下面这种情况是不合法的。

class A{}
class B{}
class C extends A,B{}  // C类不可以同时继承A类和B类

# 4.1.1 继承的概念

类的继承注意事项

（2）多个类可以继承一个父类，例如下面这种情况是允许的。

class A{}
class B extends A{}   //类B继承类A
class C extends A{}   //类C继承类A

# 4.1.1 继承的概念

类的继承注意事项

（3）在Java中，多层继承也是可以的，即一个类的父类可以再继承另外的父类。例如，C类继承自B类，而B类又可以继承自类A，这时，C类也可称作A类的子类。例如下面这种情况是允许的。

class A{}
class B extends A{}   // 类B继承类A，类B是类A的子类
class C extends B{}   // 类C继承类B，类C是类B的子类，同时也是类A的子类

# 4.1.1 继承的概念

类的继承注意事项

（4）在Java中，子类和父类是一种相对概念，一个类可以是某个类的父类，也可以是另一个类的子类。例如，在第（3）种情况中，B类是A类的子类，同时又是C类的父类。

# 4.1.2 方法的重写

先定一个小目标！

# 4.1.2 方法的重写

在继承关系中，子类会自动继承父类中定义的方法，但有时在子类中需要对继承的方法进行一些修改，即对父类的方法进行重写。在子类中重写的方法需要和父类被重写的方法具有相同的方法名、参数列表以及返回值类型。

# 下面通过一个案例讲解方法的重写，具体代码如下所示。

4.1.2 方法的重写

1// 定义Animal类
 2class Animal {		
 3    //定义动物叫的方法		
 4	void shout() {			  
 5		System.out.println("动物发出叫声");
 6	}
 7}
 8// 定义Dog类继承Animal类
 9class Dog extends Animal {    
 10	//重写父类Animal中的shout()方法
 11	void shout() {			 
 12		System.out.println("汪汪汪……");  
 13	}
 14}

案例一演示

# 4.1.2 方法的重写

15// 定义测试类
 16public class Example03 {	
 17	public static void main(String[] args) {
 18		Dog dog = new Dog(); // 创建Dog类的实例对象
 19		dog.shout();      // 调用Dog类重写的shout()方法
 20	}
 21}

# 4.1.2 方法的重写

案例一运行结果

运行代码，控制台显示的运行结果如下图所示。

# 脚下留心

子类重写父类方法时的访问权限

子类重写父类方法时，不能使用比父类中被重写的方法更严格的访问权限。例如，父类中的方法是public权限，子类的方法就不能是private权限。如果子类在重写父类方法时定义的权限缩小，则在编译时将出现错误。

# 脚下留心

子类重写父类方法时的访问权限

1// 定义Animal类
 2class Animal {		
 3    //定义动物叫的方法		
 4   public void shout() {			  
 5		System.out.println("动物发出叫声");
 6	}
 7}
 8// 定义Dog类继承Animal类
 9class Dog extends Animal {    
 10	//重写父类Animal中的shout()方法
 11	private void shout() {			 
 12		System.out.println("汪汪汪……");  
 13	}
 14}

下面我们对案例一进行修改，修改后的代码如下所示。

案例二演示

# 脚下留心

子类重写父类方法时的访问权限

15// 定义测试类
 16public class Example04 {	
 17	public static void main(String[] args) {
 18		Dog dog = new Dog(); // 创建Dog类的实例对象
 19		dog.shout();           // 调用Dog类重写的shout()方法
 20	}
 21}

# 脚下留心

子类重写父类方法时的访问权限

案例二运行结果

运行代码，控制台显示的运行结果如下图所示。

# 脚下留心

子类重写父类方法时的访问权限

案例二运行结果分析

从上图可以看出，编译文件报错“com.itheima.Dog中的shout()无法覆盖com.itheima.Anima的shout()”，这是因为子类重写父类方法时，不能使用比父类中被重写的方法更严格的访问权限。

# 4.1.3 super关键字

先定一个小目标！

# 4.1.3 super关键字

当子类重写父类的方法后，子类对象将无法访问父类中被子类重写过的方法。为了解决这个问题，Java提供了super关键字，使用super关键字可以在子类中访问父类的非私有方法、非私有属性以及构造方法。下面详细讲解super关键字的具体用法。

# 4.1.3 super关键字

super关键字的用法一

（1）使用super关键字访问或调用父类的非私属性或非私有方法，具体格式如下。

super.属性
super.方法(参数1,参数2…)

# 4.1.3 super关键字

......//省略定义Animal类
 9  // 定义Dog类继承Animal类
 10class Dog extends Animal {    
 11     // 重写父类Animal中的shout()方法,扩大了访问权限
 12	public void shout() {			 
 13         		super.shout();      // 调用父类中的shout()方法
 14		System.out.println("汪汪汪……");  
 15	}
 16     public void printName(){
 17         System.out.println("名字:"+super.name);      // 访问父类中的name属性
 18     }
 19}

下面通过一个案例学习使用super关键字访问父类的成员变量和成员方法，修改4.1.2中的案例二，具体代码如下所示。

案例一演示

# 4.1.3 super关键字

20// 定义测试类
 21public class Example05 {	
 22	public static void main(String[] args) {
 23		Dog dog = new Dog();    // 创建Dog类的对象
 24		dog.shout();                      // 调用Dog类重写的shout()方法
 25                               dog.printName();                // 调用Dog类中的printName()方法
 26	}
 27}

# 4.1.3 super关键字

案例一运行结果

运行代码，控制台显示的运行结果如下图所示。

由上图可知，控制台打印了“动物发出叫声”“名字：牧羊犬”，说明子类通过super关键字成功地访问了父类的成员变量和成员方法。

# 4.1.3 super关键字

super关键字的用法二

（2）使用super关键字调用父类中指定的构造方法，具体格式如下。

super(参数1,参数2…)

# 4.1.3 super关键字

1// 定义Animal类
 2class Animal {
 3    private String name;
 4    private int age;
 5    public Animal(String name, int age) {	// Animal类有参构造方法
 6        this.name = name;
 7        this.age = age;
 8    }
                    ......
 21    public String info() {
 22        return "名称："+this.getName()+",年龄："+this.getAge();
 23    }
 24}
 25  // 定义Dog类继承Animal类

下面通过一个案例学习如何使用super关键字调用父类的构造方法，具体代码如下所示。

案例二演示

# 4.1.3 super关键字

26class Dog extends Animal {
 27    private String color;
 28    public Dog(String name, int age, String color) {
 29        super(name, age);    //通过super关键字调用Animal类有两个参数的构造方法
 30        this.setColor(color);
 31    }
 ......//省略属性color的getter/setter方法
 38    // 重写父类的info()方法
 39    public String info() {
 40        return super.info()+",颜色："+this.getColor();  // 扩充父类中的方法
 41    }
 42}
 43// 定义测试类
 44public class Example06 {
 45    public static void main(String[] args) {
 46        Dog dog = new Dog("牧羊犬",3,"黑色");             // 创建Dog类的对象
 47        System.out.println(dog.info());
 48    }
 49}

# 4.1.3 super关键字

案例二运行结果

运行代码，控制台显示的运行结果如下图所示。

# 4.1.3 super关键字

案例二结果分析

由上图可知，控制台打印了“名称：牧羊犬，年龄：3，颜色：黑色”，说明子类Dog使用super()成功调用了父类中有两个参数的构造方法，并传递了参数name和参数age的值，其中，参数name的值为牧羊犬，参数age的值为3。
注意：通过super()调用父类构造方法的代码必须位于子类构造方法的第一行，并且只能出现一次。

# 4.1.3 super关键字

super与this关键字的作用非常相似，都可以调用构造方法、方法和属性，但是两者之间还是有区别的，super与this的区别如下表所示。

super与this的区别

注意：this和super不可以同时出现，因为使用this和super调用构造方法的代码都要求必须放在构造方法的首行。

| 区别点 | super | this |
|---|---|---|
| 访问属性 | 直接访问父类中的非私有属性 | 访问本类中的属性。如果本类中没有该属性,则从父 类中继续查找 |
| 调用方法 | 直接调用父类中的非私有方法 | 调用本类中的方法。如果本类中没有该方法,则从父 类中继续查找 |
| 调用构造方法 | 调用 父 类 构 造 方 法,必 须 放 在 子类构造方法的首行 | 调用本类构造方法,必须放在构造方法的首行 |

# final关键字

4.2

# 4.2.1 final关键字修饰类

先定一个小目标！

# 4.2.1 final关键字修饰类

1	// 使用final关键字修饰Animal类
 2	final class Animal {
 3	}
 4	// Dog类继承Animal类
 5	class Dog extends Animal {
 6	}
 7	// 定义测试类
 8	public class Example07 {
 9		public static void main(String[] args) {
 10			Dog dog = new Dog(); // 创建Dog类的对象
 11		}
 12	}

Java中使用final关键字修饰的类不可以被继承，也就是不能派生子类。下面通过一个案例进行验证，具体代码如下所示。

案例演示

# 4.2.1 final关键字修饰类

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 4.2.1 final关键字修饰类

案例运行结果分析

从上图可以看出，编译器报“无法从最终cn.itcast.Animal进行继承”错误，说明Dog类不能继承使用final修饰的Animal类。由此可见，被final关键字修饰的类不能被其他类继承。

# 4.2.2 final关键字修饰方法

先定一个小目标！

# 4.2.2 final关键字修饰方法

1	// 定义Animal类
 2	class Animal {
 3	     // 使用final关键字修饰shout()方法
 4		public final void shout() {}
 5	}
 6	// 定义Dog类继承Animal类
 7	class Dog extends Animal {
 8	     // 重写Animal类的shout()方法
 9		public void shout() {}
 10	}
 11	// 定义测试类 
 12	public class Example08 {
 13		public static void main(String[] args) {
 14			Dog dog=new Dog(); // 创建Dog类的对象
 15		}
 16	}

当一个类的方法被final关键字修饰后，该类的子类将不能重写该方法。下面通过一个案例进行验证，具体代码如下所示。

案例演示

# 4.2.2 final关键字修饰方法

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 4.2.2 final关键字修饰方法

案例运行结果分析

从上图可以看出，使用final关键字修饰父类Animal中的shout()方法，在子类Dog类中重写shout()方法时，编译报“com.itheima.Dog中的shout()无法覆盖com.itheima.Animal中的shout()被覆盖的方法为final”错误。这是因为Animal类的shout()方法被final关键字修饰，而子类不能对final关键字修饰的方法进行重写。

# 4.2.3 final关键字修饰变量

先定一个小目标！

# 4.2.3 final关键字修饰变量

1public class Example09 {
 2	public static void main(String[] args) {
 3	   final int AGE = 18;   // 使用final关键字修饰的变量AGE第一次可以被赋值
 4	   AGE = 20;                // 再次被赋值会报错
 5	}
 6}

Java中被final修饰的变量为常量，常量只能在声明时被赋值一次，在后面的程序中，常量的值不能被改变。如果再次对final修饰的常量赋值，则程序会在编译时报错。下面通过一个案例进行验证，具体代码如下所示。

案例演示

# 4.2.3 final关键字修饰变量

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 4.2.3 final关键字修饰变量

案例运行结果分析

从上图可以看出，程序编译时报错“无法为最终变量AGE分配值”，这是因为使用final定义的常量本身不可被修改。
注意：在使用final声明变量时，变量的名称要求全部的字母大写。如果一个程序中的变量使用public static final声明，则此变量将成为全局常量，如下面代码所示。
      public static final String NAME = "哈士奇";

# 4.2.3 final关键字修饰变量

由上图可知，程序编译时报错“无法为最终变量AGE分配值”，这是因为使用final定义的常量本身不可被修改。
需要注意的是，在使用final声明变量时，变量的名称要求全部的字母大写。如果一个程序中的变量使用public static final声明，则此变量将成为全局常量，如下面代码所示。

public static final String NAME = "哈士奇";

# 抽象类和接口

4.3

# 4.3.1 抽象类

先定一个小目标！

# 4.3.1 抽象类

定义一个类时，常常需要定义一些成员方法用于描述类的行为特征，但有时这些方法的实现方式是无法确定的。例如，前面定义的Animal类中的shout()方法用于描述动物的叫声，但是不同的动物，叫声也不相同，因此在shout()方法中无法准确描述动物的叫声。
针对上面描述的情况，Java提供了抽象方法来满足这种需求。抽象方法是使用abstract关键字修饰的成员方法，抽象方法在定义时不需要实现方法体。抽象方法的语法格式如下。

abstract 返回值类型 方法名称(参数列表);

抽象方法的语法格式

# 4.3.1 抽象类

abstract class 抽象类名称{
    属性;
    访问权限 返回值类型 方法名称(参数){                    //普通方法
        return [返回值];
    }
    访问权限 abstract 返回值类型 抽象方法名称(参数);//抽象方法，无方法体
}

当一个类包含了抽象方法，该类就是抽象类。抽象类和抽象方法一样，必须使用abstract关键字进行修饰。抽象类的语法格式如下。

抽象类的语法格式

# 4.3.1 抽象类

从上面抽象类的语法格式中可以发现，抽象类的定义比普通类多了一个或多个抽象方法，其他地方与普通类的组成基本相同。抽象类的定义规则如下。
（1）包含抽象方法的类必须是抽象类。
（2）声明抽象类和抽象方法时都要使用abstract关键字修饰。
（3）抽象方法只需声明而不需要实现。
（4）如果非抽象类继承了抽象类，那么该类必须实现抽象类中的全部抽象方法。

抽象类的定义规则

# 4.3.1 抽象类

1// 定义抽象类Animal
 2abstract class Animal { 
 3     // 定义抽象方法shout()
 4	abstract void shout(); 
 5}
 6// 定义Dog类继承抽象类Animal
 7class Dog extends Animal {
 8     // 重写抽象方法shout()
 9	void shout() {
 10		System.out.println("汪汪...");
 11	}
 12}

下面通过一个案例学习抽象类的使用，具体代码如下所示。

案例演示

# 4.3.1 抽象类

13// 定义测试类
 14public class Example10 {
 15	public static void main(String[] args) {
 16		Dog dog = new Dog(); // 创建Dog类的对象
 17		dog.shout();          // 通过dog对象调用shout()方法
 18	}
 19}

# 4.3.1 抽象类

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 4.3.1 抽象类

案例运行结果分析

从上图可以看出，控制台打印了“汪汪...”，说明dog对象调用了Dog类中实现的父类Animal的抽象方法shout()。
注意：使用abstract关键字修饰的抽象方法不能使用private关键字修饰，因为抽象方法必须要被子类实现，如果使用了private关键字修饰抽象方法，则子类无法实现该方法。

# 4.3.2 接口

先定一个小目标！

# 接口是一种用来定义程序的协议，它用于描述类或结构的一组相关行为。接口是由抽象类衍生出来的一个概念，并由此产生了一种编程方式，可以称这种编程方式为面向接口编程。面向接口编程就是将程序的业务逻辑进行分离，以接口的形式去对接不同的业务模块。接口中不实现任何业务逻辑，业务逻辑由接口的实现类来完成。当业务需求变更时，只需要修改实现类中的业务逻辑，而不需要修改接口中的内容，以减少需求变更对系统产生的影响。

4.3.2 接口

# 4.3.2 接口

下面通过现实生活中的的例子来类比面向接口编程。例如，鼠标、U盘等外部设备通过USB插口来连接计算机，即插即用，非常灵活。如果需要更换与计算机进行连接的外部设备，只需要拔掉当前USB插口上的设备，把新的设备插入即可，这就是面向接口编程的思想。

# 4.3.2 接口

在Java中，使用接口的目的是为了克服单继承的限制，因为一个类只能有一个父类，而一个类可以同时实现多个父接口。在JDK 8之前，接口是由全局常量和抽象方法组成的。JDK 8对接口进行了重新定义，接口中除了抽象方法外，还可以定义默认方法和静态方法，默认方法使用default关键字修饰，静态方法使用static关键字修饰，且这两种方法都允许有方法体。

# 4.3.2 接口

接口使用interface关键字声明，语法格式如下。

接口的语法格式

[public] interface 接口名 [extends 接口1,接口2...] {
	[public] [static] [final] 数据类型 常量名 = 常量;
	[public] [abstract] 返回值的数据类型 方法名(参数列表);
	[public] static 返回值的数据类型 方法名(参数列表){}
	[public] default 返回值的数据类型 方法名(参数列表){}
}

# 4.3.2 接口

在很多的Java程序中，经常看到编写接口中的方法时省略了public ，有很多读者认为它的访问权限是default，这实际上是错误的。不管写不写访问权限，接口中方法的访问权限永远是public。

接口定义注意

# 4.3.2 接口

接口本身不能直接实例化，接口中的抽象方法和默认方法只能通过接口实现类的实例对象进行调用。实现类通过implements关键字实现接口，并且实现类必须重写接口中所有的抽象方法。需要注意的是，一个类可以同时实现多个接口，实现多个接口时，多个接口名需要使用英文逗号（,）分隔。

# 4.3.2 接口

定义接口的实现类，语法格式如下。

接口实现类的语法格式

修饰符 class 类名 implements 接口1,接口2,...{
    ...
}

# 4.3.2 接口

第一、定义一个Animal接口，在Animal接口中定义了全局常量ID和全局常量NAME、抽象方法shout()、info()和静态方法getID()。
第二、定义一个Action接口，在Action接口中定义了一个抽象方法eat()，用于输出信息“喜欢吃骨头”。

案例一演示

下面通过一个案例学习接口的使用，由于代码过长此处不进行展示，仅适用文字说明代码逻辑，请参考教材4.3.2节中的文件4-11。

# 4.3.2 接口

第三、定义一个Dog类，Dog类通过implements关键字实现了Animal接口和Action接口，并重写了这两个接口中的抽象方法。
第四、使用Animal接口名直接访问了Animal接口中的静态方法getID()，输出编号信息。
第五、创建Dog类的对象dog，并通过dog对象调用了本类实现的Animal接口和Action接口中的info()方法、shout()方法，以及本类新增的eat()方法。

# 4.3.2 接口

案例一运行结果

运行代码，控制台显示的运行结果如下图所示。

注意：接口的实现类，必须实现接口中的所有抽象方法，否则程序编译报错。

# 4.3.2 接口

上述案例一演示的是类与接口之间的实现关系，如果在开发中一个子类既要实现接口又要继承抽象类，则可以按照以下语法格式定义子类。

修饰符class 类名 extends 父类名 implements 接口1,接口2,... {
    ...
}

# 4.3.2 接口

第一、定义一个Animal接口，Animal接口中声明了全局常量NAME（名称）、抽象方法shout()和抽象方法info()。
第二、定义一个抽象类Action，抽象类Action中定义了一个抽象方法eat()。
第三、定义一个Dog类，Dog类通过extends关键字继承了Action抽象类，同时通过implements实现了Animal接口。Dog类重写了Animal接口和Action抽象类中的所有抽象方法，包括shout()方法、info()方法和eat()方法。
第四、创建一个Dog类对象dog，通过对象dog分别调用info()、shout()和eat()方法。

案例二演示

下面演示一个类既可以实现接口又可以继承抽象类的情况，由于代码过长此处不进行展示，仅适用文字说明代码逻辑，请参考教材4.3.2节中的文件4-12。

# 4.3.2 接口

案例二运行结果

运行代码，控制台显示的运行结果如下图所示。

# 4.3.2 接口

在Java中，接口是不允许继承抽象类的，但是允许接口继承接口，并且一个接口可以同时继承多个接口。下面通过一个案例讲解接口的继承，由于代码过长此处不进行展示，仅适用文字说明代码逻辑，请参考教材4.3.2节中的文件4-13。

案例三演示

第一、定义一个Animal接口，Animal接口中声明了全局常量NAME（名称）、抽象方法info()。
第二、定义一个Color接口，Color接口中定义了一个抽象方法black()。
第三、定义一个接口Action并继承接口Animal和接口Color，这样接口Action中就同时拥有Animal接口中的info()方法、NAME属性和Color接口中的black()方法以及本类中的shout()方法。

# 4.3.2 接口

第四、定义一个Dog类并实现了Action接口，这样Dog类就必须同时重写Animal接口、中的抽象方法info()、Color接口中的抽象方法black()和Action接口中的抽象方法shout()。
第五、创建一个Dog类的对象dog，通过对象dog调用Dog类中定义的shout()方法以及Dog类中实现自Action接口的info()方法和eat()方法。

# 4.3.2 接口

案例三运行结果

运行代码，控制台显示的运行结果如下图所示。

# 多态

4.4

# 4.4.1 多态概述

先定一个小目标！

# 4.4.1 多态概述

多态概述

多态是面向对象思想中的一个非常重要的概念，在Java中，多态是指不同类的对象在调用同一个方法时表现出的多种不同行为。例如，要实现一个动物叫声的方法，由于每种动物的叫声是不同的，因此可以在方法中接收一个动物类型的参数，当传入猫类对象时就发出猫类的叫声，传入犬类对象时就发出犬类的叫声。在同一个方法中，这种由于参数类型不同而导致执行效果不同的现象就是多态。

# 4.4.1 多态概述

Java中多态主要有以下两种形式。
（1）方法的重载。
（2）对象的多态（方法的重写）。

多态的两种形式

# 4.4.1 多态概述

1// 定义抽象类Animal
 2abstract class Animal {  
 3  abstract void shout();     	// 定义抽象shout()方法
 4}
 5// 定义Cat类继承Animal抽象类
 6class Cat extends Animal {
 7 	// 实现shout()方法
 8	public void shout() {
 9		System.out.println("喵喵……");
 10	}
 11}
 12// 定义Dog类继承Animal抽象类
 13class Dog extends Animal {
 14     // 实现shout()方法
 15	public void shout() {
 16		System.out.println("汪汪……");

案例演示

下面以对象的多态为例，通过一个案例演示Java程序中的多态，
具体代码下所示。

# 4.4.1 多态概述

17	}
 18} 
 19// 定义测试类
 20public class Example14 {
 21	public static void main(String[] args) {
 22	      Animal an1 = new Cat(); // 创建Cat对象,使用Animal类型的变量an1引用
 23	      Animal an2 = new Dog(); // 创建Dog对象,使用Animal类型的变量an2引用
 24	      an1.shout();        
 25	      an2.shout();        
 26	}
 27}

# 4.4.1 多态概述

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 4.4.2 对象类型的转换

先定一个小目标！

# 对象向上转型，父类对象可以调用子类重写父类的方法，这样当需要新添功能时，只需要新增一个子类，在子类中对父类的功能进行扩展，而不用更改父类的代码，保证了程序的安全性。对于向上转型，程序会自动完成，对象向上转型格式如下所示。

4.4.2 对象类型的转换

1.对象向上转型

对象向上转型：父类类型 父类对象 = 子类实例;

# 4.4.2 对象类型的转换

1// 定义Anmal类
 2class Animal {
 3   public void shout(){
 4       System.out.println("喵喵……"); 
 5  }     
 6}
 7// 定义Dog类
 8class Dog extends Animal {
 9   // 重写shout()方法
 10   public void shout() {
 11       System.out.println("汪汪……"); 
 12  }
 13   public void eat() {
 14       System.out.println("吃骨头……"); 
 15  }
 16}

案例一演示

下面通过一个案例介绍如何进行对象的向上转型操作，具体代码下所示。

# 4.4.2 对象类型的转换

17// 定义测试类
 18public class Example15 {
 19   public static void main(String[] args) {
 20       Dog dog = new Dog();  // 创建Dog对象
 21       Animal an = dog;   // 向上转型
 22       an.shout();
 23   }
 24}

# 4.4.2 对象类型的转换

案例一运行结果

运行代码，控制台显示的运行结果如下图所示。

注意：父类Animal的对象an是无法调用Dog类中的eat()方法的，因为eat()方法只在子类中定义，而没有在父类中定义。

# 除了向上转型，对象还可以向下转型。向下转型一般是为了重新获得因为向上转型而丢失的子类特性。对象在进行的向下转型前，必须先进行向上转型，否则将出现对象转换异常。   	
向下转型时，必须指明要转型的子类类型。对象向下转型格式如下所示。

4.4.2 对象类型的转换

2.对象向下转型

对象向下转型：
父类类型 父类对象 = 子类实例;
子类类型 子类对象 = （子类）父类对象;

# 4.4.2 对象类型的转换

......//省略定义Animal类和定义Dog类，可参考案例一
 17// 定义测试类
 18public class Example16 {
 19   public static void main(String[] args) {
 20       Animal an = new Dog();  // 此时发生了向上转型，子类→父类
 21       Dog dog = (Dog)an;       // 此时发生了向下转型
 22       dog.shout();
 23       dog.eat();
 24   }
 25}

案例二演示

下面通过一个案例介绍对象进行向下转型，具体代码下所示。

# 4.4.2 对象类型的转换

案例二运行结果

运行代码，控制台显示的运行结果如下图所示。

# 4.4.2 对象类型的转换

注意：在向下转型时，不能直接将父类实例强制转换为子类实例，否则程序会报错。
例如，将案例二中的第20~21行代码修改为下面一行代码，则程序报错。

Dog dog = (Dog)new Animal();//编译错误

# 4.4.3 instanceof关键字

先定一个小目标！

# 上述语法格式中，如果“对象”是指定的类的实例对象，则返回true，否则返回false。

4.4.3 instanceof关键字

Java中可以使用instanceof关键字判断一个对象是否是某个类（或接口）的实例，语法格式如下所示。

instanceof关键字的语法格式

对象  instanceof  类（或接口）

# 4.4.3 instanceof关键字

1// 定义Animal类
 2class Animal {
 3   public void shout(){ 
 4    System.out.println("动物叫……"); 
 5  }    
 6}
 ......//省略定义Dog类，可参考4.4.3节中的案例一
 17// 定义测试类
 18public class Example17 {
 19   public static void main(String[] args) {
 20	Animal a1 = new Dog();         // 通过向上转型实例化Animal对象
 21	System.out.println("Animal a1 = new Dog()："+(a1 instanceof Animal));
 22	System.out.println("Animal a1 = new Dog()："+(a1 instanceof Dog));
 23	Animal a2 = new Animal();     // 实例化Animal对象
 24	System.out.println("Animal a2 = new Animal()："+(a2 instanceof Animal));
 25	System.out.println("Animal a2 = new Animal()："+(a2 instanceof Dog));
 26   }
 27}

案例演示

下面通过一个案例演示instanceof关键字的用法，具体代码下所示。

# 4.4.3 instanceof关键字

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# Object类

4.5

# 先定一个小目标！

4.5 Object类

# 4.5 Object类

Object类

Java提供了一个Object类，它是所有类的父类，每个类都直接或间接继承了Object类，因此Object类通常被称为超类。当定义一个类时，如果没有使用extends关键字为这个类显式地指定父类，那么该类会默认继承Object类。

# 4.5 Object类

Object类中常用方法

Object类中定义了一些常用方法，具体如下所示。

| 方法名称 | 方法说明 |
|---|---|
| boolean equals() | 判断两个对象是否“相等” |
| int hashCode() | 返回对象的哈希值 |
| String toString() | 返回对象的字符串表示形式 |

# 4.5 Object类

1// 定义Animal类
 2class Animal {  
 3     // 定义动物叫的方法 
 4	void shout() {	
 5		System.out.println("动物叫！");
 6	}
 7}
 8// 定义测试类
 9public class Example18 {
 10	public static void main(String[] args)  {
 11		Animal animal = new Animal();  	    // 创建Animal类对象
 12		System.out.println(animal.toString());	//  调用toString()方法并打印
 13	}
 14}

下面通过一个案例演示Object类中toString()方法的使用，具体代码下所示。

案例一演示

# 4.5 Object类

案例一运行结果

运行代码，控制台显示的运行结果如下图所示。

# 4.5 Object类

在实际开发中，通常情况下不会直接调用Object类中的方法，因为Object类中的方法并不能适用于所有的子类，这时就需要对Object类中的方法进行重写，以符合实际开发需求。下面通过重写Object类的toString()方法进行演示。修改案例一，在Animal类中重写toString()方法，具体代码下所示。

案例二演示

1// 定义Animal类
 2class Animal {
 3   //重写Object类的toString()方法
 4   public String toString(){
 5	return "这是一个动物。";
 6   }
 7}
......//省略测试类，参考案例一

# 4.5 Object类

案例二运行结果

运行代码，控制台显示的运行结果如下图所示。

# 内部类

4.6

# 4.6.1 成员内部类

先定一个小目标！

# 4.6.1 成员内部类

在一个类中除了可以定义成员变量、成员方法，还可以定义类，这样的类被称作成员内部类。成员内部类可以访问外部类的所有成员，无论外部类的成员是何种访问权限。如果想通过外部类访问内部类，则需要通过外部类创建内部类对象，创建内部类对象的具体语法格式如下：

外部类名 外部类对象 = new 外部类名();
外部类名.内部类名 内部类对象 = 外部类对象.new 内部类名();

# 4.6.1 成员内部类

1class Outer {
 2    int m = 0; 	// 定义类的成员变量
 3   //外部类方法test1()
 4    void test1() {
 5       System.out.println("外部类成员方法test1()");
 6    }
 7    // 下面的代码定义了一个成员内部类Inner
 8    class Inner {
 9        int n = 1;
 10        void show1() {
 11           // 在成员内部类的方法中访问外部类的成员变量m
 12           System.out.println("外部成员变量m = " + m);
 13           // 在成员内部类的方法中访问外部类的成员方法test1()
 14	   test1(); 
 15       }

下面通过一个案例学习如何定义成员内部类以及如何在外部类中访问内部类，具体代码如下所示。

案例演示

# 4.6.1 成员内部类

16        void show2() {
 17           System.out.println("内部成员方法show2()");
 18       }
 19    }
 20    //外部类方法test2()
 21    void test2() {						
 22       Inner inner = new Inner();		             //实例化内部类对象inner
 23       System.out.println("内部成员变量n = " + inner.n); //访问内部类变量和方法
 24       inner.show2();
 25    }
 26}
 27public class Example20 {
 28    public static void main(String[] args) {
 29        Outer outer = new Outer();			//实例化外部类对象outer
 30        Outer.Inner inner = outer.new Inner();	//实例化内部类对象inner
 31        inner.show1();	//在内部类中访问外部类的成员变量m和成员方法test1()
 32        outer.test2();	//在内部类中访问内部类的成员变量n和成员方法show2()
 33    }
 34}

# 4.6.1 成员内部类

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 4.6.2 局部内部类

先定一个小目标！

# 4.6.2 局部内部类

局部内部类，也称为方法内部类，是指定义在某个局部范围中的类，它和局部变量都是在方法中定义的，有效范围只限于方法内部。
在局部内部类中，局部内部类可以访问外部类的所有成员变量和成员方法，而在外部类中无法直接访问局部内部类中的变量和方法。如果要在外部类中访问局部内部类的成员，只能在局部内部类的所属方法中创建局部内部类的对象，通过对象访问局部内部类的变量和方法。

# 4.6.2 局部内部类

1class Outer {
 2     int m = 0;  			// 定义类的成员变量
 3    //定义一个成员方法test1()
 4     void test1() {
 5        System.out.println("外部类成员方法test1()");
 6    }
 7    void test2() {
 8        //定义一个局部内部类，在局部内部类中访问外部类变量和方法
 9        class Inner {
 10            int n = 1;
 11            void show() {
 12                System.out.println("外部成员变量m = " + m);
 13                test1();
 14           }
 15        }

下面通过一个案例，讲解局部内部类的定义以及如何访问局部内部类，具体代码如下所示。

案例演示

# 4.6.2 局部内部类

16        //访问局部内部类中的变量和方法
 17        Inner inner = new Inner();
 18        System.out.println("局部内部类变量n = " + inner.n);
 19        inner.show();
 20  }
 21}
 22public class Example21 {
 23    public static void main(String[] args) {
 24        Outer outer = new Outer();
 25        outer.test2();   //通过外部类对象outer调用创建了局部内部类的方法test2()
 26    }
 27}

# 4.6.2 局部内部类

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 4.6.3 静态内部类

先定一个小目标！

# 4.6.3 静态内部类

静态内部类，就是使用static关键字修饰的成员内部类。与成员内部类相比，在形式上，静态内部类只是在内部类前增加了static关键字，但在功能上，静态内部类只能访问外部类的静态成员，通过外部类访问静态内部类成员时，因为程序已经提前在静态常量区分配好了内存，所以即使静态内部类没有加载，依然可以通过外部类直接创建一个静态内部类对象。创建静态内部类对象的基本语法格式如下。

外部类名.静态内部类名 变量名 = new 外部类名.静态内部类名();

# 4.6.3 静态内部类

1class Outer {
 2    static int m = 0; // 定义类的静态变量
 3    // 下面的代码定义了一个静态内部类
 4    static class Inner {
 5         int n = 1;
 6         void show() {
 7             // 在静态内部类的方法中访问外部类的静态变量m
 8             System.out.println("外部类静态变量m = " + m);
 9         }
 10     }
 11  }
 12public class Example22 {
 13    public static void main(String[] args) {
 14        Outer.Inner inner = new Outer.Inner();
 15        inner.show();
 16    }
 17}

下面通过一个案例学习静态内部类的定义和使用，具体代码如下所示。

案例演示

# 4.6.3 静态内部类

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 4.6.4 匿名内部类

先定一个小目标！

# 4.6.4 匿名内部类

在Java中调用某个方法时，如果该方法的参数是接口类型，那么在传参时，除了可以传入一个接口实现类，还可以传入实现接口的匿名内部类作为参数，在匿名内部类中实现接口方法。匿名内部类就是没有名称的内部类，定义匿名内部类时，其类体作为new语句的一部分。定义匿名内部类的基本语法格式如下所示。

new 继承的父类或实现的接口名(){
   //匿名内部类的类体
}

# 4.6.4 匿名内部类

1interface Animal{			//定义接口Animal
 2    void shout();				//定义抽象方法shout()
 3}
 4public class Example23{
 5    public static void main(String[] args){
 6        String name = "小花";
 7        animalShout(new Animal(){//调用animalShout()方法，参数为匿名内部类
 8           @Override
 9            public void shout() {
 10                System.out.println(name+"喵喵...");
 11            }
 12       });
 13   }
 14   public static void animalShout(Animal an){	//该方法参数为Animal接口类型
 15       an.shout();
 16   }
 17}

下面通过一个案例学习匿名内部类的定义和使用，具体代码如下所示。

案例演示

# 4.6.4 匿名内部类

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 4.6.4 匿名内部类

注意：在JDK 8之前，局部变量前必须加final修饰符，否则程序编译时报错。在案例中的匿名内部类中访问了局部变量name，而局部变量name并没有使用final修饰符修饰，程序也没有报错。这是因为JDK 8的新增特性，允许在局部内部类、匿名内部类中访问非final修饰的局部变量。

# 本章小结

本章在上一章的基础上对面向对象的基础知识进行了更深入地讲解。首先介绍了面向对象的继承特性，包括继承的概念、方法的重写以及super关键字；接着介绍了final关键字，包括final关键字修饰类、方法和变量；然后介绍了抽象类和接口、多态、Object类的相关知识；最后介绍了内部类，包括成员内部类、局部内部类、静态内部类、匿名内部类。通过本章和第3章知识的学习，读者已经对Java中面向对象的思想和相关语法有了比较全面的认识，面向对象是Java语言的精髓，读者应重点掌握。

本

章

小

结
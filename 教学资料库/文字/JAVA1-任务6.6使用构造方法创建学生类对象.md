# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

使用构造方法创建两个学生类对象stu1、stu2，通过调用无参构造方法创建stu1；通过有参构造方法创建stu2包含姓名、年龄、性别、爱好四个属性并输出。

# ..

模块二 知识链接

构造方法

默认构造方法

无参构造方法

有参构造方法

# 构造方法

模块二 
知识链接

在 Java 的每个类中都有一种特殊的成员方法，它的方法名和类名是一致的,创建对象时，调用这种特殊方法对成员变量进行初始化，这种方法称为构造方法。创建构造方法与创建成员方法的格式相同，但要注意以下几点:
1)构造方法的名字与其所属类的类名相同
2)构造方法是给对象赋初值，没有返回值。
3)构造方法不能被程序显式调用，而是在new构造对象时系统自动调用
4)构造方法可以有零个或多个形式参数。
5)构造方法可在类中由用户定义，若用户没有定义，系统将自动生成一个无参数的空构造方法。
6)构造方法可以通过重载实现不同的初始化方法。

# 默认构造方法

模块二 
知识链接

在Java中的每个类都至少有一个构造方法，如果在一个类中没有定义构造方法，系统会自动为这个类创建一个默认的构造方法，这个方法就叫默认构造方法。该方法没有参数，方法体中没有任何代码，但是，该构造方法会将实例变量初始化为其缺省值。成员变量如果是基本数据类型，其初始化是缺省的byte, char, short, int, long, float 和 double变量，其缺省的初始值是0，boolean变量缺省的初始值是 false。	成员变量如果是引用类型，其缺省的初始值是null。

# 默认构造方法

模块二 
知识链接

用户也可以定义自己的构造方法来根据自己的需要初始化对象。值得注意的是，在一个类中，如果已经显示地声明了一个构造方法，那么程序编译时就不会再生成默认的构造方法了，所以在定义类时，若要显示地写出有参数的构造方法，最好写上无参数的构造方法。

# 无参构造方法

模块二 
知识链接

在一个类中除了默认构造方法，也可以定义无参构造方法，如以下代码:
1public class Student{
2	public Student() {  
3		System.out.println("调用了无参构造方法");
4	}

# 有参构造方法

模块二 
知识链接

在一个类中除了可以定义无参构造方法外,还可以定义有参构造方法,通过有参构造方可以实现对属性的赋值。如以下代码：
1public class Student{
2   private String name;
3   private int age;
4   private int ;
5   private int hobby;
6   public Student(String n, int a,String s,String h) {
7       name = n;
8       age = a;
9       sex=s;
10      hobby=h;
11       System.out.println("调用了有参构造方法");
12   }

# 构造方法的重载

模块二 
知识链接

在同一类中定义了多个同名而不同内容的成员方法时，称这些方法是重载(override)的方法。重载的方法主要通过形式参数列表中参数的个数、参数的数据类型和参数的顺序的不同来区分。在编译期间，Java编译器检查每个方法所用的参数数目和类型然后调用正确的方法。构造方法可以通过重载实现不同的初始化方法。如以下代码：

# 构造方法的重载

模块二 
知识链接

1public class Student{
2   private String name;
3   private int age;
4   private int ;
5   private int hobby;
6   public Student(String n) {
7       name = n;
8       System.out.println("调用了一个参数的构造方法");
9 }
10  public Student(String n, int a) {
11      name = n;
12      age = a;
13       System.out.println("调用了两个参数的构造方法");
14 }

# ，

过渡页

模块三  任务实现

使用构造方法创建两个学生类对象stu1、stu2，通过调用无参构造方法创建stu1；通过有参构造方法创建stu2包含姓名、年龄、性别、爱好四个属性并输出。

模块三 
任务实现

# 任务源码

结合任务6-6中的描述和知识链接中构造方法相关知识点可以得到文件6-7所示的代码：
       文件6-7 Example06.Java

模块三 
任务实现

1public class Student {
2	private int age ; 
3	private String name;
4	private String sex; 
5	private String hobby;
6	public Student() {
7		System.out.println("调用了无参构造方法");
8	}

9	public Student(String n, int a,String s,String h) {
10	      name = n;
11		  age = a;
12		  sex=s;
13	      hobby=h;
14		     System.out.println("调用了有参构造方法");
15		  }

# 任务源码

结合任务6-6中的描述和知识链接中构造方法相关知识点可以得到文件6-7所示的代码：
       文件6-7 Example06.Java

模块三 
任务实现

16	public void show() {
17	    System.out.println(name+" "+age+" "
+sex+" "+hobby);
18	}
19 }

20public class Example05 {
21	public static void main(String[] args) {
22		 Student stu1=new Student();
23	     Student stu2=new Student("李红",17,"女","唱歌");
24	     stu1.show();
25		 stu2.show();
26	}
}

# 运行结果

模块三 
任务实现

文件6-7运行结果如图6-8所示：

图6-8文件6-7的运行结果

# 说明

1.以上运行结果中name、sex、hobby都是字符串类型，属于引用类型，所以其缺省的初始值是null，age是整型，其缺省的初始值是0。
2.如果去掉6-8行代码，就会出现如图6-9的提示信息。这是因为在一个类中，如果已经显示地声明了一个构造方法，那么程序编译时就不会再生成默认的构造方法了，所以在定义类时，若显示地写出有参数的构造方法，最好写上无参数的构造方法，否则无法创建无参构造方法的实例。

模块三 
任务实现

# 说明

模块三 
任务实现

public Student() { }和public Student(String n, int a,String s,String h{ }这两个方法属于构造方法的重载。

图6-9未定义无参构造方法的运行结果

# 感谢关注
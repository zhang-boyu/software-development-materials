# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

子任务1：定义一个学生类，其中包括成员变量name,静态成员变量schoolName，构造方法public Student(String name)，成员方法public void show()；定义测试类，创建两个学生类对象，为静态变量赋值，分别输出两个学生的schoolName信息。

# *

模块一  任务描述

子任务2：定义一个学生类，其中包括成员变量name,静态成员变量schoolName，构造方法public Student(String name)，静态成员方法public static String getSchool()和public static void setSchool(String s)，成员方法public void show()；定义测试类，创建两个学生类对象，修改学生的学校信息，输出修改前后两个学生的信息。

# *

模块一  任务描述

子任务3：测试静态代码块的使用：定义一个学生类，其中包括成员变量name，一个构造代码块，一个静态代码块，一个构造方法public Student()；定义测试类，创建三个学生类对象。

# ..

模块二 知识链接

static关键字

静态方法

静态方法访问格式

静态方法和实例方法的区别

静态代码块

静态变量

# static关键字

模块二 
知识链接

Java中的static关键字主要用于内存管理。用于修饰类的成员，如成员变量、成员方法以及代码块等，被static修饰的成员具备一些特殊性。比如被static关键字修饰的成员变量、方法可以被类直接访问，而不需要预先构造类的实例化对象。

# 静态变量

模块二 
知识链接

在一个Java类中，可以使用static关键字来修饰成员变量，该变量被称作静态变量。静态变量被所有实例共享，可以使用“类名.变量名”的形式来访问，也可以使用对象名.变量名”的形式来访问。
static关键字只能用于修饰成员变量，不能用于修饰局部变量，否则编译会报错。例如运行以下代码会出现“Illegal modifier for parameter score; only final is permitted”（变量score的修饰符非法，只允许使用final）的编译错误信息：

# 静态变量

模块二 
知识链接

public class Student {
   public void study() {
	static int score = 60;	// 这行代码是非法的，编译会报错
   }
    }
例如，在定义一个类时,只是在描述某类事物的特征和行为,并没有产生具体的数据。只有通过new关键字创建该类的实例对象后,系统才会为每个对象分配内存空间,存储各自的数据。有时候,开发人员会希望某些特定的数据在内存中只有一份,而且能够被一个类的所有实例对象所共享。例如无锡科技职业学院的所有学生共享同一个学校名称,此时完全不必在每个学生对象所占用的内存空间中都声明一个变量来表示学校名称,而可以在对象以外的空间声明一个表示学校名称的变量让所有对象来共享。

# 静态方法

模块二 
知识链接

成员方法分为两种：一种是实例方法，没有被static 关键字修饰的方法；另一种是静态方法（类方法），是被static 关键字修饰的方法。

# 静态方法访问格式

模块二 
知识链接

如果想要使用类中的成员方法，就需要先将这个类实例化。而在实际开发时，开发人员有时希望在不创建对象的情况下，通过类名就可以直接调用某个方法，这时就需要使用静态方法，要实现静态方法只需要在成员方法前加上static关键字。
同静态变量一样，静态方法也可以通过类名和对象访问，具体如下所示。
类名.方法
或者
实例对象名.方法

# 静态方法和实例方法的区别

模块二 
知识链接

（1）静态方法可以不需要通过本类的实例对象而通过“类名.静态方法名”就可以调用。
（2）静态方法不能访问本类的实例变量和实例方法，但是可以访问静态成员。
（3）静态方法不能使用this关键字和super关键字，因为这两个关键字和特定的实例相关。
（4）实例方法可以访问静态成员和非静态成员，包括静态变量、静态常量、静态方法、实例变量和实例方法。

# 静态代码块

模块二 
知识链接

在Java类中，用static关键字修饰的代码块称为静态代码块。当类被加载时，静态代码块就会执行，由于类只加载一次，所以静态代码块只执行一次。在程序中，通常使用静态代码块对类的成员变量进行初始化。静态代码块使用注意事项：
（1）静态代码块不能存在于任何方法体内
（2）静态代码块不能直接访问实例变量和实例方法，需要通过类的实例对象来访问
（3）JVM在加载类时会执行静态代码块，所以静态代码块先于主方法执行。如果类中包含多个静态代码块，那么将按照先定义的代码块先执行，后定义的代码块后执行，每个静态代码块只执行一次。

# ，

过渡页

模块三  任务实现

子任务1：定义一个学生类，其中包括成员变量name,静态成员变量schoolName，构造方法public Student(String name)，成员方法public void show()；定义测试类，创建两个学生类对象，为静态变量赋值，分别输出两个学生的schoolName信息。

模块三 
任务实现

# 子任务1源码

子任务1：结合任务描述和知识链接中static关键字和静态变量知识点可以得到文件6-11所示的代码：

模块三 
任务实现

1public class Student {
2	String name;
3	private static String schoolName = "无锡职业学院"; 
4	public Student(String name) {
5		this.name=name;
6	}
7	public static String getSchool() {                 
8       return schoolName;
9}

10   public static void setSchool(String s) {
11    	schoolName = s;
12
13}   public void show() {
14	   System.out.println(name+"是"+schoolName+"的学生");
15}
16}

文件6-11 Example09.Java

# 子任务1源码

模块三 
任务实现

1public class Student {
2	static String schoolName;
3	String name;
4	public Student(String name) {
5		this.name=name;
6	}
7  public void show(){
8 }
9  }

10 public class Example09 {
11	public static void main(String[] args) {
12	Student stu1=new Student("李红");
13	Student stu2=new Student("王华");
14	Student.schoolName="无锡科技职业学院";
15	System.out.println(stu1.name+"是"+stu1.schoolName+"的学生");
16	System.out.println(stu2.name+"是"+stu2.schoolName+"的学生");
17 }
18 }

子任务1：结合任务描述和知识链接中static关键字和静态变量知识点可以得到文件6-11所示的代码：

文件6-11 Example09.Java

# 运行结果

模块三 
任务实现

文件6-11运行结果如图6-13所示：

图6-13文件6-11的运行结果

文件6-11中13、14行代码也可以写成：
System.out.println(stu1.name+"是"+Student.schoolName+"的学生");
System.out.println(stu2.name+"是"+Studen.schoolName+"的学生");

# ，

过渡页

模块三  任务实现

子任务2：定义一个学生类，其中包括成员变量name,静态成员变量schoolName，构造方法public Student(String name)，静态成员方法public static String getSchool()和public static void setSchool(String s)，成员方法public void show()；定义测试类，创建两个学生类对象，修改学生的学校信息，输出修改前后两个学生的信息。

模块三 
任务实现

# 子任务2源码

子任务2：结合任务描述和知识链接中static关键字和静态方法量知识点可以得到文件6-12所示的代码：
文件6-12 Example10.Java

模块三 
任务实现

1public class Student {
2	String name;
3	private static String schoolName = "无锡职业学院"; 
4	public Student(String name) {
5		this.name=name;
6	}
7	public static String getSchool() {                 
8       return schoolName;
9}

10   public static void setSchool(String s) {
11    	schoolName = s;
12
13}   public void show() {
14	   System.out.println(name+"是"+schoolName+"的学生");
15}
16}

# 子任务2源码

子任务2：结合任务描述和知识链接中static关键字和静态方法量知识点可以得到文件6-12所示的代码：
文件6-12 Example10.Java

模块三 
任务实现

17 public class Example10 {
18	public static void main(String[] args) {
19		Student stu1=new Student("李红");
20		Student stu2=new Student("王华");
21		System.out.println("----学校修改前----");
22		stu1.show();

23		stu2.show();
24		System.out.println("----学校修改后----");
25      Student.setSchool("无锡科技职业学院");
26		stu1.show();
27		stu2.show();
28	}
29 }

# 运行结果

模块三 
任务实现

文件6-12运行结果如图6-14所示：

图6-14文件6-12的运行结果

# ，

过渡页

模块三  任务实现

子任务3：测试静态代码块的使用：定义一个学生类，其中包括成员变量name，一个构造代码块，一个静态代码块，一个构造方法public Student()；定义测试类，创建三个学生类对象。

模块三 
任务实现

# 子任务3源码

结合任务描述和知识链接中静态代码块知识点可以得到文件6-13所示的代码：

模块三 
任务实现

1class Student{
2    String name;    		//成员属性
3    {
4        System.out.println("这是构造代码块");
5    }
6    static {
7        System.out.println("这是静态代码块");
8    }

9    public Student(){      	
10   System.out.println("Student类构造方法");
11}
12 }
13class Example11{
14    public static void main(String[] args) {
15        Student stu1 = new Student();
16        Student stu2 = new Student();
17        Student stu3 = new Student();
}
}

文件6-13 Example11.Java

# 运行结果

模块三 
任务实现

文件6-13运行结果如图6-15所示：

图6-12文件6-13运行结果

# 感谢关注
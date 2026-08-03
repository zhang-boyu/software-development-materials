# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

子任务1：定义一个学生类Student，其中包括属性姓名、年龄、性别、爱好；定义一个测试类用来输出学生信息。
子任务2：定义一个学生类Student，其中定义一个成员方法public void setName(String name) 用来初始化成员变量并输出学生姓名，再定义另一个成员方法public void  show()，该方法调用第一个成员方法setName(String name)；编写测试类。

# *

模块一  任务描述

子任务3：定义一个学生类Student，其中包括一个无参构造方法public Student () 和一个有参构造方法public Student(String name,int age),在有参构造方法中调用无参构造方法并在该方法中初始化这两个属性；定义一个成员方法public void  show()；编写测试类。

# ..

模块二 知识链接

this关键字

# this关键字

模块二 
知识链接

在Java中this关键字作用有三个：使用它调用本类的属性；使用它调用成员方法；使用它调用构造方法：
使用this关键字调用本类中的属性
在文件6-7中的构造方法public Student(String n, int a,String s,String h)中使用了参数n表示姓名，a表示年龄，s表示性别，h表示爱好，虽然语法上没有问题，但是可读性很差。这时可以将这些参数和成员变量命名一致，但这样导致命名冲突。解决的办法是在成员变量前面加上this关键字加以区分，如this.name是成员变量，name 是参数，也是局部变量。

# this关键字

模块二 
知识链接

在Java中this关键字作用有三个：使用它调用本类的属性；使用它调用成员方法；使用它调用构造方法：
使用this关键字调用本类中的属性，如以下代码：
public Student(String name,int age,String sex,String hobby) {
 this.name = name;
 this.age = age;
 this.sex=sex;
 this.hobby=hobby;
}

# this关键字

模块二 
知识链接

使用this关键字调用成员方法
使用this关键字也可以用来调用成员方法，例如以下代码：
public class Student {
	 String name;
	 public void setName(String name) {
	 		this.name=name;
	 		System.out.println(this.name);
	 }
	 public void show() {
	     this.setName("李红");
}
}上述代码中，在show()方法中使用this关键字调用了setName()方法。需要注意的是此处的this关键字也可以省略不写。

# this关键字

模块二 
知识链接

使用this关键字调用构造方法
构造方法是在实例化对象时被Java虚拟机自动调用，在程序中不能像调用其他成员方法一样调用构造方法，但可以在一个构造方法中使用“this(参数1,参数2…)”的形式调用其他的构造方法。

# this关键字

模块二 
知识链接

使用this关键字调用构造方法
例如以下代码：
1 class Student {
2	private String name;
3	private int age;
4	public Student () {
5		System.out.println("调用了无参的构造方法");
6	}
7 public Student (String name,int age) {
8	this();  // 调用无参的构造方法
9   this.name=name;
10  this.age=age;
}
}

# this关键字

模块二 
知识链接

使用this调用类的构造方法时，应注意以下三点。
（1）只能在构造方法中使用this调用其他的构造方法，不能在成员方法中通过this调用构造方法。
（2）在构造方法中，使用this调用其他构造方法的语句必须位于第一行，且只能出现一次。下面程序的写法是错误的。
（3）不能在一个类的两个构造方法中使用this互相调用，下面程序的写法是错误的。

# this关键字

模块二 
知识链接

使用this调用类的构造方法时，应注意以下三点。
（3）不能在一个类的两个构造方法中使用this互相调用，下面程序的写法是错误的。如以下代码：
class Student {
	public Student () {
        this("张三");  	// 调用有参构造方法
		System.out.println("调用无参构造方法。");
	}
	public Student (String name) {
		this();                  	// 调用无参构造方法
		System.out.println("调用有参构造方法。");
	}
}

# ，

过渡页

模块三  任务实现

子任务1：定义一个学生类Student，其中包括属性姓名、年龄、性别、爱好；定义一个测试类用来输出学生信息。

模块三 
任务实现

# 子任务1源码

结合任务描述和知识链接中使用this关键字调用本类中的属性，可以得到文件6-8所示的代码：文件6-8 Example06.Java

模块三 
任务实现

1 public class Student {
2    String name; 
3    int age;
4    String sex; 
5	 String  hobby;
6	 public Student(String name,int age,String sex,String hobby) {
7	 this.name = name;
8    this.age = age;
9	 this.sex=sex;
10	 this.hobby=hobby;
11	 }

12	 public void show(){
13      System.out.println(name+" "+age+" "+sex+" "+hobby);			
14		}	
15 }
16 public class Example06 {
17  public static void main(String[] args) {
18  Student stu=new Student("李明",18,"男","唱歌");
19  stu.show();
20   }
21  }

# 运行结果

模块三 
任务实现

运行结果如图6-10所示：

图6-10文件6-8运行结果

# ，

过渡页

模块三  任务实现

子任务2：定义一个学生类Student，其中定义一个成员方法public void setName(String name) 用来初始化成员变量并输出学生姓名，再定义另一个成员方法public void  show()，该方法调用第一个成员方法setName(String name)；编写测试类。

模块三 
任务实现

# 子任务2源码

结合任务描述和知识链接中使用this关键字调用成员方法，可以得到文件6-9所示的代码：
文件6-9 Example07.Java

模块三 
任务实现

1 public class Student {
2  String name;
3  public void setName(String name) {
4	 this.name=name;
5	 System.out.println(this.name);
6  }
7  public void  show() {
8   this.setName("李红");
9  }
10  }

11  public class Example07 {
12    public static void main(String[] args) {
13      Student stu1=new Student();
14      stu1.show();
15  }
16  }

# 运行结果

模块三 
任务实现

运行结果如图6-11所示：

图6-11文件6-9运行结果

# ，

过渡页

模块三  任务实现

子任务3：定义一个学生类Student，其中包括一个无参构造方法public Student () 和一个有参构造方法public Student(String name,int age),在有参构造方法中调用无参构造方法并在该方法中初始化这两个属性；定义一个成员方法public void  show()；编写测试类。

模块三 
任务实现

# 子任务3源码

结合任务描述和知识链接中使用this关键字调用构造方法，可以得到文件6-10所示的代码：
文件6-10 Example07.Java

模块三 
任务实现

1 public class Student {
2	private String name;
3   private int age;
4	public Student () {
5	   System.out.println("调用了无参的构造方法");
6 }
7  public Student (String name,int age) {
8   this();  // 调用无参的构造方法
9   this.name=name;
10  this.age=age;
11  System.out.println("调用了有参的构造方法");
12 }

13  public void show() {
14   System.out.println(name+" "+age);
15    }
16  }
17public class Example08 {
18  public static void main(String[] args) {
19  Student stu1=new Student();
20  Student stu2=new Student("李红",17);
21  stu2.show();
22	}
23 }

# 运行结果

模块三 
任务实现

运行结果如图6-12所示：

图6-12文件6-10运行结果

# 感谢关注
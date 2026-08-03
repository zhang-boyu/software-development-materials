# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

为了保护学生信息，对涉及到学生属性信息如姓名、年龄、性别、爱好进行封装，通过调用公有方法输出学生信息。

# ..

模块二 知识链接

封装的概念

封装的意义

如何实现封装

# 封装的概念

模块二 
知识链接

在Java面向对象的思想中，封装是指一种将类的实现细节包装、隐藏起来的方法。封装可以被认为是一个保护屏障，防止本类的代码和数据被外部类定义的代码随机访问。
在Java中通过private关键字限制对类的成员变量或成员方法的访问，称为封装。封装性是面向对象的基础，也是面向对象的核心特征之一。类是数据及对数据操作的封装体，类具有封装性。通过封装，将属性私有化，再提供公有方法访问私有属性。

# 封装的意义

模块二 
知识链接

封装的目的是限制对类的成员的访问，隐藏类的实现细节。类的设计者和使用者考虑的角度不同。设计者考虑如何定义类的属性和方法，如何设置其访问权限等，而类的使用者只需知道类有哪些功能，可以访问哪些属性和方法。只要使用者使用的界面不变，即使类的内部实现细节发生变化，使用者的代码就不需要改变，增强了程序的可维护性。

# 封装的意义

模块二 
知识链接

因此封装具有以下优点：
1. 良好的封装能够减少耦合。
2. 类内部的结构可以自由修改。
3. 可以对成员变量进行更精确的控制。
4. 隐藏信息，实现细节

# 如何实现封装

模块二 
知识链接

要限制类的外部对类成员的访问，可以使用访问修饰符private修饰属性，让其他类只能通过公共方法访问私有属性。封装的实现步骤如下：
1.修改属性的访问修饰符来限制对属性的访问。
例如，Student类中，属性name、age、sex、hobby都设置为private。
private String name;//属性name设为private
private int age	//属性age设为private
private String sex;	//属性 sex设为private
private String hobby;//属性 hobby设为private

# 如何实现封装

模块二 
知识链接

要限制类的外部对类成员的访问，可以使用访问修饰符private修饰属性，让其他类只能通过公共方法访问私有属性。封装的实现步骤如下：
2.为每个私有属性创建一对赋值方法setter( )和取值方法getter( )，用于对属性的访问。例如，为Student类对属性name、age、 sex、hobby创建公共setter( )和getter( )方法：如：      
1 public String getName() {
2  return name;
3}
4 public void setName(String name) {
5 this.name = name;
6 }

# ，

过渡页

模块三  任务实现

为了保护学生信息，对涉及到学生属性信息如姓名、年龄、性别、爱好进行封装，通过调用公有方法输出学生信息。

模块三 
任务实现

# 任务源码

结合任务6-5中的描述和知识链接中封装相关知识点可以得到文件6-6所示的代码：
        文件6-6 Example04.Java

模块三 
任务实现

1 public class Student {
2	private  int age ; 
3	private  String name;
4	private  String sex; 
5	private  String hobby;
6	public String getName() {
7		 return name;
8		}
9	public void setName(String name) {
10		 this.name = name;
11	 }

12	public int getAge() {
13	 return age;
14	  }
15	public void setAge(int age) {
16		if(age < 0){
17		  System.out.println("您输入的年龄有误！");
18		 } 
19        else {
20		   this.age = age;
21		}
22		  }

# 任务源码

结合任务6-5中的描述和知识链接中封装相关知识点可以得到文件6-6所示的代码：
        文件6-6 Example04.Java

模块三 
任务实现

23	public String getSex(){
24		   return sex;
25		 }
26		public void setSex(String sex) {
27		  this.sex = sex;
28		 }
29	public void setHobby(String hobby) {
30		 this.hobby = hobby;
31		 }
32	public String getHobby() {
33		 return hobby;
34		     }

35	public void show() {
36		System.out.println(name+" "+age+" "+sex+" "+hobby);
37	}
38}
39 public class Example04 {
40	public static void main(String[] args) {
41    Student stu=new Student();
42    stu.setName("李华");
43    stu.setAge(18);
44    stu.setSex("男");
45    stu.setHobby("跑步");
46    stu.show();   
47	}
48}

# 运行结果

模块三 
任务实现

文件6-6的运行结果如图6-6所示。

图6-6文件6-6的运行结果

# 说明

第35行代码也可以这样写：
public void show() {
System.out.println(getName()+" "+getAge()+" "+getSex()+" "+getHobby());
}
当43行代码写成stu.setAge(-18);将出现如图6-7的错误信息：

模块三 
任务实现

图6-7年龄小于0的运行结果

# 说明

在实际开发中，如果成员变量和局部变量的名称设置成一样的，会导致成员变量和局部变量的名称冲突，所以通常会使用this指代当前对象，通过this访问当前对象的成员变量。this关键字会在任务6-7中详细介绍。

模块三 
任务实现

# 作业

1、定义一个狗的类，包括属性：名字，年龄；方法：1）输出狗的信息的方法；2）狗能跳多远的方法；
      2、定义一个测试类：输出结果如下:花花今年3岁了，能跳1.5米。

模块三 
任务实现

# 感谢关注
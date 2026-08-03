# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

访问学生类的公有属性hobby、sex、保护类型age、私有属性name。

# ..

模块二 知识链接

访问控制权限

包的定义与访问

Java中常用的程序包

导入包

# 访问控制权限

模块二 
知识链接

在Java中，针对类、成员方法和属性，Java提供了4种访问控制权限，分别是private、default、protected和public。下面通过一张图将这4种访问控制权限按级别由低到高依次列出，如图6-3所示。



图6-3访问控制权限

# 访问控制权限

模块二 
知识链接

1.private：private属于私有访问权限，用于修饰类的属性和方法，也可以修饰内部类。类的成员一旦使用了private关键字修饰，则该成员只能在本类中进行访问。
2.default：default属于默认访问权限，如果一个类中的属性或方法没有任何的访问权限声明，则该属性或方法就是默认的访问权限，默认的访问权限可以被本包中的其他类访问，但是不能被其他包的类访问。
3.protected：protected属于受保护的访问权限。如果一个类中的成员使用了protected访问权限，则只能被本包及不同包的子类访问。
4.public：public属于公共访问权限。如果一个类中的成员使用了public访问权限，则该成员可以在所有类中被访问，不管是否在同一包中。

# 访问控制权限

模块二 
知识链接

下面通过一张表总结上述访问控制权限，如下表所示。
表6-1访问控制权限

| 访问范围 | private | default | protected | public |
|---|---|---|---|---|
| 同一类中 | √ | √ | √ | √ |
| 同一包中的类 |  | √ | √ | √ |
| 不同包的子类 |  |  | √ | √ |
| 全局范围 |  |  |  | √ |

# 包的定义与访问

模块二 
知识链接

为更好地利用和管理类，Java引入了包的机制。所谓包就是一组相关类的集合。包和操作系统管理磁盘的“文件夹”或“目录”概念基本相似。因此在设计包时，应该尽可能地将功能相近、用途相似、相互之间关系密切的类放在同一个包中。
  同一个包中的类是可见的。如果一个类没有访问控制符，说明它具有缺省的访问控制符特性。此时，这个类只能被同一个包中的类访问或引用。这一访问特性又称为包访问性。
  在Java中，同一个包中的类和接口之间的相互访问权限要高于不同包的类和接口，所以在设计类时应该有意识地规划组织类。

# Java中常用的程序包

模块二 
知识链接

1.java.lang包
java.lang包是Java语言的核心类库，包含了运行Java程序必不可少的系统类，如基本数据类型、基本数学函数、字符串处理、线程、异常处理类等
2.java.io包
java.io包是Java语言的标准输入/输出类库，包含了实现Java与操作系统、用户界面以及其他Java程序做数据交换所使用的类，如基本输入/输出流、文件输入/输出流、过滤输入/输出流、管道输入/输出流、随机输入/输出流等。
3.java.util包
java.util包包括了Java语言中的一些低级的实用工具，如处理时间的Date类，处理变长数组的Vector类，实现栈和杂凑表的Stack类和Hashtable类等。

# Java中常用的程序包

模块二 
知识链接

4.java.awt包
java.awt包是Java语言用来构建用户界面（GUI）的类库，它包括了许多界面元素和资源，主要在三个方面提供界面设计支持：低级绘图操作，如Graphics类等；图形界面组件和布局管理，如Checkbox类、Container类、LayoutManager接口等；以及界面用户交互控制和事件响应，如Event类。
5.java.applet包
java.applet包用来实现运行于Internet浏览器中的Java Applet的工具类库，它仅包含少量几个接口和一个非常有用的类Java.applet.Applet。

# Java中常用的程序包

模块二 
知识链接

6.java.net包
java.net包是Java语言用来实现网络功能的类库。实现的功能，如：底层的网络通信，如实现套接字通信的Socket类、ServerSocket类；编写用户自己的Telnet、FTP、邮件服务等实现网上通信的类；用于访问Internet上资源的类，如URL类等。
7.java.sql包
java.sql包是实现JDBC（Java database connection）的类库。利用这个包可以使Java程序具有访问不同种类数据库的功能，如Oracle、Sybase、DB2、SQL Server等。只要安装了合适的驱动程序，同一个Java程序几乎不需修改就可以存取、修改这些不同的数据库中的数据。

# 导入包

模块二 
知识链接

将类组织成包的目的是为了更好地引用包中的类，通常一个类只能引用与它在同一个包中的类。如果需要使用其它包中的public类，通常可使用以下方式：
1.加载需要使用的类
在程序文件的开始部分利用import语句将需要使用的整个类加载到当前程序中，这样在程序中需要引用这个类的地方就不需再使用包名作为前缀。如：
import Java.util.ArrayList;//导入处理数组的包
ArrayList a = new ArrayList();//新建ArrayList的实例
2.加载整个包
有些情况下可以直接利用import语句引入整个包，此时这个包中的所有类都会被加载到当前程序中，凡是用这个包中的类，都不需要再使用包名前缀。加载整个包的import语句可以写为：import Java.util.*;

# ，

过渡页

模块三  任务实现

访问学生类的公有属性hobby、sex、保护类型age、私有属性name。

模块三 
任务实现

# 任务源码

结合任务6-4中的描述和知识链接中访问控制权限知识点可以得到文件6-4所示的代码：
     文件6-4 Example03.Java

模块三 
任务实现

1 public class Student {
2	private String name="李红";//私有属性
只能在本类中进行访问
3	protected int age;	
4	public String sex;
5	public String hobby;
6	public String toString(){
7		return name+" "+age+" "+sex+" "+hobby; 
8 }
9	}

10 public class Example03 {
11  public static void main(String[] args) {
12	 Student stu1=new Student();
13	 stu1.age=18;
14	 stu1.sex="女";
15	 stu1.hobby="唱歌";
16	 System.out.println(stu1.toString());
17	}
18 }

# 运行结果

模块三 
任务实现

文件6-4的运行结果如图6-4所示。

图6-4 文件6-4的运行结果

# 说明

结合任务6-4中的描述和知识链接中访问控制权限知识点可以得到文件6-4所示的代码：
     文件6-4 Example03.Java

模块三 
任务实现

1public class Student {
2	private String name;
3	protected int age;	
4	public String sex;
5	public String hobby;
6	public String toString(){
7		return name+" "+age+" "+sex+" "+hobby; 
8}
9	}

10 public class Example03 {
11 public static void main(String[] args) {
12  Student stu1=new Student();
13  stu1.name ="李红";
14	 stu1.age=18;
15	 stu1.sex="女";
16	 stu1.hobby="唱歌";
17	 System.out.println(stu1.toString());
18	} 
19}

# 运行结果

模块三 
任务实现

运行会出现以下错误提示：The field Student.name is not visible，即name属性不能在Example03类中被访问。

图6-5 文件6-5的运行结果

# 感谢关注
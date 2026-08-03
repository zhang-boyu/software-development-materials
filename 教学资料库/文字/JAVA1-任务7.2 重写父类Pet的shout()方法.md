# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

定义一个父类Pet，包含shout()方法；定义一个子类Cat继承于父类Pet并重写父类的shout()方法;定义测试类输出Cat相关信息。

# ..

模块二 知识链接

方法的重写

子类重写父类方法时的访问权限

# 方法的重写

模块二 
知识链接

在继承关系中，子类会自动继承父类中定义的方法，但有时在子类中需要对继承的方法进行一些修改，即对父类的方法进行重写。在子类中重写的方法需要和父类被重写的方法具有相同的方法名、参数列表以及返回值类型。例如以下代码：

# 方法的重写

模块二 
知识链接

1 class Pet {		
2	public void shout() {			  
3		System.out.println("动物发出叫声");
4	}
5}
6 class Cat extends Pet {    
7	public void shout() {			 
8		System.out.println("喵喵");  
9	}
10}

# 子类重写父类方法时的访问权限

模块二 
知识链接

子类重写父类方法时，不能使用比父类中被重写的方法更严格的访问权限。例如，父类中的方法是public权限，子类的方法就不能是private权限。如果子类在重写父类方法时定义的权限缩小，如以下代码，则在编译时将出现错误,错误提示会在任务7-2重写父类Pet的shout()方法的实现中进一步说明。

# 子类重写父类方法时的访问权限

模块二 
知识链接

1 class Pet {		
2	public void shout() {			  
3		System.out.println("动物发出叫声");
4	}
5}
6 class Cat extends Pet {    
7	private void shout() {			 
8		System.out.println("喵喵");  
9	}
10}

# ，

过渡页

模块三  任务实现

定义一个父类Pet，包含shout()方法；定义一个子类Cat继承于父类Pet并重写父类的shout()方法;定义测试类输出Cat相关信息。

模块三 
任务实现

# 任务源码

结合任务7-2中的描述和知识链接中知识点方法的重写可以得到文件7-3所示的代码：

模块三 
任务实现

文件7-3 Example01.Java

1 class Pet {		
2	public void shout() {			  
3		System.out.println("动物发出叫声");
4	}
5}
6 class Cat extends Pet {    
7	public void shout() {			 
8		System.out.println("喵喵");  
9	}
10 }

11public class Example03 {
12	public static void main(String[] args) {
13		 Cat cat = new Cat(); 
14		 cat.shout();
15	}
16 }

# 运行结果

文件7-3的运行结果如图7-3所示：

模块三 
任务实现

图7-3 文件7-3的运行结果

# 运行结果

模块三 
任务实现

如果没有重写父类的shout()方法，即将上述Cat类代码改为如下代码所示：
public class Cat extends Pet {
	 }
输出结果如图7-4所示：

图7-4文件7-3未重写父类方法的运行结果

# 运行结果

模块三 
任务实现

若把文件7-3中第7行代码改为private void shout()时会出现如图7-5的错误提示信息：





            图7-5子类方法修改为private权限的运行结果

# 感谢关注
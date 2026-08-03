# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务1：在子类Cat中访问父类Pet的非私有属性name和非私有方法shout()
子任务2：在子类Cat的构造方法 public Cat(String name, int age, String color){}中调用父类Pet的构造方法public Pet(String name, int age){}

# ..

模块二 知识链接

super关键字

# super关键字

模块二 
知识链接

在Java中，super关键字是一个非常重要的概念，它主要用于引用当前对象的直接父类对象（超类对象）。当子类重写父类的方法后，子类对象将无法访问父类中被子类重写过的方法。为了解决这个问题，Java提供了super关键字，使用super关键字可以在子类中访问父类的非私有方法、非私有属性以及构造方法。super关键字主要用于以下几种情况：

# super关键字

模块二 
知识链接

1.访问父类的属性和方法
如果子类与父类有同名的属性和方法，子类想要调用父类中声明的那个属性或方法时，就需要使用super关键字。具体格式如下：
super.属性
super.方法(参数1,参数2…)

# super关键字

模块二 
知识链接

2.使用super关键字调用父类中指定的构造方法
   在子类的构造方法中，如果你想调用父类的构造方法，就必须使用super关键字，并且这是super在子类的构造方法中的唯一用途。注意，super()调用必须是子类构造方法中的第一条语句（除了注释）。具体格式如下：
super(参数1,参数2…)

# super关键字

模块二 
知识链接

2.使用super关键字调用父类中指定的构造方法
  在子类的方法中，super可以引用父类的实例，这主要是从逻辑上理解，super关键字代表当前对象的直接父类对象。super关键字的使用不仅限于上述场景，但它主要围绕子类与父类之间的交互和继承关系。理解super的使用对于掌握Java中的继承和多态等面向对象编程的核心概念至关重要。

# super关键字

模块二 
知识链接

3.super与this的区别
  super与this关键字的作用非常相似，都可以调用构造方法、方法和属性，但是两者之间还是有区别的，super与this的区别如表7-1所示。

# super关键字

模块二 
知识链接

3.super与this的区别

注意：this和super不可以同时出现，因为使用this和super调用构造方法的代码都要求必须放在构造方法的首行。

| 区别点 | super | this |
|---|---|---|
| 访问属性 | 直接访问父类中的非私有属性 | 访问本类中的属性。如果本类中没有该属性,则从父 类中继续查找 |
| 调用方法 | 直接调用父类中的非私有方法 | 调用本类中的方法。如果本类中没有该方法,则从父 类中继续查找 |
| 调用构造方法 | 调用父类构造方法,必须放在子类构造方法的首行 | 调用本类构造方法,必须放在构造方法的首行 |

# ，

过渡页

模块三  任务实现

子任务1：在子类Cat中访问父类Pet的非私有属性name和非私有方法shout()。

模块三 
任务实现

# 任务源码

结合任务描述和知识链接中使用super关键字访问父类的属性和方法知识点可以得到
文件7-4所示的代码：

模块三 
任务实现

文件7-4 Example04.Java

1public class Pet {
2	String name = "花花";
3   void shout() {
4       System.out.println("宠物发出叫声");
5    }
6}

7public class Cat extends Pet {
8	public void shout() {
9        super.shout();      // 调用父类中的shout()方法
10        System.out.println("喵喵……");
11    }
12    public void printName(){
13      System.out.println("这只猫叫"+super.name);// 访问父类中的name属性
14    }
15	 }

# 任务源码

结合任务描述和知识链接中使用super关键字访问父类的属性和方法知识点可以得到
文件7-4所示的代码：

模块三 
任务实现

文件7-4 Example04.Java

16public class Example04 {
17	public static void main(String[] args) {
18		  Cat cat = new Cat();   
19	      cat.shout();      
20	      cat.printName();  
21	}
22}

# 运行结果

文件7-4运行结果如图7-6所示：

模块三 
任务实现

图7-6文件7-4运行结果

# ，

过渡页

模块三  任务实现

子任务2：在子类Cat的构造方法 public Cat(String name, int age, String color){}中调用父类Pet的构造方法public Pet(String name, int age){}

模块三 
任务实现

# 任务源码

子任务2：结合任务描述和知识链接中使用super关键字访问父类中指定的构造方法知识点可以得到文件7-5所示的代码：

模块三 
任务实现

文件7-5 Example05.Java

1public class Pet {
2	private String name;
3    private int age;
4    public Pet(String name, int age) {	// Animal类有参构造方法
5        this.name = name;
6        this.age = age;
7    }
8    public String getName() {
9        return name;
10    }
11    public void setName(String name) {
12        this.name = name;
13    }

14    public int getAge() {
15        return age;
16    }
17    public void setAge(int age) {
18        this.age = age;
19    }
20    public void show() {
21 System.out.print( "这只猫咪叫"+this.getName()+",今年"+this.getAge()+"岁了");
22    }
23}

# 任务源码

结合任务描述和知识链接中使用super关键字访问父类的属性和方法知识点可以得到
文件7-4所示的代码：

模块三 
任务实现

文件7-4 Example04.Java

24public class Cat extends Pet {
25	private String color;
26   public Cat(String name, int age, String color) {
27      super(name, age); //通过super关键字调用Pet类有两个参数的构造方法
28       this.setColor(color);
29    }
30    public String getColor() {
31        return color;
32    }
33    public void setColor(String color) {
34        this.color = color;
35    }

// 重写父类的show()方法
36    public void  show() {
37    	super.show();
38       System.out.println(",颜色是"+this.getColor());  // 扩充父类中的方法
39    }
40	 }
41public class Example05 {
42	public static void main(String[] args) {
43		  Cat cat = new Cat("花花",3,"白色");            
44	      cat.show();
45	}
46}

# 运行结果

文件7-5运行结果如图7-7所示：

模块三 
任务实现

图7-7文件7-5的运行结果

如果父类中没有无参构造方法，而子类构造方法中又没有显式调用父类的其他构造方法，则编译时会报错。例如去掉文件7-5中27行代码，就会出现如图7-8的错误提示：

图7-8 子类未调用父类的其他构造方法的运行结果

# 感谢关注
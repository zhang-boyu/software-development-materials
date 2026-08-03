# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务1：定义父类Pet，包含方法void eat()；定义子类Cat和Dog，两个子类重写父类中的eat()方法；定义测试类，测试两个类实例的不同形态。
子任务2：定义父类Pet，包含方法void shout()；定义子类Dog包含方法void shout()和 void eat()；定义测试类，创建Dog实例和Pet实例，使父类Pet实例指向子类Dog实例，使用父类实例调用shout()方法。

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务3：定义父类Pet和子类Dog，其中包含的方法同任务2；定义测试类，创建Dog实例，使父类Pet实例指向子类Dog实例，然后使父类实例强制转换为子类实例，使用子类实例调用shout()方法。

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务4：定义父类Pet，包含方法void eat()；定义子类Cat和Dog，两个子类重写父类中的eat()方法；定义测试类，创建Dog实例和Cat实例使父类Pet实例指向子类Dog实例和Cat实例,判断Dog实例是否属于Dog实例Pet实例,判断Cat实例是否属于Cat实例Pet实例，判断Dog实例是否不属于Cat实例。

# ..

模块二 知识链接

多态概述

对象类型的转换

instanceof关键字

# 多态概述

模块二 
知识链接

多态是面向对象思想中的一个非常重要的概念，在Java中，多态是指不同类的对象在调用同一个方法时表现出的多种不同行为。例如，要实现一个动物叫声的方法，由于每种动物的叫声是不同的，因此可以在方法中接收一个动物类型的参数，当传入猫类对象时就发出猫类的叫声，传入犬类对象时就发出犬类的叫声。在同一个方法中，这种由于参数类型不同而导致执行效果不同的现象就是多态。
Java中的多态是面向对象编程的一个核心概念，它允许我们以统一的接口来处理不同的对象类型。多态性主要体现在两个方面：编译时多态（静态多态）和运行时多态（动态多态）。Java主要利用运行时多态来实现其强大的功能。

# 对象类型的转换

模块二 
知识链接

掌握对象类型的转换，能够在多态时使用向上转型和向下转型完成对象类型的转换
对象向上转型
对象向上转型父类对象可以调用子类重写父类的方法，这样当需要新添功能时，只需要新增一个子类，在子类中对父类的功能进行扩展，而不用更改父类的代码，保证了程序的安全性。对于向上转型，程序会自动完成，对象向上转型格式如下所示：
父类类型 父类对象 = 子类实例;

# 对象类型的转换

模块二 
知识链接

对象向下转型
除了向上转型，对象还可以向下转型。向下转型一般是为了重新获得因为向上转型而丢失的子类特性。对象在进行的向下转型前，必须先进行向上转型，否则将出现对象转换异常。   	向下转型时，必须指明要转型的子类类型。对象向下转型格式如下所示：
父类类型 父类对象=子类实例;
子类类型 子类对象=（子类）父类对象;

# instanceof关键字

模块二 
知识链接

instanceof 关键字在 Java 中是一个二元操作符，它用于测试左边的对象是否是右边类或接口的实例。如果左边的对象确实是右边类或接口的实例（或者实现了该接口），则 instanceof 表达式的结果是 true；否则，结果是 false。这个操作符在处理多态时特别有用，因为它允许你在运行时检查对象的实际类型。语法格式如下所示：
对象  instanceof  类（或接口）

# ，

过渡页

模块三  任务实现

子任务1：定义父类Pet，包含方法void eat()；定义子类Cat和Dog，两个子类重写父类中的eat()方法；定义测试类，测试两个类实例的不同形态。

模块三 
任务实现

# 任务源码

子任务1：结合任务描述和知识链接中多态知识点可以得到文件7-13所示的代码：

模块三 
任务实现

文件7-13  Example13

1public class Pet  {
2	 void eat() {  
3	        System.out.println("宠物吃食物");  
4	    }  
5}
6public class Cat extends Pet {
7	void eat() {  
8       System.out.println("猫爱吃鱼");  
9    }  
10  }
11public class Dog  extends Pet {
12	void eat() {  
13        System.out.println("狗爱吃肉");  
14    }  
15}

16public class Example13 {
17	public static void main(String[] args) {
18	  Pet pet1 = new Cat(); // 创建Cat对象,使用Pet类型的变量pet1引用
19	  Pet pet2 = new Dog(); // 创建Dog对象,使用Pet类型的变量pet2引用
20    pet1.eat();
21    pet2.eat();       
22	}
23}

# 运行结果

模块三 
任务实现

文件7-13的运行结果如图7-15所示：

图7-15文件7-13的运行结果

# ，

过渡页

模块三  任务实现

子任务2：定义父类Pet，包含方法void shout()；定义子类Dog包含方法void shout()和 void eat()；定义测试类，创建Dog实例和Pet实例，使父类Pet实例指向子类Dog实例，使用父类实例调用shout()方法。

模块三 
任务实现

# 任务源码

结合任务描述和知识链接中对象向上转型知识点可以得到文件7-14所示的代码：

模块三 
任务实现

文件7-14  Example14

1public class Pet  {
2	 void shout() {
3		 System.out.println("宠物发出叫声");  
4	 }
5}
6public class Dog extends Pet {
7	void eat() {  
8        System.out.println("狗爱吃肉");  
9    } 
10	void shout() {
11		 System.out.println("汪汪......");  
12	 }
13}

14public class Example14 {
15	public static void main(String[] args) {
16		Dog dog=new Dog();
17		Pet pet=dog;// 向上转型
18		pet.shout();
19	}
20}

# 运行结果

模块三 
任务实现

文件7-14的运行结果如图7-16所示：

图7-16文件7-14的运行结果

# ，

过渡页

模块三  任务实现

子任务3：定义父类Pet和子类Dog，其中包含的方法同任务2；定义测试类，创建Dog实例，使父类Pet实例指向子类Dog实例，然后使父类实例强制转换为子类实例，使用子类实例调用shout()方法。

模块三 
任务实现

# 任务源码

结合任务描述和知识链接中对象向上转型知识点可以得到文件7-15所示的代码，其中类Pet和Dog代码同子任务2，这里不再重复，以下是测试类的代码：

模块三 
任务实现

文件7-15  Example15

1public class Example15 {
2	public static void main(String[] args) {
3	   Pet pet=new Dog();// 向上转型
4     Dog dog=(Dog)pet;// 向下转型
5	   dog.shout();
6	}
7}

# 运行结果

模块三 
任务实现

文件7-15的运行结果如图7-17所示：

图7-17文件7-15的运行结果

注意：在向下转型时，不能直接将父类实例强制转换为子类实例，否则程序会报错。
例如，将文件7-15中第3-4行代码修改为下面一行代码，则程序报错。
Dog dog = (Dog)new Pet();//编译错误

# ，

过渡页

模块三  任务实现

子任务4：定义父类Pet，包含方法void eat()；定义子类Cat和Dog，两个子类重写父类中的eat()方法；定义测试类，创建Dog实例和Cat实例使父类Pet实例指向子类Dog实例和Cat实例,判断Dog实例是否属于Dog实例Pet实例,判断Cat实例是否属于Cat实例Pet实例，判断Dog实例是否不属于Cat实例。

模块三 
任务实现

# 任务源码

结合任务描述和知识链接中instanceof关键字语法格式知识点可以得到文件7-16所示的代码：

模块三 
任务实现

文件7-16  Example16

1public class Pet  {
2	 void eat() {  
3	        System.out.println("宠物吃食物");  
4	    }  
5}
6public class Cat extends Pet {
7	void eat() {  
8        System.out.println("猫爱吃鱼");  
9    }  
10  }

11public class Dog  extends Pet {
12	void eat() {  
13        System.out.println("狗爱吃肉");  
14    }  
15}

# 任务源码

结合任务描述和知识链接中instanceof关键字语法格式知识点可以得到文件7-16所示的代码：

模块三 
任务实现

文件7-16  Example16

16public class Example16 {
17	public static void main(String[] args) {
18		Pet dog = new Dog(); // 多态  
19		Pet cat = new Cat(); // 多态  
20        if (dog instanceof Dog) {  
21            System.out.println("dog是Dog的一个实例");  
22        }  
23        if (dog instanceof Pet) {  
24            System.out.println("dog是Pet的一个实例");  
25        }  
26        if (cat instanceof Pet) {  
27            System.out.println("cat是Pet的一个实例");  
28        }

29        if (cat instanceof Cat) {  
30            System.out.println("cat是Cat的一个实例");  
31        }  
        // 下面的判断会失败，因为dog是Dog的实例，而不是Cat的实例  
32        if (!(dog instanceof Cat)) {  
33            System.out.println("dog不是Cat的一个实例");  
34        }   
35    }  
36	}

# 运行结果

模块三 
任务实现

文件7-16的运行结果如图7-18所示：

图7-18文件7-16的运行结果

需要注意的是，instanceof 不能用于基本数据类型，如下面的代码会编译错误  
   if (1 instanceof Integer) {  
      }

# 感谢关注
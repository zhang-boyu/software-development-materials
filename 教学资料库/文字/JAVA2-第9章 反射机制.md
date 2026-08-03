# 第9章  反射机制

Java基础入门（第3版）

# 学习目标/Target

# 章节概述/ Summary

在Java中，如果定义了一个类，则可以通过类的实例化操作创建对象，并通过对象获取对应的类信息。反射机制是Java中非常重要的一个知识点，应用面很广，Java中的大部分类库以及框架底层都用到了反射机制，反射机制是Java框架设计的灵魂。本章将针对Java的反射机制进行详细讲解。

# 目录/Contents

# 反射概述

9.1

# 9.1  反射概述

先定一个小目标！

# 9.1  反射概述

在日常生活中，反射是一种物理现象，例如，通过照镜子可以反射出你的容貌，水面可以反射出物体的形态等，这些都是反射。通过反射，可以将一个虚像映射到实物，这样就可以获取实物的某些形态特征。Java程序中也有反射，Java程序中的反射也是同样的道理，常规情况下程序通过类创建对象，反射就是将这一过程进行反转，通过实例化对象来获取所属类的信息。

反射概述

# 9.1  反射概述

反射的作用

Java的反射机制可以动态获取程序信息以及动态调用对象的功能，它主要有以下4个作用。
（1）在程序运行状态中，构造任意一个类的对象。
（2）在程序运行状态中，获取任意一个对象所属的类的信息。
（3）在程序运行状态中，调用任意一个类的成员变量和方法。
（4）在程序运行状态中，获取任意一个对象的属性和方法。

# 9.1  反射概述

反射的优点

反射机制的优点是可以实现动态创建对象和编译(即动态编译)，特别是在Java EE的开发中，反射的灵活性表现的十分明显。
例如，一个大型的软件，不可能一次就把程序设计得很完美，当这个程序编译、发布上线后，需要更新某些功能时，如果采用静态编译，需要把整个程序重新编译一次才可以实现功能的更新，这就需要用户把以前的软件卸载，再重新安装新的版本。而采用反射机制，程序可以在运行时动态地创建和编译对象，不需要用户重新安装软件，即可实现功能的更新

# 认识Class类

9.2

# 9.2  认识Class类

先定一个小目标！

# 认识Class类

9.2  认识Class类

在1.5节中学习了Java程序的运行机制，JVM编译.java文件生成对应的.class文件，然后将.class文件加载到内存中执行。在执行.class文件的时候可能需要用到其他类（其他.class文件内容），这个时候就需要获取其他类的信息（反射）。JVM在加载.class文件时，会产生一个Class对象代表该.class字节码文件，从Class对象中可以获得.class文件内容，即获得类的信息。因此要想完成反射操作，就必须先认识Class类。

# 9.2  认识Class类

Class类的常用方法

Class类提供了很多方法，通过Class类的方法可以获取一个类的相应信息，包括该类的方法、属性，具体如下所示。

| 方法 | 描述 |
|---|---|
| forName(String className) | 获取与给定字符串名称的类或接口相关联的Class对象 |
| getConstructors() | 获取类中所有public修饰的构造方法对象 |
| getDeclaredFields() | 获取所有成员变量对应的字段类对象，包括public，protected，default和private修饰的字段，但不包括从父类继承的字段 |
| getFields() | 获取所有public修饰的成员变量对应的字段类对象，包括从父类继承的字段 |
| getMethods() | 获取所有public修饰的成员方法对应的方法类对象，包括从父类继承的方法 |
| getMethod(String name,        Class...parameter Type) | 根据方法名和参数类型获得对应的方法类对象，并且只能获得public修饰的方法类对象 |
| getInterfaces() | 获取当前类所实现的全部接口 |

# 9.2  认识Class类

| 方法 | 描述 |
|---|---|
| getClass() | 获取调用该方法的Class对象 |
| getName() | 获取类的完整名称，名称中包含包的名称 |
| getPackage() | 获取类所属的包名称 |
| getSuperclass() | 获取类的父类 |
| newInstance() | 创建Class对象关联类的对象 |
| getComponentType() | 获取数组的对应Class对象 |
| isArray() | 判断此Class对象是否是一个数组 |

# Class类实例化对象的3种方式

9.2  认识Class类

因为Class类本身并没有定义任何构造方法，所以Class类不能直接使用构造方法进行对象的实例化，使用Class类进行对象的实例化可以使用以下3种方式：
（1）根据全限定类名获取：Class.forName(“全限定类名”)。
（2）根据对象获取：对象名.getClass()。
（3）根据类名获取：类名.class。

# 9.2  认识Class类

案例演示

下面通过一个案例演示Class类的3种实例化方式。具体代码如下所示。

class A{      }
class Example01 {
public static void main(String args[]){
      Class<?> c1 = null;			//声明Class对象c1
      Class<?> c2 = null;			//声明Class对象c2
      Class<?> c3 = null;			//声明Class对象c3
       try{ 
          c1 = Class.forName("com.itheima.A");//通过第（1）种方式实例化c1对象
       }catch(ClassNotFoundException e){
          e.printStackTrace();
      }
      c2 = new A().getClass();		//通过第（2）种方式实例化c2对象
      c3 = A.class;			//通过第（3）种方式实例化c3对象
      System.out.println("类名称："+c1.getName());
      System.out.println("类名称："+c2.getName());
      System.out.println("类名称："+c3.getName());
}
}

# 案例运行结果

9.2  认识Class类

运行代码，控制台显示的运行结果如下图所示。

# 案例运行结果分析

从上图可以看出，3种实例化Class对象的结果是一样的，但是类名.class是JVM使用类装载器，将类装入内存(如果类还没有装入内存),不做类的初始化工作，返回Class的对象；Class.forName("类名字符串")会进行类的静态初始化，返回Class的对象；实例对象.getClass()返回实例对象运行时所属的类的Class的对象。

9.2  认识Class类

# Class类的使用

9.3

# 9.3.1  通过无参构造方法实例化对象

先定一个小目标！

# 如果想通过Class类实例化其他类的对象，则可以调用newInstance()方法，在调用newInstance()方法实例化其他类的对象时，必须要保证被实例化的类中存在一个无参构造方法。

9.3.1  通过无参构造方法实例化对象

通过无参构造方法实例化对象

# 9.3.1  通过无参构造方法实例化对象

案例一演示通过无参构造方法实例化对象

通过一个案例演示Class类通过无参构造方法实例化对象。具体步骤如下。

# 9.3.1  通过无参构造方法实例化对象

class Person{
   private String name;
   private int age;
   public String getName() {return name;}
   public void setName(String name) {this.name = name;}
   public int getAge() {return age;}
   public void setAge(int age) {this.age = age;}
   public String toString() {
        return "姓名："+this.name+",年龄："+this.age;
   }
}

步骤一：创建Person类，在Person类中定义name和age属性并编写name与age的getter和setter方法及toString()方法。代码如下所示：

# 9.3.1  通过无参构造方法实例化对象

public static void main(String args[]){
      Class<?> c = null; 			//声明Class类对象c
     try{
          c = Class.forName("com.itheima.Person");//调用forName()方法实例化c
      }catch(ClassNotFoundException e){
         e.printStackTrace();
      }
     Person per = null;			//声明Person类对象per
      try{
        per = (Person)c.newInstance();//通过c调用newInstance()方法实例化per
      }catch (Exception e){
         e.printStackTrace();
      }
      per.setName("张三");
      per.setAge(30);
      System.out.println(per);
   }

步骤二：定义main()方法，调用Class.forName()方法实例化Class对象，将Person的全限定名作为参数传入，使用Class对象c调用newInstance()方法实例化对象per。代码如下所示：

# 运行代码，控制台显示的运行结果如下图所示。

注意：在调用newInstance()方法实例化类对象时，被实例化对象的类中必须存在无参构造方法，否则无法实例化对象。

案例一运行结果

9.3.1  通过无参构造方法实例化对象

# 9.3.1  通过无参构造方法实例化对象

案例二演示没有无参构造方法时实例化对象

通过一个案例演示没有无参构造方法时，通过newInstance()方法实例化对象。具体步骤如下。

# 9.3.1  通过无参构造方法实例化对象

class Person{
    private String name;
    private int age;
    public Person(String name,int age){		//定义有参构造方法
         this.setName(name);
         this.setAge(age);
    }
    public String toString() {
        return "姓名："+this.name+",年龄："+this.age;
    }
    //省略定义getter/setter方法的代码
}

步骤一：定义Person类，在Person类中定义name和age属性并编写属性的getter和setter方法及toString()方法，定义有参构造方法。代码如下所示：

# 9.3.1  通过无参构造方法实例化对象

public static void main(String args[]){
      Class<?> c = null; 
     try{
          c = Class.forName("com.itheima.Person");
      }catch(ClassNotFoundException e){
         e.printStackTrace();
      }
     Person per = null;
      try{
        per = (Person)c.newInstance();
      }catch (Exception e){
         e.printStackTrace();
      }
  }

步骤二：定义main()方法，对Person对象使用newInstance()方法进行实例化，代码如下所示：

# 运行代码，控制台显示的运行结果如下图所示。

由图可知，报错信息提示Person类中没有发现无参构造方法，无法使用newInstance()方法实例化Person对象。因此，在使用Class类实例化其他类对象时一定要在其他类中编写无参构造方法。

案例二运行结果

9.3.1  通过无参构造方法实例化对象

# 9.3.2  通过有参构造方法实例化对象

先定一个小目标！

# 9.3.2  通过有参构造方法实例化对象

通过有参构造方法实例化对象的操作步骤如下: 

(1)通过调用Class类中的getConstructors()方法获取要实例化的类中的全部构造方法。

(2)获取实例化使用的有参构造方法对应的Constructor对象。

(3)通过 Constructor类实例化对象。

# 9.3.2  通过有参构造方法实例化对象

Constructor类用于存储要实例化化的类的构造方法，Constructor类的常用方法如下所示。

| 方法 | 描述 |
|---|---|
| getModifiers() | 获取构造方法的修饰符 |
| getName() | 获取构造方法的名称 |
| getParameterTypes() | 获取构造方法中参数的类型 |
| toString() | 返回此构造方法的信息 |
| newInstance(Object...initargs) | 通过该构造方法的指定参数列表创建一个该类的对象，如果未设置参数则表示采用默认无参的构造方法 |

# 9.3.2  通过有参构造方法实例化对象

class Example04 {
  public static void main(String args[]){
      Class<?> c = null; 
     try{
          c = Class.forName("com.itheima.Person");    //实例化对象c
      }catch(ClassNotFoundException e){
         e.printStackTrace();
      }
     Person per = null;
     Constructor<?> cons[] = null;		//声明Constructor类对象数组cons
     cons = c.getConstructors();		//获取Person类的全部构造方法
      try{
        per = (Person)cons[0].newInstance("张三",30); //实例化Person对象per
      }catch (Exception e){
         e.printStackTrace();
      }
     System.out.println(per);
  }
}

演示通过有参构造方法时实例化对象

# 9.3.2  通过有参构造方法实例化对象

运行代码，控制台显示的运行结果如下图所示。

运行结果

# 通过反射获取类结构

9.4

# 9.4  通过反射获取类结构

在实际开发中，通过反射可以得到一个类的完整结构，包括类的构造方法、类的属性、类的方法。
通过反射获取类结构需要使用到java.lang.reflect包中的以下3个类。
（1）Constructor：用于获取类中的构造方法。
（2）Field：用于获取类中的属性。
（3）Method：用于获取类中的方法

# 9.4  通过反射获取类结构

Constructor类、Field类和Method类都是AccessibleObject类的子类，AccessibleObject类的继承关系如下图所示。

# 9.4.1  获取类所实现的全部接口

先定一个小目标！

# getInterfaces()方法声明格式

要获取一个类所实现的全部接口，可以调用Class类中的getInterfaces()方法。getInterfaces()方法声明格式如下所示：

9.4.1  获取类所实现的全部接口

public Class[] getInterfaces();

getInterfaces()方法返回一个Class类的对象数组，数组中存储的是类所实现的接口。使用对象数组中的元素（接口）调用Class类中的getName()方法可以获取接口的名称。

# 9.4.1  获取类所实现的全部接口

案例演示getInterfaces()方法获取类所实现的全部接口

下面通过一个案例讲解通过getInterfaces()方法获取一个类所实现的全部接口，具体步骤如下。

# 9.4.1  获取类所实现的全部接口

interface China{
   public static final String NATION = "CHINA";
   public static final String AUTHOR = "张三";
}
class Person implements China{
    private String name;
    private int age;
    public Person(String name,int age){
         this.setName(name);
         this.setAge(age);
    }
    //省略定义getter/setter方法和toString()方法的代码
}

步骤一：定义接口China，声明两个字符串常量NATION和AUTHOR，然后定义Person类实现接口China，在类中声明name和age属性并编写属性的getter和setter方法及toString()方法，定义有参构造方法。代码如下所示：

# 9.4.1  获取类所实现的全部接口

public class Example05 {
       public static void main(String args[]){
     	Class<?> c = null;
  	try{
   		c = Class.forName("com.itheima.Person");
 	 }catch(ClassNotFoundException e){
    		e.printStackTrace();
	}
	Class<?> cons[] = c.getInterfaces();
	for (int i = 0;i < cons.length; i++){
    	        System.out.println("实现的接口名称："+ cons[i].getName());
 	}
       }
}

步骤二：定义main()方法，以Class数组的形式将全部的接口对象返回，并利用循环的方式将数组的内容依次输出，代码如下所示：

# 运行代码，控制台显示的运行结果如下图所示。

案例运行结果

9.4.1  获取类所实现的全部接口

# 9.4.2  获取父类

先定一个小目标！

# getSuperClass()方法声明格式

如果要获取一个类的父类，可以调用Class类中的getSuperClass()方法。getSuperClass()方法声明格式如下：

9.4.2  获取父类

public Class<? Super T> getSuperClass();

getSuperClass()方法返回一个Class类的实例，通过该实例调用Class类中的getName()方法可以获取类的名称。

# 9.4.2  获取父类

案例演示getSuperClass()方法获取父类

下面通过一个案例讲解调用getSuperClass()方法获取一个类的父类。具体步骤如下。

# 9.4.2  获取父类

class Person {
    private String name;
    private int age;
    public Person(String name,int age){
         this.setName(name);
         this.setAge(age);
    }
  public String toString() {
       return "姓名："+this.name+",年龄："+this.age;
  }
  ......//省略Person类的getter/setter方法
}

步骤一：定义Person类，在类中定义属性和构造方法，属性的getter/setter方法，toString()方法。代码如下所示：

# 9.4.2  获取父类

public class Example06 {
     public static void main(String args[]){
          Class<?> c1 = null;                                 //声明Class对象
          try{
                 c1 = Class.forName("com.itheima.Person");    //实例化Class对象
          }catch(ClassNotFoundException e){
                e.printStackTrace();
          }
          Class<?> c2 = c1.getSuperclass();                //取得Person类的父类
          System.out.println("父类名称："+ c2.getName());
     }
}

步骤二：定义main()方法，声明从class对象并实例化，使用getSuperclass()方法取得Person类的父类。代码如下所示：

# 运行代码，控制台显示的运行结果如下图所示。

案例运行结果

9.4.2  获取父类

由图可知，Person类在编写时没有显式地继承一个父类，所以会默认继承Object类。

# 9.4.3  获取全部构造方法

先定一个小目标！

# 获取构造方法

类的构造方法的获取在9.3.2节已经讲解，获取类的构造方法需要调用Class类的getConstructors()方法。调用getConstructors()方法获取的构造方法需要存储到Constructor类型的数组当中。通过调用Constructor类的方法可以获取构造方法的详细信息，如构造方法的权限、名称、参数信息等。

9.4.3  获取全部构造方法

# 9.4.3  获取全部构造方法

案例演示getConstructors()方法获取全部构造方法

下面演示通过getConstructors()方法获取全部构造方法，然后存储到Constructor类型的数组当中的过程。具体步骤如下。

# 9.4.3  获取全部构造方法

步骤一：定义Person类，声明属性name和age，定义无参构造方法、有一个参数name的构造方法、有两个参数的构造方法，为属性定义getter/setter方法，定义toString()方法。这部分代码比较简单，此处省略不写，可以根据描述信息自行编写代码，或者参考教材案例文件9-7。

# 9.4.3  获取全部构造方法

Class<?> c1 = null;                                //声明Class对象c1
        try{
           c1 = Class.forName("com.itheima.Person");   //实例化c1
        }catch(ClassNotFoundException e){e.printStackTrace();}
        Constructor<?> con[]  = c1.getConstructors();//获取全部构造方法，存到Constructor类数组中
        for (int i = 0;i < con.length;i++){             //循环打印构造方法信息
            Class<?> p[] = con[i].getParameterTypes();//获取构造方法详细信息并输出
            System.out.print("构造方法：");
            System.out.print(con[i].getModifiers()+" "); //获取构造方法权限
            System.out.print(con[i].getName());           //获取构造方法名称
            System.out.print("（");
            for (int j = 0;j < p.length; j++){//打印构造方法参数信息			  
                System.out.print(p[j].getName()+ " arg" +i);
                if (j < p.length-1){
                    System.out.print(",");
                }
            }
            System.out.println("）{}");
        }

步骤二：定义main()方法，代码如下所示：

# 运行代码，控制台显示的运行结果如下图所示。

案例运行结果

9.4.3  获取全部构造方法

# 9.4.3  获取全部构造方法

案例运行结果分析

由上图可知，控制台输出了Person类的所有构造方法名称及参数信息，在获取构造方法权限时可以发现，getModifiers()方法返回的是一个数字1而不是public，这是因为Java源码中方法的权限修饰符是使用数字标识的，如果要把表示权限的数字转换成用户可以看懂的关键字，则需要调用java.lang.reflect包中Modifier类的toString()方法。调用Modifier类的toString()方法将数字还原成权限修饰符。

# 9.4.3  获取全部构造方法

调用Modifier类的toString()方法

调用Modifier类的toString()方法将数字还原成权限修饰符，只需要将案例中的这行代码System.out.print(con[i].getModifiers()+" "); 替换成如下代码：

int mo = con[i].getModifiers();
System.out.print(Modifier.toString(mo) + " ");

代码替换后，再次运行程序。查看结果。

# 运行代码，控制台显示的运行结果如下图所示。

案例运行结果

9.4.3  获取全部构造方法

由图可知，使用Modifier类将权限修饰符从数字1还原成了关键字public。

# 9.4.4  获取全部方法

先定一个小目标！

# getMethods()方法

如果要获取类中的所有public修饰的成员方法对象，那么可以使用Class类中的getMethods()方法，该方法返回一个Method类的对象数组。如果想要进一步获取方法的具体信息，如方法的参数、抛出的异常声明等，可以调用Method类提供的一系列方法。

9.4.4  获取全部方法

# Method类的常用方法

9.4.4  获取全部方法

| 方法 | 描述 |
|---|---|
| getModifiers() | 获取方法的权限修饰符 |
| getName() | 获取方法的名称 |
| getParameterTypes() | 获取方法的全部参数的类型 |
| getReturnType() | 获取方法的返回值类型 |
| getExceptionType() | 获取方法抛出的全部异常 |
| newInstance(Object...initargs) | 通过反射调用类中的方法 |

# 9.4.4  获取全部方法

案例演示

演示类的全部方法的获取。定义main()方法，省略Person类的定义，完整代码可参考教材案例文件9-8，具体代码如下所示。

Class<?> c = null;                               //声明Class对象c
try{
            c = Class.forName("com.itheima.Person"); //实例化Class对象c
}catch(ClassNotFoundException e){
            e.printStackTrace();
}
Method m[] = c.getMethods();    //获取全部方法，存储到Method类数组对象m中
for (int i = 0;i < m.length; i++){        //遍历数组m循环输出方法信息
           Class<?> r = m[i].getReturnType();    //获取方法的返回值类型
           Class<?> p[] = m[i].getParameterTypes(); //获取全部的参数类型
           int xx = m[i].getModifiers();                //获取方法的权限修饰符
           System.out.print(Modifier.toString(xx)+" ");  //还原修饰符
           System.out.print(r.getName()+" ");           //获取方法名称
           System.out.print(m[i].getName());            
           System.out.print("(");
           ......//省略循环输出方法的参数
           Class<?> ex[] = m[i].getExceptionTypes();             //获取方法抛出的全部异常
           ......//省略判断是否有异常，输出异常信息   参考教材案例文件9-8 
}

# 9.4.4  获取全部方法

运行代码，控制台显示的运行结果如下图所示。

案例运行结果

由图可知，控制台不仅将Person类的方法输出，也将从Object类中继承而来的方法进行了输出。

# 9.4.5  获取全部属性

先定一个小目标！

# 9.4.5  获取全部属性

获取类的全部属性的两种方式

（1）获取本类中，以及实现的接口或继承的父类中的公共属性，需要调用getFields()方法。getFields()方法声明如下所示：

public Field[] getFields() throws SecurityException;

通过反射也可以获取一个类中的全部属性，类中的属性包括两部分，从父类继承的属性和本类定义的属性。

# 9.4.5  获取全部属性

（2）获取本类中的全部属性，需要调用getDeclaredFields()方法。getDeclareFields()方法声明如下所示：

public Field[] getDeclaredFields throws SecurityException;

上述两个方法返回的都是Field数组，Field数组中的每一个Field对象表示类中的一个属性。如果要获取属性的详细信息，就需要调用Field类提供的一系列方法。

# 9.4.5  获取全部属性

Field类的常用方法

| 方法 | 描述 |
|---|---|
| getModifiers() | 获取属性的权限修饰符 |
| getName() | 获取属性的名称 |
| isAccessible() | 判断属性是否可被外部访问 |
| setAccessible(Boolean flag) | 设置属性是否可被外部访问 |
| toString() | 返回Filed类的信息 |
| get(Object obj) | 获取参数对象中属性的具体内容 |
| set(Object obj, Object value) | 设置指定对象中属性的具体内容 |

# 9.4.5  获取全部属性

案例演示

案例讲解如何获取一个类中的全部属性信息。定义main()方法，省略Person类的定义，完整代码可参考教材案例文件9-9，具体代码如下所示。

Class<?> c1 = null;                               //声明Class对象c
try{
            c1 = Class.forName("com.itheima.Person"); //实例化Class对象c
}catch(ClassNotFoundException e){
            e.printStackTrace();
}
//获取本类属性，存储到Field类数组f当中
Field f[] = c1.getDeclaredFields();  
for (int i = 0;i<f.length;i++){            //循环输出属性信息
                Class<?> r = f[i].getType();           //获取属性的类型
                int mo = f[i].getModifiers();          //获取属性权限修饰符
                String priv = Modifier.toString(mo);  //转换属性的权限修饰符
                System.out.print("本类属性：");
                System.out.print(priv+" ");             //输出属性权限修饰符
                System.out.print(r.getName()+" ");     //输出属性类型
                System.out.print(f[i].getName());      //输出属性名称
                System.out.println(";");
}

# 9.4.5  获取全部属性

运行代码，控制台显示的运行结果如下图所示。

案例运行结果

# 9.4.6  通过反射调用类中的方法

先定一个小目标！

# 9.4.6  通过反射调用类中的方法

反射调用类中的方法时操作步骤

通过反射调用类中的方法时，需要使用Method类完成，具体操作步骤如下。
（1）通过调用Class类的getMethod()方法获取一个Method类的对象。调用getMethod()方法时需要传入方法名作为参数。
（2）通过获取的Method对象调用invoke()方法，执行目标方法。调用invoke()方法时，需要传递Class对象的实例作为参数。

# 9.4.6  通过反射调用类中的方法

案例演示

下面通过一个案例讲解通过反射调用类中的方法。定义main()方法，省略Person类的定义，完整代码可参考教材案例文件9-10，具体代码如下所示。

public class Example10 {
    public static void main(String args[]){
        Class<?> c = null;
        try{
            c = Class.forName("com.itheima.Person");
        }catch(ClassNotFoundException e){
            e.printStackTrace();
        }
        try{
            Method met = c.getMethod("sayHello");
            met.invoke(c.newInstance());
        }catch(Exception e){
            e.printStackTrace();
        }
    }
}

# 9.4.6  通过反射调用类中的方法

运行代码，控制台显示的运行结果如下图所示。

案例运行结果

# 反射的应用

9.5

# 9.5.1  通过反射调用类中的getter/setter方法

先定一个小目标！

# 9.5.1  通过反射调用类中的getter/setter方法

从面向对象部分读者就了解到类中的属性必须封装，封装之后的属性要通过setter方法设置属性值，通过getter方法获取属性值，那么在使用反射调用类中方法的操作中，最重要的是调用类中的setter方法及getter方法。
       getter/setter方法的调用过程与9.4.6节中类方法的调用过程类似，但因为getter/setter方法需要访问属性，所以稍显复杂。

# 9.5.1  通过反射调用类中的getter/setter方法

案例演示通过反射调用类中的setter方法及getter方法

下面通过一个案例讲解使用反射调用类中的setter方法及getter方法。具体步骤如下。

# 9.5.1  通过反射调用类中的getter/setter方法

步骤一：定义Person类，声明属性name和age，定义无参构造方法、有一个参数name的构造方法、有两个参数的构造方法，为属性定义getter/setter方法，定义toString()方法。这部分代码比较简单，此处省略不写，可以根据描述信息自行编写代码，或参考教材案例文件9-11。

# 9.5.1  通过反射调用类中的getter/setter方法

public static String initStr(String old){
        String str= old.substring(0,1).toUpperCase()+old.substring(1);
        return str;
    }

步骤二：定义initStr()方法，通过此方法将字符串中的首字母转换成大写，并在首字母转换成大写之后，将字符串连接到set字符串及get字符串之后找到对应的方法。代码如下所示：

# 9.5.1  通过反射调用类中的getter/setter方法

public static void setter(Object obj,String att,Object value,Class<?> type){
        try {
         Method met= obj.getClass().getMethod("set"+initStr(att),type);
         met.invoke(obj,value);
        }catch(Exception e){
            e.printStackTrace();
        }
    }
public static void getter(Object obj,String att){
        try {
            Method met= obj.getClass().getMethod("get"+initStr(att));
            System.out.println(met.invoke(obj));
        }catch(Exception e){
            e.printStackTrace();
        }
}

步骤三：定义setter()方法和getter()方法，代码如下所示：

# 9.5.1  通过反射调用类中的getter/setter方法

public static void main(String args[]){
        Class<?> c = null;
        Object obj = null;
        try{
            c = Class.forName("com.itheima.Person");	//对象c为Class类型
            obj = c.newInstance();	                    //实例化Class对象
        }catch(Exception e){
            e.printStackTrace();
        }
        setter(obj,"name","张三",String.class);
        setter(obj,"age",18,int.class);
        System.out.print("姓名：");
        getter(obj,"name");
        System.out.print("年龄：");
        getter(obj,"age");
}

步骤四：定义main()方法，代码如下所示：

# 9.5.1  通过反射调用类中的getter/setter方法

运行代码，控制台显示的运行结果如下图所示。

案例运行结果

# 9.5.2  通过反射操作属性

先定一个小目标！

# 9.5.2  通过反射操作属性

在反射操作中，虽然可以通过调用类中的getter/setter方法访问类的属性，但是这样操作起来太过繁琐。除了调用getter/setter方法访问类的属性之外，反射机制也可以直接通过Field类操作类中的属性，通过Field类提供的set()方法和get()方法可以直接设置、获取类的属性值。
       通过调用Field类的getter/setter方法访问类的属性时，首先要调用Field类中的setAccessible()方法将需要操作的属性权限设置成可以被外部访问。

# 9.5.2  通过反射操作属性

案例演示

讲解如何使用反射直接操作类的属性。定义main()方法，省略Person类的定义，完整代码可参考教材案例文件9-12，具体代码如下所示。

public static void main(String args[]) throws Exception{
        Class<?> c = null;                             //声明一个Class对象
        Object obj = null;                             //声明一个Object对象
        c = Class.forName("com.itheima.Person");   //实例化Class对象
        obj = c.newInstance();                         //实例化Object对象
        Field nameField = null;                        //表示name属性
        Field ageField = null;                         //表示age属性
        nameField = c.getDeclaredField("name");     //获取name属性
        ageField = c.getDeclaredField("age");        //获取age属性
        nameField.setAccessible(true);       //将name属性设置为可被外部访问
        nameField.set(obj,"张三");             //设置name属性值
        ageField.setAccessible(true);         //将age属性设置为可被外部访问
        ageField.set(obj,30);                   //设置age属性值
        System.out.println("姓名："+nameField.get(obj));
        System.out.println("年龄："+ageField.get(obj));
}

# 9.5.2  通过反射操作属性

注意：以上程序是扩大类属性的访问权限后直接进行了属性的操作，所以在Person类中并不需要编写getter方法和setter方法，但是在实际开发中，这种直接操作属性的方式是不安全的，读者在以后的开发中，不要直接操作属性，而是要通过setter方法和getter方法操作属性，本案例只是演示通过反射可以直接访问类中的属性。

# 9.5.2  通过反射操作属性

运行代码，控制台显示的运行结果如下图所示。

案例运行结果

# 本章小结

本章主要介绍了Java的反射机制。首先介绍了反射机制原理；然后带领读者认识了Class类；接着通过案例介绍了Class类的使用，包括通过无参构造方法实例化对象和通过有参构造方法实例化对象；接下来介绍了通过反射获取类结构，包括获取接口、获取父类、获取构造方法，获取全部方法、获取全部属性和通过反射调用类中的方法；最后讲解了反射的应用，包括通过反射调用类中的setter、getter方法和通过反射操作类中的属性。通过本章的学习，读者对Java的反射会有一定的了解，掌握好这些知识，对以后的实际开发大有裨益。

本

章

小

结
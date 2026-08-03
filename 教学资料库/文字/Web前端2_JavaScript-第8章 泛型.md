# 第8章  泛型

Java基础入门（第3版）

# 学习目标/Target

# 章节概述/ Summary

通过之前的学习，读者可以了解到，把一个对象存入集合后，再次取出该对象时，该对象的编译类型就变成了Object类型(尽管其在运行时类型没有改变)。集合设计成这样，提高了它的通用性，但是也带来了一些类型不安全和繁琐的问题，例如，集合可以同时存储任何类型的对象，通常对取出之后的对象都需要强制类型转换，而且如果不知道实际参数类型的情况，也无法进行强制类型转换。为了解决这些问题，从JDK 5版本开始引入了泛型，本章将围绕泛型的相关内容进行讲解。

# 目录/Contents

# 泛型基础

8.1

# 8.1.1  泛型概述

先定一个小目标！

# 8.1.1  泛型概述

泛型是在JDK 5中引入的一个新特性，其本质是参数化类型，也就是将具体的类型形参化，参数化的类型（可以称之为类型形参）在使用或者调用时传入具体的类型（类型实参），类似于调用方法时传入实参才确定方法形参的具体值。泛型的声明由一对尖括号和类型形参组成，类型形参定义在尖括号中间，定义类、接口和方法时使用泛型声明，定义出的类、接口和方法分别称为泛型类、泛型接口和泛型方法。

泛型的概念

# 8.1.1  泛型概述

泛型的定义

使用泛型编程，会在使用或者调用时传入具体的类型时才确定最终的数据类型，所以集合需要存储什么类型的数据，在创建集合时传入对应的类型即可。
定义泛型时类型形参由一对尖括号（<>）包含在中间，使用或者调用泛型时，需要将类型实参写在尖括号（<>）之间。
JDK 5之后的类库中很多重要的类和接口都引入了泛型，例如集合体系中的类和接口。下面分别演示未引入泛型和使用泛型编程的区别，体验泛型具体有什么好处。

# 8.1.1  泛型概述

案例一演示

未引入泛型之前，如果想要创建一个只保存Integer类型的List集合。具体代码如下所示。

public class Example01{
    public static void main(String[] args) {
        // 创建一个只保存Integer类型的List集合
        List intList = new ArrayList();
        intList.add(1);
        intList.add(2);
        //因为失误存放了Integer类型之外的字符串数据
        intList.add("3");
        for (int i = 0; i < intList.size(); i++) {
            /*因为List里面默认取出的全部Object对象，所以使用之前需要进行强
            * 制类型转换。集合内最后一个元素进行转换时候将出现类型转换异常
            * */
            Integer num=(Integer)intList.get(i);
        }
    }
}

# 8.1.1  泛型概述

案例一代码分析

在案例一的代码中，第4行代码想创建一个只保存Integer类型的List集合，第5~8行代码往集合中存放数据，由于存放数据时并没有出现编译异常，操作者认为存入的数据类型都符合要求，但是在执行第13行代码时却会出现异常。因为在第8行代码中存放了Integer类型之外的字符串数据。接下来使用泛型优化案例一代码。

# 8.1.1  泛型概述

案例二演示

下面使用泛型优化案例一。具体代码如下所示。

public class Example03 {
    public static void main(String[] args) {
        // 创建一个只保存Integer类型的List集合
        List<Integer> intList = new ArrayList<Integer>();
        intList.add(1);
        intList.add(2);
        //下面代码将出现编译时异常
        intList.add("3");
        for (int i = 0; i < intList.size(); i++) {
            //下面的代码无需强制类型转换
            Integer num=intList.get(i);
        }
    }
}

# 8.1.1  泛型概述

案二例代码分析

在案例二的代码中，List<Integer>指定创建的集合intList的类型形参为Integer，也就是创建后的intList集合中只能保存Integer类型的元素；第11行代码不用进行强制类型转换，因为此时intList集合会记住集合内所有元素都是Integer类型。如果需要创建一个只保存String类型的List集合时，只需在创建集合时，使用<String>的类型形参替换<Integer>即可。

# 8.1.2  使用泛型的好处

先定一个小目标！

# 8.1.2  使用泛型的好处

使用泛型的好处

（1）提高类型的安全性
使用泛型后，将类型的检查从运行期提前到编译期，编译期的类型检查，可以更早、更容易的找出因为类型限制而导致的类型转换异常，从而提高程序的可靠性。
（2）消除强制类型转换
使用泛型后，程序会记住当前的类型形参，从而无需对传入的实参值进行强制类型转换。使得代码更加清晰和筒洁，可读性更高。

# 8.1.2  使用泛型的好处

使用泛型的好处

（3）提高代码复用性
使用泛型后，可以更好的将程序中通用的代码提取出来，在使用时传入不同类型的参数，避免了多次编写相同功能的代码，以提高代码的复用性。
（4）拥有更高的运行效率
使用泛型之前，传入的实际参数值作为Object类型传递时，需要进行封箱和拆箱操作，会消耗程序的一定的开销。使用泛型后，类型形参中都需要使用引用数据类型，即传入的实际参数的类型都是对应引用数据类型，避免了封箱和拆箱操作，降低了程序运行的开销，提高了程序运行的效率。

# 泛型类

8.2

# 8.2  泛型类

先定一个小目标！

# 泛型类的语法格式

8.2  泛型类

定义类时，在类名后加上尖括号包含类型形参，定义的这个类就是泛型类。创建泛型类的实例对象时传入不同的类型实参，从而可以动态生成无数个该泛型类的子类。在JDK类包中泛型类的最典型应用就是各种容器类，如ArrayList、HashMap等。定义泛型类的格式具体如下。

[访问权限] class 类名<类型形参变量1，类型形参变量2，…，类型形参变量n>{
    …
}

# 泛型类的语法格式分析

8.2  泛型类

上述语法格式中，类名<类型形参变量>是一个整体的数据类型，通常称为泛型类型；类型形参变量，没有特定的意义，可以是任意一个字母，但是为了提高可读性，建议使用有意义的字母。一般情况下使用较多的字母及意义如下所示。
 E：表示Element（元素），常用在java Collection里使用，如	List<E>,Iterator<E>,Set<E>。
 K，V：表示Key，Value（Map的键值对）。
 N：表示Number（数字）。
 T：表示Type（类型），如String，Integer等。

# 泛型类的定义与创建

8.2  泛型类

定义：定义泛型类时，类的构造方法名称还是类的名称，类型形参变量可以用于属性的类型、方法的返回值类型和方法的参数类型。
创建：创建泛型类的对象时，不强制要求传入类型实参，如果传入类型实参，类型形参会根据传入的类型实参做相应的限制，此时泛型才会起到本应起到的限制作用。如果不传入类型实参的话，在泛型类中使用类型形参的方法或成员变量定义的类型可以为任何的类型。

# 8.2  泛型类

案例演示泛型的使用

下面通过自定义一个泛型类，演示泛型的使用。具体步骤如下。

# 8.2  泛型类

// 定义泛型类Goods
class Goods<T> {
      // 类型形参变量作用于属性的类型
      private T info ;
      // 类型形参变量作用于构造方法的参数类型
      public Goods(T info) {
          this.info = info;
      }
      // 类型形参变量作用于方法的参数类型
      public void setInfo(T info){
          this.info = info ;
      }
      // 类型形参变量作用于方法的返回值类型
      public T getInfo(){
          return this.info ;
      }
}

步骤一：定义泛型类Goods，声明私有变量info，定义构造方法，与getter/setter方法。代码如下所示：

# 8.2  泛型类

public class Example04 {
    public static void main(String[] args) {
        // 创建Godds对象
        Goods goods = new Goods<Integer>(666);
        System.out.println(goods.getInfo()+"..."+goods.getInfo().getClass());
        goods.setInfo("热卖商品");
        System.out.println(goods.getInfo()+"..."+goods.getInfo().getClass());
    }
}

步骤二：定义main()方法，创建Godds对象，分别调用setInfo()方法和getInfo()方法。代码如下所示：

# 案例运行结果

8.2  泛型类

运行代码，控制台显示的运行结果如下图所示。

# 案例运行结果分析

从上图可以看出，控制台打印了2行信息，分别打印“666...class java.lang.Integer”和“热卖商品...class java.lang.String”，可以得出，执行文件8-4中的第22行代码时，属性info的值为666，类型为Integer；执行文件8-4中的第24行代码时，属性info的值为热卖商品，类型为String。说明类型形参会根据类型实参进行确定。

8.2  泛型类

# 泛型接口

8.3

# 8.3  泛型接口

先定一个小目标！

# 泛型接口的语法格式

8.3  泛型接口

定义泛型接口和定义泛型类的语法格式类似，在接口名称后面加上尖括号包含类型形参即可。集合相关的接口中很多接口也都是泛型接口，如Collection、List等。定义泛型接口的基本语法格式如下所示：

[访问权限] interface 接口名称<类型形参变量>{}

# 1．使用非泛型类实现泛型接口

当使用非泛型类实现接口时，需要明确接口的泛型类型，也就是需要将类型实参传入到接口中。此时实现类重写接口中使用泛型的地方，都需要将类型形参替换成传入的类型实参，这样可以直接使用泛型接口的类型实参，具体代码如下所示。

8.3  泛型接口

步骤一：定义一个泛型接口。

public interface Inter<T> {
        public abstract void show(T t);
}

# 8.3  泛型接口

步骤二：定义泛型接口的实现类，在泛型接口后指定类型实参以明确接口的泛型类型。

public class InterImpl implements Inter<String> {
    @Override
    public void show(String s) {
        System.out.println(s);
    }
}

步骤三：定义测试类，创建Inter对象时，传入的类型实参必须是String类型，否则编译异常。

public class Example05{
      public static void main(String[] args) {
          Inter<String> inter = new InterImpl();
          inter.show("hello");//传入的参数必须是String类型
      }
}

# 8.3  泛型接口

步骤四：运行代码，控制台显示的运行结果如下图所示。

# 2．使用泛型类实现泛型接口

8.3  泛型接口

当使用泛型类实现泛型接口时，需要将泛型的声明加在实现类中，并且泛型类和泛型接口使用的都是同一个类型形参变量，否则会出现编译异常。具体代码如下所示。

步骤一：定义泛型接口的实现类，使用泛型类实现泛型接口。

public class InterImpl<T> implements Inter<T> {
    @Override
    public void show(T t) {
        System.out.println(t);
    }
}

# 8.3  泛型接口

步骤二：重新定义测试类，创建Inter对象时，传入不同的类型实参，并分别调用show()方法进行输出验证。

public class Example06 {
    public static void main(String[] args) {
        Inter<String> inter = new InterImpl();
        inter.show("hello");
        Inter<Integer> ii = new InterImpl<>();
        ii.show(12);
    }
}

# 8.3  泛型接口

步骤三：运行代码，控制台显示的运行结果如下图所示。

从上图可以看出，分别在控制台打印hello和12，说明和使用非泛型类实现接口相比，使用泛型类实现接口创建对象时，类型实参可以为任意类型。

# 泛型方法

8.4

# 8.4.1  泛型方法的概述

先定一个小目标！

# 定义泛型方法的语法格式

泛型方法是将类型形参的声明放在修饰符和返回类型之间的方法。在Java程序中，定义泛型方法常用的格式如下所示：

8.4.1  泛型方法的概述

[访问权限修饰符] [static] [final] <类型形参> 返回值类型 方法名 （形式参数列表）{}

# 定义泛型方法注意事项

（1）访问权限修饰符(包括private、public、protected)、static和 final都必须写在类型形参列表的前面。
（2）返回值类型必须写在类型形参列表的后面。
（3）泛型方法可以在泛型类中，也可以在普通类中。

8.4.1  泛型方法的概述

# 定义泛型方法注意事项

（4）泛型类中的任何方法本质上都是泛型方法，所以在实际使用中很少会在泛型类中再用上面的形式来定义泛型方法。
（5）类型形参可以用在方法体中修饰局部变量，也可以修饰方法的返回值。
（6）泛型方法可以是实例方法（没有用static修饰，也叫非静态方法）也可以是静态方法。

8.4.1  泛型方法的概述

# 8.4.2  泛型方法的应用

先定一个小目标！

# 8.4.2  泛型方法的应用

泛型方法的两种使用方式

方式一如下：

对象名|类名.<类型实参>方法名（类型实参列表）;

方式二如下：

对象名|类名.方法名（类型实参列表）;

# 两种调用泛型方法的差别

如果泛型方法是实例方法，则需要使用对象名进行调用；如果泛型方法是静态方法，可以使用类名进行调用。
两种调用泛型方法的差别在于，方法名之前是否显式地指定了类型实参。调用时是否需要显式地指定了类型实参，要根据泛型方法的声明形式，以及调用时编译器能否从实际参数表中获得足够的类型信息决定，如果编译器能够根据实际参数推断出参数类型，就可以不指定类型实参，反之则需要指定类型实参。

8.4.2  泛型方法的应用

# 8.4.2  泛型方法的应用

案例演示泛型方法的定义与使用

下面通过一个案例，演示泛型方法的定义与使用。具体步骤如下。

# 8.4.2  泛型方法的应用

案例演示

下面通过一个案例，演示泛型方法的定义与使用。具体代码如下所示。

class Student {
    // 静态泛型方法
    public static <T> void staticMethod(T t) {
        System.out.println(t + "..." + t.getClass());
    }
    // 普通泛型方法
    public <T> void otherMethod(T t) {
        System.out.println(t + "..." + t.getClass());
    }
}

步骤一：定义Student类，在类中定义一个静态泛型方法和一个普通泛型方法。代码如下所示：

# 8.4.2  泛型方法的应用

public class Example07 {
	public static void main(String[] args) {
        // 使用方式一调用静态的泛型方法
        Student.staticMethod("staticMethod");
        // 使用方式二调用静态的泛型方法
        Student.<String>staticMethod("staticMethod");
        Student stu = new Student();
        // 使用方式一调用普通的泛型方法
        stu.otherMethod(666);
       // 使用方式二调用普通的泛型方法
        stu.<Integer>otherMethod(666);
}
}

步骤二：定义main()方法，调用方法测试结果。代码如下所示：

# 8.4.2  泛型方法的应用

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 8.4.2  泛型方法的应用

案例运行结果分析

从运行结果图可以得出，案例中第14行代码和第16行代码执行结果一样，第19行代码和第21行代码执行结果一样。说明泛型方法可以在非泛型类中定义，并且在调用泛型方法的时候确定泛型的具体类型 。上述结果中虽然使用方式一和方式二的输出结果一致，但是方式一隐式的传入类型实参，不能直观的查看到调用的方法是泛型方法，不利于代码的阅读和维护，通常建议使用第二种方式调用泛型方法。

# 类型通配符

8.5

# 8.5.1  类型通配符的概述

先定一个小目标！

# 类型通配符表示方式

8.5.1  类型通配符的概述

类型通配符使用一个问号（?）表示，类型通配符可以匹配任何类型的类型实参。

# 8.5.1  类型通配符的概述

案例演示通配符的使用

下面使用一个案例演示类型通配符的使用。具体步骤如下。

# 8.5.1  类型通配符的概述

// 定义泛型类Person
class Person<T> {
            private T info;
            public Person(T info) {
this.info = info;
}
public T getInfo() {
  return info;
}
}

步骤一：定义泛型类Person，声明私有变量info，定义有参构造方法和getter方法。代码如下所示：

# 8.5.1  类型通配符的概述

public class Example08{
    public static void main(String[] args) {
        // 创建Person对象，传入String类型的类型实参
        Person<?> person = new Person<String>("M1");
        System.out.println( person.getInfo()+"..."+person.getInfo().getClass());
        // 创建Person对象，传入Integer类型的类型实参
        person=new Person<Integer>(666);
        System.out.println( person.getInfo()+"..."+person.getInfo().getClass());
    }
}

步骤二：定义main()方法，创建Person对象，分别传入String类型和Integer类型的类型实参，进行测试。代码如下所示：

# 8.5.1  类型通配符的概述

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

从图可以看出，控制台成功输出了2条信息。说明泛型类Person的对象接收了2种不同的类型实参。

# 8.5.1  类型通配符的概述

如果创建Person对象时，不使用类型通配符，而是使用指定的类型实参，会出现编译异常，具体如下图所示。

不使用通配符的情况一

# 8.5.1  类型通配符的概述

不使用通配符的情况二

使用Object代替类型通配符？接收所有的类型，也会出现编译异常，具体如下图所示。

会出现上图所示的编译异常，是因为泛型中，类名和泛型的声明是一个整体类型，Person<Object>并不是Person<String>的父类。

# 8.5.2  类型通配符的限定

先定一个小目标！

# 8.5.2  类型通配符的限定

1．设定类型通配符的上限

当使用Person<?>时，表示这个泛型Person可以接收所有类型的类型实参。但有时候不想让某个泛型类接收所有类型的类型实参，只想接收指定的类型及其子类，这个时候可以为类型通配符设定上限。设定类型通配符的上限的语法格式如下所示：

<? extends 类 >

# 8.5.2  类型通配符的限定

案例演示

下面根据上述语法格式，演示设定类型通配符的下限的使用。具体代码如下所示。

public class Example10{
// 设定类型通配符的下限，此时传入的类型实参，必须是Number类型或者Number类型的父类
public static void getElement(Collection<? super Number> coll){}   
public static void main(String[] args) {
        // 创建Collection对象，传入Number类型的类型实参
        Collection<Number> list1 = new ArrayList<Number>();
        // 创建Collection对象，传入Object类型的类型实参
        Collection<Object> list2 = new ArrayList<Object>();
        // 创建Collection对象，传入Integer类型的类型实参
        Collection<Integer> list3 = new ArrayList<Integer>();
        getElement(list1);
        getElement(list2);
        getElement(list3);
    }
}

# 8.5.2  类型通配符的限定

案例代码分析

定义方法getElement(),设定类型通配符的下限为Number，设定后调用该方法时传入的类型实参必须是Number类型或者是Number的父类；
创建3个Collection对象，分别传入了Number类型、Object类型和Integer类型的类型实参；
分别将创建的3个Collection对象作为参数调用getElement()方法，由于list3创建时传入的Integer类型不是Number的父类，出现编译异常。

# 8.5.2  类型通配符的限定

2．设定类型通配符的下限

设定类型通配符时，除了可以设定类型通配符的上限，也可以对类型通配符的下限进行设定。设定类型通配符的下限后，类型实参只能是设定的类型及其父类型，设定的语法格式如下所示：

<? super 类 >

# 8.5.2  类型通配符的限定

案例演示

下面根据上述语法格式，演示设定类型通配符的上限的使用。具体代码如下所示。

public class Example09 {
    // 设定类型通配符的上限，此时传入的类型实参必须是Number类型或者Number类型的子类
    public static void getElement(Collection<? extends Number> coll){}
    public static void main(String[] args) {
        // 创建Collection对象，传入Number类型的类型实参
        Collection<Number> list1 = new ArrayList<Number>();
        // 创建Collection对象，传入Integer类型的类型实参
        Collection<Integer> list2 = new ArrayList<Integer>();
        // 创建Collection对象，传入String类型的类型实参
        Collection<String> list3 = new ArrayList<String>();
        getElement(list1);
        getElement(list2);
        getElement(list3);
    }
}

# 8.5.2  类型通配符的限定

案例代码分析

定义方法getElement(),设定类型通配符的上限为Number，设定后调用该方法时传入的类型实参必须是Number类型或者是Number的子类；
创建3个Collection对象，分别传入了Number类型、Integer类型和String类型的类型实参；
然后分别将创建的3个Collection对象作为参数调用getElement()方法，由于list3创建时传入的String类型不是Number的子类，出现编译异常。

# 本章小结

本章主要介绍了泛型的相关知识。首先介绍了泛型的基础知识，包括了泛型概述、使用泛型的好处；其次介绍了泛型类，接着介绍了泛型接口；然后介绍了泛型方法，包括了泛型方法的定义和泛型方法的使用；最后介绍了泛型的类型通配符，包括类型通配符的概述和类型通配符的限定。通过本章的学习，读者应该对Java中的泛型有一定的了解。

本

章

小

结
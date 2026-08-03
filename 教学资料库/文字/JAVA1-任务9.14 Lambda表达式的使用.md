# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

创建一个整数类型的ArrayList集合并添加元素，使用Lambda表达式遍历该集合元素。

# ..

模块二 知识链接

Lambda 表达式概述

‌‌Lambda表达式常用的语法格式

# ‌‌‌Lambda 表达式概述

模块二 
知识链接

Lambda 表达式是JDK8的一个新特性，可以取代大部分的匿名内部类，写出更优雅的 Java代码，尤其在集合的遍历和其他集合操作中，可以极大地优化代码结构。JDK 也提供了大量的内置函数式接口供我们使用，使得Lambda表达式的运用更加方便、高效。

# ‌‌‌‌‌Lambda表达式常用的语法格式

模块二 
知识链接

Lambda表达式常用的语法格式如表9-10所示。

表9-10 Lambda表达式常用的语法格式

| 语法格式 | 描述 |
|---|---|
| （）->System.out.println（"Hello Lambda!"）; | 无参数，无返回值 |
| （x）->System.out.println（x） | 有一个参数，并且无返回值 |
| x->System.out.println（x） | 若只有一个参数，小括号可以省略不写 |
| Comparator<Integer>com=（x，y）->{
System.out.println（"函数式接口"）;
return Integer.compare（x，y）;}; | 有两个以上的参数，有返回值，并且Lambda方法体中有多条语句 |
| Comparator<Integer>com=（x，y）->Integer.compare（x， y）; | 若Lambda体中只有一条语句，return和大括号都可以省略不写 |
| （Integer x，Integer y）->Integer.compare（x，y）; | Lambda表达式的参数列表的数据类型可以省略不写，因为JVM编译器通过上下文推断出，数据类型，即“类型推断” |

# ，

过渡页

模块三  任务实现

创建一个整数类型的ArrayList集合并添加元素，使用Lambda表达式遍历该集合元素。

模块三 
任务实现

# 任务源码

根据任务描述以及Lambda表达式常用的语法格式知识点可以得到文件9-27所示的代码。

文件9-27 Example26.java

模块三 
任务实现

1import java.util.ArrayList;
2public class Example26 {
3  public static void main（String[] args） {
4    ArrayList<Integer> list=new ArrayList<>（）;
5    list.add（10）;
6    list.add（21）;
7    list.add（32）;
8    list.add（43）;
9    list.add（11）;

# 任务源码

根据任务描述以及Lambda表达式常用的语法格式知识点可以得到文件9-27所示的代码。

文件9-27 Example26.java

模块三 
任务实现

10   list.add（52）;
//通过lambda表达遍历集合
11  list.forEach（e->{
12      System.out.print（e+" "）;
13  }）;
14 }
15 }

# 运行结果

模块三 
任务实现

文件9-27的运行结果如图9-35所示。

图9-35 文件9-27的运行结果

# 感谢关注
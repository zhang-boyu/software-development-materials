# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务1：创建一个ArrayList集合，向该集合中添加字符串，利用Iterator接口遍历集合中的字符串。
子任务2：删除子任务1中集合的某一个字符串。

# ..

模块二 知识链接

集合的遍历

Iterator接口

Iterator对象遍历集合机制

# 集合的遍历

模块二 
知识链接

在实际开发中，经常需要按照某种次序对集合中的每个元素进行访问，并且仅访问一次，这种对集合的访问也称为集合的遍历。针对这种需求，JDK 提供了 Iteratc接口和foreach循环。

# Iterator接口

模块二 
知识链接

Iterator接口是Java集合框架中的一员，但它与Collection、Map接口有所不同，Collection接口与Map接口主要用于存储元素，而Iterator主要用于迭代访问（遍历）Collection中的元素，通常情况下Iterator对象也被称为迭代器。

# Iterator对象遍历集合机制

模块二 
知识链接

Iterator对象在遍历集合时，内部采用指针的方式来跟踪集合中的元素。Iterator集合中的元素的过程如图9-5所示，在调用Iterator 的 next( )方法之前，不指向任何元素；第一次调用Iterator的next( )方法时，当第二次调用next( )方法时，Iterator 的指针会指向第二个元素并将该元素返回;以此类推，直到hasNext方法返回false，表示已经遍历完集合中所有的元素，终止对元素的遍历。

# Iterator对象遍历集合机制

模块二 
知识链接

图9-5 迭代器迭代遍历集合中的元素过程

# ，

过渡页

模块三  任务实现

子任务1：创建一个ArrayList集合，向该集合中添加字符串，利用Iterator接口遍历集合中的字符串。
子任务2：删除子任务1中集合的某一个字符串。

模块三 
任务实现

# 任务源码

子任务1：结合任务描述和知识链接中使用Iterator接口知识点可以得到文件9-3所示的代码。               文件9-3  Example03.java

模块三 
任务实现

1import java.util.*;
2public class Example03 {
3 public static void main（String[] args） {
4   ArrayList list = new ArrayList（）; // 创建ArrayList集合
5   list.add（"张磊"）; // 向该集合中添加字符串
6   list.add（"李智"）;
7   list.add（"王芳"）;
8   list.add（"赵光"）;

# 任务源码

子任务1：结合任务描述和知识链接中使用Iterator接口知识点可以得到文件9-3所示的代码。               文件9-3  Example03.java

模块三 
任务实现

9   Iterator it = list.iterator（）; // 获取Iterator对象
10  while （it.hasNext（）） { // 判断ArrayList集合中是否存在下一个元素
11  Object obj = it.next（）; // 取出ArrayList集合中的元素
12  System.out.println（obj）;
13     }
14    }
15   }

# 运行结果

文件9-3的运行结果如图9-6所示。

模块三 
任务实现

图9-6 文件9-3运行结果

# 任务源码

子任务2：结合任务描述和知识链接中使用Iterator接口知识点可以得到文件9-4所示的代码。
                      文件9-4  Example04.java

模块三 
任务实现

1import java.util.*;
2public class Example03 {
3 public static void main（String[] args） {
4   ArrayList list = new ArrayList（）; // 创建ArrayList集合
5   list.add（"张磊"）; // 向该集合中添加字符串
6   list.add（"李智"）;
7   list.add（"王芳"）;
8   list.add（"赵光"）;
9   Iterator it = list.iterator（）; // 获取Iterator对象

# 任务源码

子任务2：结合任务描述和知识链接中使用Iterator接口知识点可以得到文件9-4所示的代码。
                      文件9-4  Example04.java

模块三 
任务实现

10  while （it.hasNext（）） { // 判断ArrayList集合中是否存在下一个元素
11  Object obj = it.next（）;
12  if （"李智".equals（obj）） {  // 判断该集合中的元素是否为李智
13     list.remove（obj）;  // 删除该集合中的元素
14     }
15     }
16    System.out.println（list）;
17    }
18  }

# 运行结果

文件9-4运行结果如图9-7所示。

模块三 
任务实现

图9-7 文件9-4的运行结果

# 感谢关注
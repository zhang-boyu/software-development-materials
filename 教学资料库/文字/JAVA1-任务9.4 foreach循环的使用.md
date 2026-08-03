# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务1：创建一个ArrayList集合，向该集合中添加字符串，使用foreach循环遍历该集合元素并输出。
子任务2：修改字符串数组strs中的所有元素为“gh”并输出。

# ..

模块二 知识链接

foreach循环

foreach循环其语法格式

foreach循环缺陷

# foreach循环

模块二 
知识链接

虽然 Iterator 可以用来遍历集合中的元素，但写法上比较烦琐，为了简化书写，从JDK5开始，提供了foreach循环，它是一种更加简洁的for 循环，主要用于遍历数组或集合中的元素，也称增强for循环。

# foreach循环其语法格式

模块二 
知识链接

for（容器中元素类型临时变量：容器变量）{
//执行语句
}
从上面的格式可以看出，与for循环相比，foreach循环不需要获得集合的长度，也不需
要根据索引访问容器中的元素，就能够自动遍历集合中的每个元素。

# foreach循环缺陷

模块二 
知识链接

foreach循环虽然书写起来很简洁，但在使用时也存在一定的局限性。当使用foreach循环遍历集合和数组时，只能访问集合中的元素，不能对其中的元素进行修改，具体见子任务2。

# ，

过渡页

模块三  任务实现

子任务1：创建一个ArrayList集合，向该集合中添加字符串，使用foreach循环遍历该集合元素并输出。
子任务2：修改字符串数组strs中的所有元素为“gh”并输出。

模块三 
任务实现

# 任务源码

子任务1：结合任务描述和知识链接中foreach循环知识点可以得到文件9-5所示的代码。

文件9-5 Example05.java

模块三 
任务实现

1import java.util.*;
2public class Example05 {
3	public staticvoidmain（String[] args） {
4	      ArrayList list = new ArrayList（）; // 创建ArrayList集合
5	list.add（"张华"）; // 向ArrayList集合中添加字符串元素
6	list.add（"李方"）;
7	list.add（"王磊"）;

# 任务源码

子任务1：结合任务描述和知识链接中foreach循环知识点可以得到文件9-5所示的代码。

文件9-5 Example05.java

模块三 
任务实现

8	for（Object obj : list）{	//使用foreach循环遍历ArrayList对象
9		  System.out.println（obj）;// 取出并打印ArrayList集合中的元素
10	      }
11   }
12 }

# 运行结果

文件9-5运行结果如图9-9所示。

模块三 
任务实现

图9-9 文件9-5的运行结果

# 任务源码

子任务2：结合任务描述和知识链接中foreach循环知识点可以得到文件9-6所示的代码。

文件9-6 Example06.java

模块三 
任务实现

1public class Example06 {
2  static String[] strs = { "ab"， "cd"， "ef" };
3  public static void main（String[] args） {
4      for （String str : strs） {// foreach循环遍历数组
5         str = "gh";
6      }
7   System.out.println（"foreach循环修改后的数组："+strs[0]+"，"+strs[1]+"，"+ strs[2]）;
8  }

# 运行结果

文件9-6运行结果如图9-10所示。

模块三 
任务实现

图9-10 文件9-6的运行结果

# 感谢关注
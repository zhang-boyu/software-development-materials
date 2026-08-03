# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

定义一个LinkedHashSet集合，向该集合插入4个字符串元素，使用Iterator接口遍历集合中的字符串元素。

# ..

模块二 知识链接

LinkedHashSet

# LinkedHashSet

模块二 
知识链接

类HashSet和 LinkedHashSet都是接口Set的实现，两者都不能保存重复的数据。
主要区别是HashSet不保证集合中元素的顺序，即不能保证迭代的顺序与插入的顺序一致。
而LinkedHashSet按照元素插入的顺序进行迭代，即迭代输出的顺序与插入的顺序保持一致。

# ，

过渡页

模块三  任务实现

定义一个LinkedHashSet集合，向该集合插入4个字符串元素，使用Iterator接口遍历集合中的字符串元素。

模块三 
任务实现

# 任务源码

结合任务描述和知识链接中接口的定义和实现方法相关知识点可以得到文件9-10所示的代码。

文件9-10 Example09.java

模块三 
任务实现

1import java.util.Iterator;
2import java.util.LinkedHashSet;
3public class Example09 {
4    public static void main（String[] args） {
5        LinkedHashSet set = new LinkedHashSet（）;  
6        set.add（"张华"）;                   // 向该Set集合中添加字符串
7        set.add（"李磊"）;
8        set.add（"王浩"）;
9       Iterator it = set.iterator（）;  // 获取Iterator对象

# 任务源码

结合任务描述和知识链接中接口的定义和实现方法相关知识点可以得到文件9-10所示的代码。

文件9-10 Example09.java

模块三 
任务实现

10       while （it.hasNext（））{  // 通过while循环，判断集合中是否有元素
11          Object obj = it.next（）;
12            System.out.println（obj）;
13        }
14    }
15 }

# 运行结果

模块三 
任务实现

文件9-10的运行结果如图9-16所示。

图9-16 文件9-14的运行结果

# 感谢关注
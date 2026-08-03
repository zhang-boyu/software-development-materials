# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

创建一个 LinkedHashMap类的集合，并向该集合存储键和值，输出集合中所有指定的键的值。

# ..

模块二 知识链接

LinkedHashMap类

LinkedHashMap类的方法

# LinkedHashMap类

模块二 
知识链接

HashMap 集合并不保证集合元素存入和取出的顺序。如果想让这两个顺序一致，可以使用 Java中提供的LinkedHashMa类，它是HashMap的子类，和Linkedlist一样也使用双向链表来维护内部元素的关系，使LinkedHashMap元素迭代的顺序与存入的顺序一致。

# LinkedHashMap类的方法

模块二 
知识链接

1.创建一个LinkedHashMap对象
LinkedHashMap<String， Integer> linkedHashMap = new LinkedHashMap<>（）;
2.添加元素到LinkedHashMap
linkedHashMap.put（"one"， 1）;
linkedHashMap.put（"two"， 2）;
linkedHashMap.put（"three"， 3）;

# LinkedHashMap类的方法

模块二 
知识链接

3.遍历LinkedHashMap
（1）使用for-each循环
for（Map.Entry<String， Integer> entry : linkedHashMap.entrySet（）） {
System.out.println（"Key = " + entry.getKey（） + "，Value = " + entry.getValue（））;
}
（2）使用迭代器
Iterator<Map.Entry<String，Integer>>iterator = linkedHashMap.entrySet（）.iterator（）;
while（iterator.hasNext（）） {
Map.Entry<String， Integer> entry = iterator.next（）;
System.out.println（"Key = " + entry.getKey（） + "， Value = " + entry.getValue（））;
}

# LinkedHashMap类的方法

模块二 
知识链接

4.获取LinkedHashMap的大小
int size = linkedHashMap.size（）;
5.检查LinkedHashMap是否包含特定的键或值
boolean containsKey = linkedHashMap.containsKey（"one"）;
boolean containsValue = linkedHashMap.containsValue（1）;
6.获取LinkedHashMap的特定元素
Integer value = linkedHashMap.get（"one"）;
7.删除LinkedHashMap的特定元素
LinkedHashMap.remove（"one"）;
8.清空LinkedHashMap
linkedHashMap.clear（）。

# ，

过渡页

模块三  任务实现

创建一个 LinkedHashMap类的集合，并向该集合存储键和值，输出集合中所有指定的键的值。

模块三 
任务实现

# 任务源码

根据任务描述以及LinkedHashMap知识点可以得到文件9-18所示的代码。

文件9-18 Example17.java

模块三 
任务实现

1import java.util.*;
2public class Example17 {
3  public static void main（String[] args） {
4     LinkedHashMap map = new LinkedHashMap（）; // 创建LinkedHashMap集合
5     map.put（"3"， "张华"）; // 存储键和值
6     map.put（"2"， "李磊"）;
7     map.put（"1"， "王智"）;
8     Set keySet = map.keySet（）;
9    Iterator it = keySet.iterator（）;
10   while （it.hasNext（）） {

# 任务源码

根据任务描述以及LinkedHashMap知识点可以得到文件9-18所示的代码。

文件9-18 Example17.java

模块三 
任务实现

11     Object key = it.next（）;
12     Object value = map.get（key）; // 获取每个键所对应的值
13     System.out.println（key + ":" + value）;
14   }
15 }
16 }

# 运行结果

模块三 
任务实现

文件9-18的运行结果如图9-27所示。

图9-27 文件9-18的运行结果

# 感谢关注
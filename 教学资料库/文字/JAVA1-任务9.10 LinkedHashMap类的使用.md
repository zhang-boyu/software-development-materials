# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

创建一个 TreeMap类的集合，并向该集合存储键和值，输出集合中所有指定的键的值。

# ..

模块二 知识链接

TreeMap类

‌主要方法

‌TreeMap的特点和适用场景

# TreeMap类

模块二 
知识链接

HashMap集合存储的元素的键值是无序的和不可重复的，为了对集合中的元素的键值进行排序，Map接口还有了另一个可以对集合中元素键和值进行排序的实现类TreeMap。
它也是用来存储键值映射关系的，并且不允许出现重复的键。在TreeMap内部是通过二叉树的原理来保证键的唯一性，这与TreeSet集合存储的原理一样，因此TreeMap中所有的键是按照某种顺序排列的。

# 主要方法

模块二 
知识链接

TreeMap类中定义了一些常用方法，具体如表9-7所示。

表9-7 TreeMap类的常用方法

| 方法声明 | 功能描述 |
|---|---|
| put（K key， V value） | 插入键值对 |
| get（Object key） | 获取指定键的值 |
| remove（Object key） | 移除指定键的值 |
| containsKey（Object key） | 检查是否包含指定键。 |
| containsValue（Object value） | 检查是否包含指定值。 |
| size（） | 返回映射中的键值对数量。 |
| clear（） | 移除所有映射关系 |

# TreeMap的特点和适用场景

模块二 
知识链接

有序性‌：TreeMap中的键值对是有序的，遍历时可以按照排序顺序获取或操作元素。
动态更新‌：支持动态插入、删除和修改键值对操作，且这些操作会保持元素的有序性。
范围查询‌：提供了一系列的方法来支持范围查询，例如headMap、tailMap和subMap等，可以根据指定的范围获取子映射。

# ，

过渡页

模块三  任务实现

创建一个 TreeMap类的集合，并向该集合存储键和值，输出集合中所有指定的键的值。

模块三 
任务实现

# 任务源码

根据任务描述以及成员TreeMap知识点可以得到文件9-19所示的代码。

文件9-19 Example18.java

模块三 
任务实现

1import java.util.Iterator;
2import java.util.Set;
3import java.util.TreeMap;
4public class Example18 {
5   public static void main（String[] args） {
6   TreeMap map = new TreeMap（）; // 创建TreeMap集合
7   map.put（3， "王智"）; // 存储键和值
8   map.put（1， "张华"）;
9   map.put（2， "李磊"）;
10  map.put（2， "李雷"）;
11  Set keySet = map.keySet（）;

# 任务源码

根据任务描述以及成员TreeMap知识点可以得到文件9-19所示的代码。

文件9-19 Example18.java

模块三 
任务实现

12  Iterator it = keySet.iterator（）;
13  while （it.hasNext（）） {
14     Object key = it.next（）;
15     Object value = map.get（key）; // 获取每个键所对应的值
16     System.out.println（key+":"+value）;
17   }
18  }
19 }

# 运行结果

模块三 
任务实现

文件9-19的运行结果如图9-28所示。

图9-28 文件9-19的运行结果

# 感谢关注
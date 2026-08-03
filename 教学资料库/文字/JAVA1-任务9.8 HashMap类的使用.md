# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务1：创建一个HashMap类的集合，并向该集合存储键和值，输出集合中所有指定的键的值。
子任务2：创建一个HashMap类的集合，并向该集合存储键和值，先遍历Map集合中所有的键，再根据键获取相应的值，输出集合中所有的键和值。
子任务3：创建一个HashMap类的集合，并向该集合存储键和值， 获取集合中键值对映射关系、获取集合中的键和值并输出。

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务4：创建一个HashMap类的集合，并向该集合存储键和值，使用for-each循环和entrySet（ ）方法遍历并输出集合中的键和值。
子任务5：创建一个HashMap类的集合，并向该集合存储键和值，使用for-each循环和keySet（ ）方法并输出集合中的键和值。

# ..

模块二 知识链接

Map接口简介

Map接口中常用方法

HashMap集合法

HashMap集合的遍历

# Map接口简介

模块二 
知识链接

数学中的函数描述了自变量到因变量的映射。Map接口借鉴了数学中函数的思想，因此Map接口中的每个元素都是由键到值的映射，即Map接口中的每个元素都由一个键值对组成。
Map接口是一种双列集合，它的每个元素都包含一个键对象Key和值对象Value，键和值对象之间存在一种对应关系，称为映射。Map中键对象Key不允许重复，访问Map集合中的元素时，只要指定了Key，就能找到对应的Value。

# Map接口中常用方法

模块二 
知识链接

Object类中定义了一些常用方法，具体如表9-6所示。

表9-6 Map接口的常用方法

| 方法声明 | 功能描述 |
|---|---|
| void put（Object key， Object value） | 将指定的值和键存入到集合中，并进行映射关联 |
| Object get（Object key） | 返回指定键所映射的值；如果此映射不包含该键的映射关系，则返回null |
| void clear（） | 移除所有的键值对元素 |
| V remove（Object key） | 根据键删除对应的值，返回被删除的值 |
| int size（） | 返回集合中的键值对的个数 |
| boolean containsKey（Object key） | 如果此映射包含指定键的映射关系，则返回 true。 |
| boolean containsValue（Object value） | 如果此映射将一个或多个键映射到指定值，则返回 true |
| Set keySet（） | 返回此映射中包含的键的Set集合 |
| Collection<V> values（） | 返回此映射中包含的值的Collection集合 |
| Set<Map.Entry<K，V>>entrySet（） | 返回此映射中包含的映射关系的Set集合 |

# HashMap集合

模块二 
知识链接

HashMap集合HashMap集合是Map接口的一个实现类，HashMap集合中的大部分方法都是Map接口方法的实现。在开发中，通常把HashMap集合对象的引用赋值给Map接口变量，那么接口变量就可以调用类实现的接口方法。HashMap集合用于存储键值映射关系，但HashMap集合没有重复的键并且键值无序。

# HashMap集合的遍历

模块二 
知识链接

在Java中，可以使用迭代器或增强的 for循环来遍历 HashMap 中的所有元素：
（1）使用迭代器Iterator和keySet（ ）方法遍历，具体使用详见子任务2。
（2）使用迭代器Iterator和entrySet（ ）方法遍历，具体使用详见子任务3。
（3）使用for-each循环和entrySet（ ）方法遍历，具体使用详见子任务4。
（4）使用for-each循环和keySet（ ）方法遍历，具体使用详见子任务5。

# ，

过渡页

模块三  任务实现

子任务1：创建一个HashMap类的集合，并向该集合存储键和值，输出集合中所有指定的键的值。
子任务2：创建一个HashMap类的集合，并向该集合存储键和值，先遍历Map集合中所有的键，再根据键获取相应的值，输出集合中所有的键和值。
子任务3：创建一个HashMap类的集合，并向该集合存储键和值， 获取集合中键值对映射关系、获取集合中的键和值并输出。

模块三 
任务实现

# ，

过渡页

模块三  任务实现

子任务4：创建一个HashMap类的集合，并向该集合存储键和值，使用for-each循环和entrySet（ ）方法遍历并输出集合中的键和值。
子任务5：创建一个HashMap类的集合，并向该集合存储键和值，使用for-each循环和keySet（ ）方法并输出集合中的键和值。

模块三 
任务实现

# 任务源码

子任务1：根据任务描述以及Map接口的常用方法知识点可以得到文件9-13所示的代码。

文件9-13 Example12.java

模块三 
任务实现

1import java.util.*;
2public class Example12 {
3	publicstatic void main（String[] args） {
4		Map map = new HashMap（）; // 创建HashMap对象
5		map.put（"1"， "张华"）;  // 存储键和值
6		map.put（"2"， "李磊"）;
7		map.put（"3"， "王智"）;
8		System.out.println（"1：" + map.get（"1"））; // 根据键获取值
9		System.out.println（"2：" + map.get（"2"））;
10		System.out.println（"3：" + map.get（"3"））;
11    }
12	}

# 运行结果

模块三 
任务实现

文件9-13的运行结果如图9-21所示。

图9-21 文件9-13的运行结果

# 任务源码

子任务2：根据任务描述以及Map接口的常用方法知识点可以得到文件9-14所示的代码。
文件9-14 Example13.java

模块三 
任务实现

1 import java.util.*;
2 public class Example13 {
3   public static void main（String[] args） {
4     Map map = new HashMap（）; // 创建HashMap集合
5     map.put（"1"， "张华"）; // 存储键和值
6     map.put（"2"， "李磊"）;
7     map.put（"3"， "王智"）;
8   Set keySet = map.keySet（）; // 获取键的集合
9   Iterator it = keySet.iterator（）; // 获取Iterator对象

# 任务源码

子任务2：根据任务描述以及Map接口的常用方法知识点可以得到文件9-14所示的代码。
文件9-14 Example13.java

模块三 
任务实现

10  while （it.hasNext（）） {
11  Object key = it.next（）;
12  Object value = map.get（key）; // 获取每个键所对应的值
13  System.out.println（key + ":" + value）;
14   }
15  }
16 }

# 运行结果

模块三 
任务实现

文件9-14的运行结果如图9-23 所示。

图9-23 文件9-14的运行结果

# 任务源码

子任务3：根据任务描述以及Map接口的常用方法知识点可以得到文件9-15所示的代码。

文件9-15 Example14.java

模块三 
任务实现

1import java.util.*;
2public class Example14 {
3	public staticvoidmain（String[] args） {
4		Map map = new HashMap（）;         // 创建HashMap集合
5		map.put（"1"， "张华"）;  // 存储键和值
6		map.put（"2"， "李磊"）;
7		map.put（"3"， "王智"）;
8		Set entrySet = map.entrySet（）;
9		Iterator it = entrySet.iterator（）;              // 获取Iterator对象
10		while （it.hasNext（）） {
1

# 任务源码

子任务3：根据任务描述以及Map接口的常用方法知识点可以得到文件9-15所示的代码。

文件9-15 Example14.java

模块三 
任务实现

1			// 获取集合中键值对映射关系
12			Map.Entry entry = Map.Entry）it.next（））;
13			Object key = entry.getKey（）; // 获取Entry中的键
14			Object value = entry.getValue（）;// 获取Entry中的值
15			System.out.println（key + ":" + value）;
16		} 
17	}
18 }

# 运行结果

模块三 
任务实现

文件9-15的运行结果如图9-24 所示。

图9-24 文件9-15的运行结果

# 任务源码

子任务4：根据任务描述以及Map接口的常用方法知识点可以得到文件9-16所示的代码。

文件9-16 Example15.java

模块三 
任务实现

1import java.util.*;
2public class Example15 {
3	public staticvoidmain（String[] args） {
4		HashMap<String， String> map = new HashMap<>（）;
5		map.put（"1"， "张华"）;  // 存储键和值
6		map.put（"2"， "李磊"）;
7		map.put（"3"， "王智"）;
8		for （Map.Entry<String， String> entry : map.entrySet（）） {
9		System.out.println（entry.getKey（） + ":" + entry.getValue（））;
10		}
11 }
12 }

# 运行结果

模块三 
任务实现

文件9-16的运行结果如图9-25 所示。

图9-25 文件9-16的运行结果

# 任务源码

子任务5：根据任务描述以及Map接口的常用方法知识点可以得到文件9-17所示的代码。

文件9-17 Example16.java

模块三 
任务实现

1import java.util.*;
2public class Example16 {
3   public static void main（String[] args） {
4       HashMap<String， String> map = new HashMap<>（）;
5       map.put（"1"， "张华"）; // 存储键和值
6       map.put（"2"， "李磊"）;
7       map.put（"3"， "王智"）;
8       for （String key: map.keySet（）） {
9          System.out.println（ key + ":" + map.get（key））;
10    }
11  }
12}

# 运行结果

模块三 
任务实现

文件9-17的运行结果如图9-26 所示。

图9-26 文件9-17的运行结果

# 感谢关注
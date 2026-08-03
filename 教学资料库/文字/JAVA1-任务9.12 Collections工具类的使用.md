# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务1：创建一个ArrayList类的字符串集合，添加元素并输出集合元素；反转该集合元素并输出；按自然顺序排序并输出；打乱集合元素并输出；交换集合首尾元素并输出。
子任务2：创建一个ArrayList类的整数集合，添加元素并输出集合元素；找出集合中的最大元素和最小元素并输出；替换集合中的一个整数再次输出集合元素；利用二分法查找出集合中某个元素的索引并输出。

# ..

模块二 知识链接

‌Collections工具类

‌‌添加、排序操作

‌‌查找、替换操作

# ‌Collections工具类

模块二 
知识链接

Collections工具类位于java.util包中，它提供了大量的静态方法用于对集合中的元素进行排序、查找和修改操作。

# ‌‌添加、排序操作

模块二 
知识链接

（ Collections工具类提供了一系列方法用于对List集合进行添加和排序操作，常用的方法如表9-8所示。

表9-8 Collections常用的添加和排序方法

| 方法声明 | 功能描述 |
|---|---|
| static <T> boolean addAll（Collection<? super T> c， T...elements） | 将所有指定元素添加到指定集合c中。T...elements代表可变参数 |
| static void reverse（List list） | 反转指定List集合中元素的顺序 |
| static void shuffle（List list） | 随机打乱List集合中元素的顺序 |
| static void sort（List list） | 根据元素的自然顺序（从小到大）对List集合中的元素进行排序 |
| static void swap（List list，int i，int j） | 将指定List集合中索引为i的元素和索引为j的元素进行交换 |

# ‌‌查找、替换操作

模块二 
知识链接

Collections类还提供了一些常用方法用于操作Set集合、List集合和Map集合等进行查找和替换的操作，常用的方法如表9-9所示。

表9-9 Collections常用的查找和替换方法

| 方法声明 | 功能描述 |
|---|---|
| static int binarySearch（List list，Object key） | 使用二分法搜索指定对象在List集合中的索引，要求查找的List集合中的元素必须是有序的 |
| static Object max（Collection col） | 根据元素的自然顺序，返回给定集合中最大的元素 |
| static Object min（Collection col） | 根据元素的自然顺序，返回给定集合中最小的元素 |
| static boolean replaceAll（List list，Object oldVal，Object newVal） | 用一个新值newVal替换List集合中所有的旧值oldVal |

# ，

过渡页

模块三  任务实现

子任务1：创建一个ArrayList类的字符串集合，添加元素并输出集合元素；反转该集合元素并输出；按自然顺序排序并输出；打乱集合元素并输出；交换集合首尾元素并输出。
子任务2：创建一个ArrayList类的整数集合，添加元素并输出集合元素；找出集合中的最大元素和最小元素并输出；替换集合中的一个整数再次输出集合元素；利用二分法查找出集合中某个元素的索引并输出。

模块三 
任务实现

# 任务源码

子任务1：根据任务描述以及Collections工具类中添加、排序操作中的常用方法知识点可以得到文件9-21所示的代码。
文件9-21 Example20.java

模块三 
任务实现

1import java.util.ArrayList;
2import java.util.Collections;
3public class Example20 {
4public static void main（String[] args） {
5   ArrayList<String> list = new ArrayList<>（）;
6   Collections.addAll（list， "d"，"z"，"b"，"m"）; // 添加元素
7   System.out.println（"排序前： " + list）;
8   Collections.reverse（list）; // 反转集合
9   System.out.println（"反转后： " + list）; 
10  Collections.sort（list）; // 按自然顺序排列

# 任务源码

子任务1：根据任务描述以及Collections工具类中添加、排序操作中的常用方法知识点可以得到文件9-21所示的代码。
文件9-21 Example20.java

模块三 
任务实现

11  System.out.println（"按自然顺序排序后： " + list）;
12  Collections.shuffle（list）; // 随机打乱集合元素
13  System.out.println（"按随机顺序排序后： " + list）; 
14  Collections.swap（list， 0， list.size（）-1）; // 将集合首尾元素交换
15  System.out.println（"集合首尾元素交换后： " + list）; 
16  }
17 }

# 运行结果

模块三 
任务实现

文件9-21的运行结果如图9-30所示。

图9-30 文件9-19的运行结果

# 任务源码

子任务2：根据任务描述以及Collections工具类中添加、排序操作中的常用方法知识点可以得到文件9-22所示的代码。
文件9-22 Example21.java

模块三 
任务实现

1import java.util.ArrayList;
2import java.util.Collections;
3public class Example21 {
4public static void main（String[] args） {
5  ArrayList<Integer> list = new ArrayList<>（）;
6  Collections.addAll（list， 5，7，-2，6，8）;// 向集合中添加所有指定元素
7  System.out.println（"集合中的元素： " + list）;
8  System.out.println（"集合中的最大元素： " + Collections.max（list））;
9  System.out.println（"集合中的最小元素： " + Collections.min（list））;
10 Collections.replaceAll（list， 7， 0）; // 将集合中的7用0替换掉

# 任务源码

子任务2：根据任务描述以及Collections工具类中添加、排序操作中的常用方法知识点可以得到文件9-22所示的代码。
文件9-22 Example21.java

模块三 
任务实现

11 System.out.println（"替换后的集合： " + list）;
12 Collections.sort（list）; //使用二分查找前，必须保证元素有序
13 System.out.println（"集合排序后为： "+list）;
14 int index = Collections.binarySearch（list， 8）;
15 System.out.println（"集合通过二分查找方法查找元素8所在索引为："+index）;
}
}

# 运行结果

模块三 
任务实现

文件9-22的运行结果如图9-31所示。

图9-31 文件9-22的运行结果

# 感谢关注
# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

创建一个ArrayList集合，向集合中添加4个元素，输出集合元素及其长度，输出第2个元素，删除索引为3的元素，替换索引为1的元素为李宏，输出新的集合元素。

# ..

模块二 知识链接

集合的概念

Collection接口

List接口

# 集合的概念

模块二 
知识链接

为了存储不同类型的多个对象，Java提供了一系列特殊的类，这些类可以存储任意类型的对象，并且存储的长度可变，被统称为集合。集合可以简单理解为一个长度可变，可以存储不同数据类型的动态数组。集合都位于java.util包中，使用集合时必须导入java.util包。以下是集合体系核心架构图，如图9-1所示。其中，虚线框里都是接口类型，实线框里是具体的实现类。

# 集合的概念

模块二 
知识链接

图9-1 集合核心体系架构图

# 集合的概念

模块二 
知识链接

表9-1 集合中的核心接口

| 接口 | 描述 |
|---|---|
| Collection | 集合中最基本的接口，一般不直接使用该接口 |
| List | Collection的子接口，用于存储一组有序、不唯一的对象，是集合中常用的接口之一 |
| Set | Collection的子接口，用于存储一组无序、唯一的对象 |
| Map | 用于存储一组键值对象，提供键到值的映射 |

# Collection接口

模块二 
知识链接

Collection接口是Java单列集合中的根接口，它定义了各种具体单列集合的共性，其他单列集合大多直接或间接继承该接口，Collection接口的定义如下所示。
public interface Collection<E> extends Iterable<E>{
    //Query Operations
}

# Collection接口

模块二 
知识链接

表9-2 Collection接口的常用方法

在开发中，很少直接使用Collection接口，基本上都是使用其子接口，Collection接口的子接口主要有List、Set等。

| 方法声明 | 功能描述 |
|---|---|
| boolean add（Object o） | 向集合中添加一个元素 |
| boolean addAll（Collection c） | 将指定集合c中的所有元素添加到本集合中 |
| void clear（） | 删除集合中的所有元素 |
| boolean remove（Object o） | 删除集合中指定的元素 |
| boolean removeAll（Collection c） | 删除当前集合中包含集合c中的所有元素 |

# List接口

模块二 
知识链接

List接口继承自Collection接口，List接口实例中允许存储重复的元素，所有的元素以线性方式进行存储。在程序中可以通过索引访问List接口实例中存储的元素。另外，List接口实例中存储的元素是有序的，即元素的存入顺序和取出顺序一致。
    List作为Collection集合的子接口，不但继承了Collection接口中的全部方法，而且还增加了一些根据元素索引操作集合的特有方法。

1、List接口简介

# List接口

模块二 
知识链接

表9-3 List接口的常用方法

| 方法声明 | 功能描述 |
|---|---|
| Void add（int index，Object element） | 将元素element插入List的index索引处 |
| boolean addAll（intindex，Collection c） | 将集合c所包含的所有元素插入到List集合的index索引处 |
| Object get（int index） | 返回集合index索引处的元素 |
| Object remove（int index） | 删除index索引处的元素 |
| Object set（int index， Object element） | 将index索引处元素替换成element对象，并将替换后的元素返回 |
| int indexOf（Object o） | 返回对象o在List中第一次出现的位置索引 |
| int lastIndexOf（Object o） | 返回对象o在List中最后一次出现的位置索引 |
| List subList（int fromIndex， int toIndex） | 返回从索引fromIndex（包括）到 toIndex（不包括）处所有元素集合组成的子集合 |

# ，

过渡页

模块三  任务实现

创建一个ArrayList集合，向集合中添加4个元素，输出集合元素及其长度，输出第2个元素，删除索引为3的元素，替换索引为1的元素为李宏，输出新的集合元素。

模块三 
任务实现

# 任务源码

结合任务描述和知识链接中相关知识点可以得到文件9-1所示的代码。：

模块三 
任务实现

文件9-1 Example01.Java

1import java.util.*;
2 public class Example01 {
3    public static void main（String[] args） {
4        ArrayList list = new ArrayList（）; // 创建ArrayList集合
5        list.add（"张华"）; //向集合中添加元素
6        list.add（"李红"）;
7        list.add（"王磊"）;
8        list.add（"赵永"）;

# 任务源码

结合任务描述和知识链接中相关知识点可以得到文件9-1所示的代码。：

模块三 
任务实现

文件9-1 Example01.Java

9        System.out.println（"集合元素为："+list）;//输出集合元素
10       System.out.println（"集合的长度：" + list.size（））; //获取集合中元素的个数
11       System.out.println（"第2个元素是：" + list.get（1））; //取出并打印指定位置的元素
12       list.remove（3）;  //删除索引为3的元素
13       System.out.println（"删除索引为3的元素："+list）;
14       list.set（1，"李宏"）; //替换索引为1的元素为李宏
15       System.out.println（"替换索引为1的元素为李宏后的集合为："+list）;
16     }
17   }

# 运行结果

文件9-1的运行结果如图9-2所示:

模块三 
任务实现

图9-2 文件9-1的运行结果

# 感谢关注
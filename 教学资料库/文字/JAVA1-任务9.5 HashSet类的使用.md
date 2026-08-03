# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务1：创建一个HashSet集合，向该集合中添加4个字符串元素，其中有两个字符串重复，使用Iterator接口遍历集合中的字符串。
子任务2：创建一个HashSet集合，向该集合中存储自定义类对象。

# ..

模块二 知识链接

Set接口

HashSet类

HashSet存储元素的流程

# Set接口

模块二 
知识链接

Set接口也继承自Collection接口，它与Collection接口中的方法基本一致，并没有对Collection接口进行功能上的扩充。与List接口不同的是，Set接口中元素是无序的，并且都会以某种规则保证存入的元素不出现重复。
Set接口常见的实现类有3个，分别是HashSet、LinkedHashSet、TreeSet。其中，HashSet根据对象的哈希值来确定元素在集合中的存储位置，具有良好的存取和查找性能；LinkedHashSet是链表和哈希表组合的一个数据存储结构；TreeSet则是以二叉树的方式存储元素，它可以对集合中的元素进行排序。

# HashSet类

模块二 
知识链接

HashSet是Set接口的一个实现类，它所存储的元素是不可重复的。当向HashSet集合中添加一个元素时，首先会调用该元素的hashCode( )方法来确定元素的存储位置，然后再调用元素对象的equals( )方法来确保该位置没有重复元素。Set集合与List集合存取元素的方式都一样，但是Set集合中的元素是无序的。

# HashSet存储元素的流程

模块二 
知识链接

当调用HashSet集合的add( )方法存入元素时，首先调用HashSet集合的hashCode( )方法获得元素对象的哈希值，然后根据对象的哈希值计算出一个存储位置。如果该位置上没有元素，则直接将元素存入。如果该位置上有元素存在，则会调用equals( )方法让当前存入的元素和该位置上的元素进行比较，如果返回的结果为false，就将该元素存入集合，返回的结果为true，则说明有重复元素，就将需要存入的重复元素舍弃。具体流程如图9-12所示。

# HashSet存储元素的流程

模块二 
知识链接

图9-12 HashSet存储元素的流程

# ，

过渡页

模块三  任务实现

子任务1：创建一个HashSet集合，向该集合中添加4个字符串元素，其中有两个字符串重复，使用Iterator接口遍历集合中的字符串。
子任务2：创建一个HashSet集合，向该集合中存储自定义类对象。

模块三 
任务实现

# 任务源码

子任务1：结合任务描述和知识链接中HashSet知识点可以得到文件9-7所示的代码。

文件9-7  Example06.java

模块三 
任务实现

1import java.util.*;
2public class Example07 {
3 public static void main（String[] args） {
4    HashSet hset = new HashSet（）; // 创建HashSet集合
5    hset.add（"张华"）; // 向该Set集合中添加字符串
6    hset.add（"李雷"）;
7    hset.add（"王治"）;
8    hset.add（"李雷"）; // 向该Set集合中添加重复元素
9    Iterator it = hset.iterator（）; // 获取Iterator对象

# 任务源码

子任务1：结合任务描述和知识链接中HashSet知识点可以得到文件9-7所示的代码。

文件9-7  Example06.java

模块三 
任务实现

10   while （it.hasNext（）） { // 通过while循环，判断集合中是否有元素
11   Object obj = it.next（）;// 如果有元素，就调用迭代器的next( )方法获取元素
12   System.out.println（obj）;
13  }
14 }
15 }

# 运行结果

文件9-7的运行结果如图9-13所示。

模块三 
任务实现

图9-13 文件9-7的运行结果

# 任务源码

子任务2：结合任务描述和知识链接中HashSet知识点可以得到文件9-8所示的代码。
文件9-8  Example08.java

模块三 
任务实现

1 class Student {		    		 
2   String  id;
3   String name;
4   public Student（String id，String name）{
5     this.id=id;
6     this.name=name;
7 }
8   public String toString（） {// 重写toString( )方法
9	    return id+":"+name;
10           }
11 }

# 任务源码

子任务2：结合任务描述和知识链接中HashSet知识点可以得到文件9-8所示的代码。

文件9-8  Example08.java

模块三 
任务实现

12import java.util.*;
13   public class Example08 {
14     public static void main（String[] args） {
15	   HashSet hs = new HashSet（）;                    // 创建HashSet集合
16     Student stu1 = new Student（"1"， "张华"）;  // 创建Student对象
17     Student stu2 = new Student（"2"， "李磊"）;
18	Student stu3 = new Student（"2"， "李磊"）;

# 任务源码

子任务2：结合任务描述和知识链接中HashSet知识点可以得到文件9-8所示的代码。

文件9-8  Example08.java

模块三 
任务实现

19	   hs.add（stu1）;
20	   hs.add（stu2）;
21    hs.add（stu3）;
22	  System.out.println（hs）;
23           }
24 }

# 运行结果

文件9-8的运行结果如图9-14所示。

模块三 
任务实现

图9-14 文件9-8的运行结果

由上图可知，运行结果中出现了两个相同的学生信息“2:李磊”，这样的学生信息应该被视为重复元素，不允许同时出现在HashSet集合中。上面文件之所以没有去掉这样的重复元素，是因为在定义Student类时没有重写hashCode（）和equals( )方法。改写Student类，在类中重写hashCode方法和equals方法。代码如文件9-9所示。

# 运行结果

模块三 
任务实现

1class Student {     
2   String  id;
3   String name;
4   public Student（String id，String name）{
5     this.id=id;
6     this.name=name;
7 }
8   public int hashCode（） { // 重写hashCode方法
9     return id.hashCode（）; // 返回id属性的哈希值
10  }
11   public boolean equals（Object obj） { // 重写equals方法
12     if （this == obj） { // 判断是否是同一个对象
13       return true; // 如果是，直接返回true
14     }

文件9-9  Example08.java

# 运行结果

模块三 
任务实现

15     if （!（obj instanceof Student）） { // 判断对象是为Student类型
16         return false; 
17      }
18     Student stu = （Student） obj; // 将对象强转为Student类型
19     boolean b = this.id.equals（stu.id）; // 判断id值是否相同
20     return b; // 返回判断结果
21    }
22    public String toString（） {// 重写toString( )方法
23     return id+":"+name;
24      }
25  }
26  import java.util.*;
27   public class Example07 {

文件9-9  Example08.java

# 运行结果

模块三 
任务实现

28   public static void main（String[] args） {
29	   HashSet hs = new HashSet（）;                    // 创建HashSet集合
30	   Student stu1 = new Student（"1"， "张华"）;  // 创建Student对象
31     Student stu2 = new Student（"2"， "李磊"）;
32     Student stu3 = new Student（"2"， "李磊"）;
33     hs.add（stu1）;
34     hs.add（stu2）;
35     hs.add（stu3）;
36     System.out.println（hs）;
37  }
38 }

文件9-9  Example08.java

# 运行结果

模块三 
任务实现

再次运行文件9-9，得到如图9-15所示的运行结果。

图9-15 文件9-9的运行结果

# 感谢关注
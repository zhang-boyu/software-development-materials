# 第7章  集合

Java基础入门（第3版）

# 学习目标/Target

# 学习目标/Target

# 章节概述/ Summary

在前面的章节中我们学习了数组，数组可以存储多个对象，但是数组只能存储相同类型的对象，如果要存储一批不同类型的对象，数组便无法满足需求了。为此，Java提供了集合，集合可以存储不同类型的多个对象。本章将针对Java中的集合类进行详细地讲解。

# 目录/Contents

# 目录/Contents

# 集合概述

7.1

# 7.1  集合概述

先定一个小目标！

# 7.1  集合概述

为了存储不同类型的多个对象，Java提供了一系列特殊的类，这些类可以存储任意类型的对象，并且存储的长度可变，被统称为集合。集合可以简单理解为一个长度可变，可以存储不同数据类型的动态数组。集合都位于java.util包中，使用集合时必须导入java.util包。

什么是集合

# 7.1  集合概述

集合体系核心架构

集合体系核心架构图如下所示。

上图列出了Java开发中常用的一些集合类，其中，虚线框里都是接口类型，实线框里是具体的实现类。

# 7.1  集合概述

集合中的核心接口

集合中的核心接口如下表所示。

| 接口 | 描述 |
|---|---|
| Collection | 集合中最基本的接口，一般不直接使用该接口 |
| List | Collection的子接口，用于存储一组有序、不唯一的对象，是集合中常用的接口之一 |
| Set | Collection的子接口，用于存储一组无序、唯一的对象 |
| Map | 用于存储一组键值对象，提供键到值的映射 |

# Collection接口

7.2

# 7.2  Collection接口

先定一个小目标！

# 7.2  Collection接口

Collection接口的定义

Collection接口是Java单列集合中的根接口，它定义了各种具体单列集合的共性，其他
单列集合大多直接或间接继承该接口，Collection接口的定义如下所示：

public interface Collection<E> extends Iterable<E>{
    //Query Operations
}

由上述Collection接口的定义可以看到，Collection是Iterable的子接口，Collection和
Iterable后面的<E>表示它们都使用了泛型。

# Collection接口的常用方法

Collection接口的常用方法如下表所示。

7.2  Collection接口

| 方法声明 | 功能描述 |
|---|---|
| boolean add(Object o) | 向集合中添加一个元素 |
| boolean addAll(Collection c) | 将指定集合c中的所有元素添加到本集合中 |
| void clear() | 删除集合中的所有元素 |
| boolean remove(Object o) | 删除集合中指定的元素 |
| boolean removeAll(Collection c) | 删除当前集合中包含集合c中的所有元素 |

# Collection接口的常用方法

7.2  Collection接口

| 方法声明 | 功能描述 |
|---|---|
| boolean isEmpty() | 判断集合是否为空 |
| boolean contains(Object o) | 判断集合中是否包含某个元素 |
| boolean containsAll(Collection c) | 判断集合中是否包含指定集合c中的所有元素 |
| Iterator iterator() | 返回集合的的迭代器(Iterator)，迭代器用于遍历该集合所有元素 |
| int size() | 获取集合元素个数 |

# List接口

7.3

# 7.3.1  List接口简介

先定一个小目标！

# 7.3.1  List接口简介

List接口继承自Collection接口，List接口实例中允许存储重复的元素，所有的元素以线性方式进行存储。在程序中可以通过索引访问List接口实例中存储的元素。另外，List接口实例中存储的元素是有序的，即元素的存入顺序和取出顺序一致。

List接口简介

# List接口常用方法

List作为Collection集合的子接口，不但继承了Collection接口中的全部方法，而且还增加了一些根据元素索引操作集合的特有方法。List接口的常用方法如下表所示。

7.3.1  List接口简介

| 方法声明 | 功能描述 |
|---|---|
| void add(int index,Object element) | 将元素element插入List的index索引处 |
| boolean addAll(int index,Collection c) | 将集合c所包含的所有元素插入到List集合的index索引处 |
| Object get(int index) | 返回集合index索引处的元素 |
| Object remove(int index) | 删除index索引处的元素 |

# List接口常用方法

7.3.1  List接口简介

上述列举了List接口的常用方法，List接口的所有实现类都可以通过调用这些方法操作集合元素。

| 方法声明 | 功能描述 |
|---|---|
| Object set(int index, Object element) | 将index索引处元素替换成element对象，并将替换后的元素返回 |
| int indexOf(Object o) | 返回对象o在List中第一次出现的位置索引 |
| int lastIndexOf(Object o) | 返回对象o在List中最后一次出现的位置索引 |
| List subList
(int fromIndex, int toIndex) | 返回从索引fromIndex（包括）到 toIndex（不包括）处所有元素集合组成的子集合 |

# 7.3.2  ArrayList

先定一个小目标！

# 7.3.2  ArrayList

ArrayList是List接口的一个实现类，它是程序中最常见的一种集合。ArrayList集合内部封装了一个长度可变的数组对象，当存入的元素超过数组长度时，ArrayList会在内存中分配一个更大的数组来存储这些元素，因此可以将ArrayList集合看作一个长度可变的数组。

# 7.3.2  ArrayList

ArrayList集合的元素插入过程

# 7.3.2  ArrayList

案例演示

下面通过一个案例学习ArrayList集合的元素存取。具体代码如下所示。

public class Example01 {
   public static void main(String[] args) {
        ArrayList list = new ArrayList(); // 创建ArrayList集合
        list.add("张三");                     // 向集合中添加元素
        list.add("李四");
        list.add("王五");
        list.add("赵六");
        System.out.println("集合的长度：" + list.size());       //获取集合中元素的个数
        System.out.println("第2个元素是：" + list.get(1));    //取出并打印指定位置的元素
        list.remove(3);        			        //删除索引为3的元素
        System.out.println("删除索引为3的元素:"+list);
        list.set(1,"李四2");                                                     //替换索引为1的元素为李四2
        System.out.println("替换索引为1的元素为李四2:"+list);
    }
}

# 7.3.2  ArrayList

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.3.2  ArrayList

案例运行结果分析

从上图的运行结果可以看出，索引位置为1的元素是集合中的第2个元素，这就说明集合和数组一样，索引的取值范围是从0开始的，最后一个索引是size-1，在访问元素时一定要注意索引不可超出此范围，否则程序会抛出索引越界异常IndexOutOfBoundsException。
由于ArrayList集合的底层是使用一个数组来存储元素，在增加或删除指定位置的元素时，会创建新的数组，效率比较低，因此Arraylist集合不适合做大量的增删操作，而适合元素的查找。

# 7.3.3  LinkedList

先定一个小目标！

# 7.3.3  LinkedList

为了克服ArrayList集合在查询元素时速度很快，但在增删元素时效率较低的局限性，可以使用List接口的另一个实现类LinkedList。LinkedList集合内部维护了一个双向循环链表，链表中的每一个元素都使用引用的方式记录它的前一个元素和后一个元素，从而可以将所有的元素彼此连接起来。当插入一个新元素时，只需要修改元素之间的引用关系即可，删除一个节点也是如此。正因为这样的存储结构，所以LinkedList集合增删效率非常高。

# 7.3.3  LinkedList

LinkedList集合添加、删除元素过程

# 7.3.3  LinkedList

LinkedList集合特有的方法

针对元素的增加、删除和获取操作，LinkedList集合定义了一些特有的方法，如下表所示。

| 方法声明 | 功能描述 |
|---|---|
| void add(int index, E element) | 在集合的index索引处插入element元素 |
| void addFirst(Object o) | 将指定元素o插入此集合的开头 |
| void addLast(Object o) | 将指定元素o添加到此集合的结尾 |
| Object getFirst() | 返回此集合的第一个元素 |
| Object getLast() | 返回此集合的最后一个元素 |
| Object removeFirst() | 移除并返回集合的第一个元素 |
| Object removeLast() | 移除并返回集合的最后一个元素 |
| boolean offer(Object o) | 将指定元素o添加到集合的结尾 |

# 7.3.3  LinkedList

LinkedList集合特有的方法

| 方法声明 | 功能描述 |
|---|---|
| boolean offerFirst(Object o) | 将指定元素o添加到集合的开头 |
| boolean offerLast(Object o) | 将指定元素o添加到集合的结尾 |
| Object peekFirst() | 获取集合的第一个元素 |
| Object peekLast() | 获取集合的最后一个元素 |
| Object pollFirst() | 移除并返回集合的第一个元素 |
| Object pollLast() | 移除并返回集合的最后一个元素 |
| void push(Object o) | 将指定元素o添加到集合的开头 |

# 7.3.3  LinkedList

案例演示

上述列出的方法主要是针对集合中的元素进行增加、删除和获取操作。下面通过一个案例学习这些方法的使用。具体代码如下所示。

public static void main(String[] args) {
        LinkedList link = new LinkedList();   // 创建LinkedList集合
        link.add("张三");
        link.add("李四");
        link.add("王五");
        link.add("赵六");
        System.out.println(link.toString()); // 获取并打印该集合中的元素
        link.add(3, "Student");     // 向link集合中索引3处插入元素Student
        link.addFirst("First");     // 向link集合第一个位置插入元素First
        System.out.println(link);
        System.out.println(link.getFirst()); // 取出link集合中第一个元素
        link.remove(3);               // 移除link集合中指定索引位置为3的元素
        link.removeFirst();          // 移除link集合中第一个元素
        System.out.println(link);
}

# 7.3.3  LinkedList

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 集合遍历

7.4

# 7.4.1  Iterator接口

先定一个小目标！

# Iterator接口是Java集合框架中的一员，但它与Collection、Map接口有所不同，Collection接口与Map接口主要用于存储元素，而Iterator主要用于迭代访问（遍历）Collection中的元素，通常情况下Iterator对象也被称为迭代器。

7.4.1  Iterator接口

# 案例演示

下面通过一个案例学习如何使用Iterator迭代集合中的元素。具体代码如下所示。

public class Example03 {
    public static void main(String[] args) {
        ArrayList list = new ArrayList(); // 创建ArrayList集合
        list.add("张三");                     // 向该集合中添加字符串
        list.add("李四");
        list.add("王五");
        list.add("赵六");
        Iterator it = list.iterator(); // 获取Iterator对象
        while (it.hasNext()) {           // 判断ArrayList集合中是否存在下一个元素
            Object obj = it.next();     // 取出ArrayList集合中的元素
            System.out.println(obj);
        }
    }
}

7.4.1  Iterator接口

# 案例运行结果

运行代码，控制台显示的运行结果如下图所示。

7.4.1  Iterator接口

# 迭代器迭代元素过程

迭代器对象在遍历集合时，内部采用指针的方式来跟踪集合中的
元素。迭代器迭代元素过程如下图所示。

注意：通过迭代器获取ArrayList集合中的元素时，这些元素的类型都是Object类型，如果
想获取到特定类型的元素，则需要进行对数据类型强制转换。

7.4.1  Iterator接口

# 脚下留心

并发修改异常

在使用Iterator迭代器对集合中的元素进行迭代时，如果调用了集合对象的remove()方法删除元素，之后继续使用迭代器遍历元素，会出现异常。

# 脚下留心

并发修改异常

案例演示

假设在集合中存储了学校所有学生的姓名，一个名为张三的学生中途转学，就需要在迭代集合时找出该元素并将其删除。具体代码如下所示。

ArrayList list = new ArrayList();    //创建ArrayList集合
        list.add("张三");
        list.add("李四");
        list.add("王五");        
        Iterator it = list.iterator();       // 获得Iterator对象
        while (it.hasNext()) {                // 判断该集合是否有下一个元素
            Object obj = it.next();           // 获取该集合中的元素
            if ("张三".equals(obj)) {         // 判断该集合中的元素是否为张三
                list.remove(obj);              // 删除该集合中的元素
            }
        }
        System.out.println(list);

# 脚下留心

并发修改异常

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 脚下留心

并发修改异常

案例运行结果分析

案例在运行时抛出了并发修改异常ConcurrentModificationException。这个异常是迭代器对象抛出的，出现异常的原因是集合在迭代器运行期间删除了元素，会导致迭代器预期的迭代次数发生改变，迭代器的迭代结果不准确。要解决上述问题，有两种方式可以采用。

# 脚下留心

并发修改异常

并发修改异常解决方式一

从业务逻辑上讲只想将姓名为张三的学生删除，因此只需找到该学生后跳出循环不再迭代即可，也就是在案例代码“list.remove(obj);”下面增加一个break语句，代码如下。

if ("张三".equals(obj)) {
	list.remove(obj);
	break;
}

在使用break语句跳出循环以后，由于没有继续使用迭代器对集合中的元素进行迭代，所以集合中删除元素对程序没有任何影响，就不会再出现异常。

# 脚下留心

并发修改异常

并发修改异常解决方式二

if ("张三".equals(obj)) {
	it.remove();
}

如果需要在集合的迭代期间对集合中的元素进行删除，可以使用迭代器本身的删除方法，将案例代码“list.remove(obj);”替换成it.remove()即可解决这个问题，代码如下。

# 脚下留心

并发修改异常

修改后的运行结果

替换代码后再次运行程序，控制台显示的运行结果如下图所示。

# 7.4.2  foreach循环

先定一个小目标！

# 7.4.2  foreach循环

foreach循环语法格式

foreach循环是一种更加简洁的for循环。foreach循环用于遍历数组或集合中的元素，
语法格式如下所示：

for(容器中元素类型 临时变量:容器变量) {
	执行语句
}

# 7.4.2  foreach循环

案例演示

下面通过一个案例演示foreach循环的用法。具体代码如下所示。

import java.util.*;
public class Example05 {
	public static void main(String[] args) {
	      ArrayList list = new ArrayList(); // 创建ArrayList集合
	      list.add("张三");                          // 向ArrayList集合中添加字符串元素
	      list.add("李四");
	      list.add("王五");		
	      for (Object obj : list) {	  // 使用foreach循环遍历ArrayList对象
		System.out.println(obj);// 取出并打印ArrayList集合中的元素
	      }
	}
}

# 7.4.2  foreach循环

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 脚下留心

foreach循环缺陷

foreach循环虽然书写起来很简洁，但在使用时也存在一定的局限性。当使用foreach循环遍历集合和数组时，只能访问集合中的元素，不能对其中的元素进行修改。

# 脚下留心

案例演示

以一个String类型的数组为例演示foreach循环的缺陷。具体代码如下所示。

foreach循环缺陷

static String[] strs = { "aaa", "bbb", "ccc" };
public static void main(String[] args) {
// foreach循环遍历数组
for (String str : strs) {
          str = "ddd";
	}
	System.out.println("foreach循环修改后的数组:" + strs[0] + "," +   strs[1] + ","+ strs[2]);
	// for循环遍历数组
	for (int i = 0; i < strs.length; i++) {
	          strs[i] = "ddd";
	}
	System.out.println("普通for循环修改后的数组:" + strs[0] + "," + strs[1] + ","+ strs[2]);
          }

# 脚下留心

案例运行结果

运行程序，控制台显示的运行结果如下图所示。

foreach循环缺陷

# 脚下留心

案例运行结果分析

foreach循环缺陷

从上述图中的运行结果可以看出foreach循环并不能修改数组中元素的值。原因是第6行代码中的str = "ddd"只是将临时变量str赋值为了一个新的字符串，这和数组中的元素没有一点关系。而在普通for循环中，可以通过索引的方式引用数组中的元素并修改其值。

# Set接口

7.5

# 7.5.1  Set接口简介

先定一个小目标！

# 7.5.1  Set接口简介

Set接口也继承自Collection接口，它与Collection接口中的方法基本一致，并没有对Collection接口进行功能上的扩充。与List接口不同的是，Set接口中元素是无序的，并且都会以某种规则保证存入的元素不出现重复。

Set接口常见的实现类有3个，分别是HashSet、LinkedHashSet、TreeSet。其中，HashSet根据对象的哈希值来确定元素在集合中的存储位置，具有良好的存取和查找性能；LinkedHashSet是链表和哈希表组合的一个数据存储结构；TreeSet则是以二叉树的方式存储元素，它可以对集合中的元素进行排序。

Set接口

# 7.5.2  HashSet

先定一个小目标！

# 7.5.2  HashSet

HashSet是Set接口的一个实现类，它所存储的元素是不可重复的。当向HashSet集合中添加一个元素时，首先会调用该元素的hashCode()方法来确定元素的存储位置，然后再调用元素对象的equals()方法来确保该位置没有重复元素。Set集合与List集合存取元素的方式都一样，但是Set集合中的元素是无序的。

# 7.5.2  HashSet

案例一演示

下面通过一个案例学习HashSet集合的应用。具体代码如下所示。

import java.util.*;
public class Example07 {
      public static void main(String[] args) {
            HashSet hset = new HashSet();   // 创建HashSet集合
            hset.add("张三");                  // 向该Set集合中添加字符串
            hset.add("李四");
            hset.add("王五");
            hset.add("李四");                  // 向该Set集合中添加重复元素
            Iterator it = hset.iterator();  // 获取Iterator对象
            while (it.hasNext()) {  // 通过while循环，判断集合中是否有元素
	   Object obj = it.next();// 如果有元素，就调用迭代器的next()方法获取元素
	   System.out.println(obj);
           }
     }
}

# 7.5.2  HashSet

案例一运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.5.2  HashSet

案例一结果分析

由上图的打印结果可以看出，取出元素的顺序与添加元素的顺序并不一致，并且重复存入的字符串对象“李四”被去除了，只添加了一次。

# 7.5.2  HashSet

HashSet存储元素的流程

当调用HashSet集合的add()方法存入元素时，首先调用HashSet集合的hashCode()方法获得元素对象的哈希值，然后根据对象的哈希值计算出一个存储位置。如果该位置上没有元素，则直接将元素存入。如果该位置上有元素存在，则会调用equals()方法让当前存入的元素和该位置上的元素进行比较，如果返回的结果为false，就将该元素存入集合，返回的结果为true，则说明有重复元素，就将需要存入的重复元素舍弃。

# 7.5.2  HashSet

案例二演示

下面通过案例演示向HashSet存储自定义类对象。具体代码如下所示。

class Student {		    		 
           ......//省略声明变量id和name，省略有参构造方法	
           public String toString() {// 重写toString()方法
	return id+":"+name;
           }
}
public class Example08 {
           public static void main(String[] args) {
	 HashSet hs = new HashSet();                    // 创建HashSet集合
	 Student stu1 = new Student("1", "张三");  // 创建Student对象
	 Student stu2 = new Student("2", "李四");
	 Student stu3 = new Student("2", "李四");
	 hs.add(stu1);
	 hs.add(stu2);
	 hs.add(stu3);
	 System.out.println(hs);
           }
}

# 7.5.2  HashSet

案例二运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.5.2  HashSet

案例二结果分析

由上图可知，运行结果中出现了两个相同的学生信息“2:李四”，这样的学生信息应该被视为重复元素，不允许同时出现在HashSet集合中。上面文件之所以没有去掉这样的重复元素，是因为在定义Student类时没有重写hashCode()和equals()方法。

# 7.5.2  HashSet

案例演示：向HashSet集合中添加数据时去除重复数据

下面改写案例二中的Student类，假设id相同的学生就是同一个学生，改写后的代码执行。具体步骤如下。

# 7.5.2  HashSet

// 重写hashCode方法
public int hashCode() { 
	return id.hashCode();	               // 返回id属性的哈希值
}
// 重写equals方法
public boolean equals(Object obj) { 
	if (this == obj) {                               // 判断是否是同一个对象
		return true;	                // 如果是，直接返回true
	}
	if (!(obj instanceof Student)) {         // 判断对象是为Student类型
		return false;			
	}
	Student stu = (Student) obj;            // 将对象强转为Student类型
	boolean b = this.id.equals(stu.id);   // 判断id值是否相同
	return	b;	                // 返回判断结果
}

步骤一：改写Student类，在类中重写hashCode方法和equals方法。代码如下所示：

# 7.5.2  HashSet

public class Example09 {
	public static void main(String[] args) {
		HashSet hs = new HashSet();                  // 创建HashSet对象
		Student stu1 = new Student("1", "张三");  // 创建Student对象
		Student stu2 = new Student("2", "李四");
		Student stu3 = new Student("2", "李四");
		hs.add(stu1);	                 // 向集合存入对象
		hs.add(stu2);
		hs.add(stu3);
		System.out.println(hs);                      // 打印集合中的元素
	}
}

步骤二：定义main()方法，创建HashSet对象，并向集合中存入对象。代码如下所示：

# 7.5.2  HashSet

案例三运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.5.3  LinkedHashSet

先定一个小目标！

# 7.5.3  LinkedHashSet

HashSet集合存储的元素是无序的，如果想让元素的存取顺序一致，可以使用Java提供的LinkedHashSet类，LinkedHashSet类是HashSet的子类，与LinkedList一样，它也使用双向链表来维护内部元素的关系。

# 7.5.3  LinkedHashSet

案例演示

下面通过一个案例学习LinkedHashSet类的用法。具体代码如下所示。

import java.util.Iterator;
import java.util.LinkedHashSet;
public class Example10 {
    public static void main(String[] args) {
        LinkedHashSet set = new LinkedHashSet();  
        set.add("张三");                   // 向该Set集合中添加字符串
        set.add("李四");
        set.add("王五");
        Iterator it = set.iterator();  // 获取Iterator对象
        while (it.hasNext()){           // 通过while循环，判断集合中是否有元素
            Object obj = it.next();
            System.out.println(obj);
        }
    }
}

# 7.5.3  LinkedHashSet

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

由上图可知，元素迭代出来的顺序和存入的顺序是一致的。

# 7.5.4  TreeSet

先定一个小目标！

# 7.5.4  TreeSet

TreeSet集合介绍

TreeSet是Set接口的另一个实现类，它内部采用平衡二叉树来存储元素，这样的结构可以保证TreeSet集合中没有重复的元素，并且可以对元素进行排序。所谓二叉树就是说每个节点最多有两个子节点的有序树，每个节点及其子节点组成的树称为子树，通常左侧的子节点称为“左子树”，右侧的节点称为“右子树”，其中左子树上的元素小于它的根结点，而右子树上的元素大于它的根结点。

# 7.5.4  TreeSet

二叉树中元素的存储结构

在二叉树中，同一层的元素，左边的元素总是小于右边的元素。接下来通过一个具体的图例来演示二叉树的存储过程。

# 7.5.4  TreeSet

二叉树的存储方式

假设向集合中存入8个元素，依次为13、8、17、17、1、11、15、25，如果以二叉树的方式来存储，在集合中的存储结构会形成一个树状结构。具体存储方式如下图所示。

# 7.5.4  TreeSet

TreeSet集合的特有方法

针对TreeSet集合存储元素的特殊性，TreeSet在继承Set接口的基础上实现了一些特有的方法。具体如下表所示。

| 方法声明 | 功能描述 |
|---|---|
| Object first() | 返回TreeSet集合的首个元素 |
| Object last() | 返回TreeSet集合的最后一个元素 |
| Object lower(Object o) | 返回TreeSet集合中小于给定元素的最大元素，如果没有返回null |
| Object floor(Object o) | 返回TreeSet集合中小于或等于给定元素的最大元素，如果没有返回null |
| Object higher(Object o) | 返回TreeSet集合中大于给定元素的最小元素，如果没有返回null |
| Object ceiling(Object o) | 返回TreeSet集合中大于或等于给定元素的最小元素，如果没有返回null |
| Object pollFirst() | 移除并返回集合的第一个元素 |
| Object pollLast() | 移除并返回集合的最后一个元素 |

# 7.5.4  TreeSet

案例演示

定义main()方法演示TreeSet集合中常用方法的使用，具体代码如下所示。

TreeSet ts = new TreeSet();     // 创建TreeSet集合
// 1、向TreeSet集合中添加元素
ts.add(3);
ts.add(29);
ts.add(101);
ts.add(21);
System.out.println("创建的TreeSet集合为："+ts);
// 2、获取首尾元素
System.out.println("TreeSet集合首元素为："+ts.first());
System.out.println("TreeSet集合尾部元素为："+ts.last());
// 3、比较并获取元素
System.out.println("集合中小于或等于9的最大的一个元素为："+ts.floor(9)); 
System.out.println("集合中大于10的最小的一个元素为："+ts.higher(10));
System.out.println("集合中大于100的最小的一个元素为："+ts.higher(100));
// 4、删除元素
Object first = ts.pollFirst();
System.out.println("删除的第一个元素是："+first);
System.out.println("删除第一个元素后TreeSet集合变为："+ts);

# 7.5.4  TreeSet

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.5.4  TreeSet

TreeSet的排序规则

Java提供了两种TreeSet的排序规则，分别为自然排序和自定义排序。在默认情况下，TreeSet集合都是采用自然排序，接下来将对这两种排序规则进行详细讲解。

# 7.5.4  TreeSet

自然排序

自然排序要求向TreeSet集合中存储的元素所在类必须实现Comparable接口，并重写compareTo()方法，然后TreeSet集合就会对该类型元素使用compareTo()方法进行比较。compareTo()方法将当前对象与指定的对象进行顺序比较，返回值为一个整数，其中返回负整数、零或正整数分别表示当前对象小于、等于或大于指定对象，默认根据比较结果顺序排列。

# 7.5.4  TreeSet

案例演示：compareTo()方法实现对象元素的顺序存取

下面通过一个案例学习将自定义的Student对象使用compareTo()方法实现对象元素的顺序存取。具体步骤如下。

# 7.5.4  TreeSet

import java.util.TreeSet;
class Student implements Comparable{
         ......//省略声明属性name和age，重写toString()方法
        //重写Comparable接口的compareTo()方法
        public int compareTo(Object obj) {
                Student stu = (Student)obj;
                //定义比较方式，先比较age，再比较name
                if(this.age - stu.age > 0){
                	      return 1;
                }
                if(this.age - stu.age == 0){
                	      return this.name.compareTo(stu.name);
                }
                return -1;
         }
}

步骤一：定义Student类并实现Comparable接口，声明属性name和age，重写toString()方法，重写Comparable接口的compareTo()方法。代码如下所示：

# 7.5.4  TreeSet

public class Example12 {
           public static void main(String[] args) {
                      TreeSet ts = new TreeSet();
                      ts.add(new Student("Lucy",18));
                      ts.add(new Student("Tom",20));
                      ts.add(new Student("Bob",20));
                      ts.add(new Student("Tom",20));
                      System.out.println(ts);
           }
}

步骤二：定义main()方法，创建TreeSet对象，添加数据并测试输出。代码如下所示：

# 7.5.4  TreeSet

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.5.4  TreeSet

自定义排序

如果不想实现Comparable接口或者不想按照实现了Comparable接口的类中compareTo()方法的规则进行排序，可以通过自定义比较器的方式对TreeSet集合中的元素自定义排序规则。实现Comparator接口的类都是一个自定义比较器，可以在自定义比较器中的compare()方法中自定义排序规则。

# 7.5.4  TreeSet

案例演示

接下来通过一个案例在TreeSet集合中自定义排序，排序规则是先根据Student的id升序排列，如果id相同则根据name进行升序排列

步骤一：创建Student类，在类中声明属性id和name，定义有参构造方法，并重写toString()方法。省略步骤一代码部分，可参考教材案例文件7-13。

步骤二：定义main()方法 ，创建一个TreeSet集合并通过匿名内部类的方式实现了Comparator接口，在内部类中重写了Comparator接口的compare()方法。

# 7.5.4  TreeSet

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# Map接口

7.6

# 7.6.1 Map接口简介

先定一个小目标！

# 7.6.1 Map接口简介

Map接口介绍

Map接口是一种双列集合，它的每个元素都包含一个键对象Key和值对象Value，键和值对象之间存在一种对应关系，称为映射。Map中键对象Key不允许重复，访问Map集合中的元素时，只要指定了Key，就能找到对应的Value。

# 7.6.1 Map接口简介

Map接口常用方法

Map接口定义了一系列方法用于访问元素，具体如下所示。

| 方法声明 | 功能描述 |
|---|---|
| void put(Object key, Object value) | 将指定的值和键存入到集合中，并进行映射关联 |
| Object get(Object key) | 返回指定键所映射的值；如果此映射不包含该键的映射关系，则返回null |
| void clear() | 移除所有的键值对元素 |
| V remove(Object key) | 根据键删除对应的值，返回被删除的值 |
| int size() | 返回集合中的键值对的个数 |

# 7.6.1 Map接口简介

Map接口常用方法

| 方法声明 | 功能描述 |
|---|---|
| boolean containsKey(Object key) | 如果此映射包含指定键的映射关系，则返回 true。 |
| boolean containsValue(Object value) | 如果此映射将一个或多个键映射到指定值，则返回 true |
| Set keySet() | 返回此映射中包含的键的Set集合 |
| Collection<V> values() | 返回此映射中包含的值的Collection集合 |
| Set<Map.Entry<K,V>>entrySet() | 返回此映射中包含的映射关系的Set集合 |

# 7.6.2  HashMap

先定一个小目标！

# 7.6.2  HashMap

HashMap集合是Map接口的一个实现类，HashMap集合中的大部分方法都是Map接口方法的实现。在开发中，通常把HashMap集合对象的引用赋值给Map接口变量，那么接口变量就可以调用类实现的接口方法。HashMap集合用于存储键值映射关系，但HashMap集合没有重复的键并且键值无序。

# 7.6.2  HashMap

案例演示

下面通过一个案例学习HashMap的用法，具体代码如下所示。

import java.util.*;
public class Example14 {
	public static void main(String[] args) {
		Map map = new HashMap(); // 创建HashMap对象
		map.put("1", "张三");          // 存储键和值
		map.put("2", "李四");
		map.put("3", "王五");
		System.out.println("1：" + map.get("1"));  // 根据键获取值
		System.out.println("2：" + map.get("2"));
		System.out.println("3：" + map.get("3"));
	}
}

# 7.6.2  HashMap

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.6.2  HashMap

修改案例，在map.put("3", "王五");这行代码下面增加一行代码，具体代码如下所示。

map.put("3", "赵六");

修改后案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.6.2  HashMap

修改后的案例结果分析

由上图可知，Map中仍然只有3个元素，只是第二次添加的值“赵六”覆盖了原来的值“王五”，这也证实了Map中的键必须是唯一的，不能重复，如果存储了相同的键，后存储的值则会覆盖原有的值，简而言之就是，键相同，值覆盖。

# 7.6.2  HashMap

第一种取出Map中所有的键和值的实现方式

先遍历Map集合中所有的键，再根据键获取相应的值。

# 7.6.2  HashMap

案例演示

下面通过一个案例演示先遍历Map集合中所有的键，再根据键获取相应的值，具体代码如下所示。

public class Example15 {
	public static void main(String[] args) {
		Map map = new HashMap();      // 创建HashMap集合
		map.put("1", "张三");                  // 存储键和值
		map.put("2", "李四");
		map.put("3", "王五");
		Set keySet = map.keySet();         // 获取键的集合
		Iterator it = keySet.iterator();     // 获取Iterator对象
		while (it.hasNext()) {
		        Object key = it.next();
		        Object value = map.get(key);  // 获取每个键所对应的值
		        System.out.println(key + ":" + value);
		}
	}
}

# 7.6.2  HashMap

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.6.2  HashMap

第二种取出Map中所有的键和值的实现方式

先获取集合中所有的映射关系，然后从映射关系中取出键和值。

# 7.6.2  HashMap

案例演示

下面通过一个案例演示先获取集合中所有的映射关系，然后从映射关系中取出键和值，具体代码如下所示。

public static void main(String[] args) {
	Map map = new HashMap();         // 创建HashMap集合
	map.put("1", "张三");       		// 存储键和值
	map.put("2", "李四");
	map.put("3", "王五");
	Set entrySet = map.entrySet();
	Iterator it = entrySet.iterator();              // 获取Iterator对象
	while (it.hasNext()) {
		// 获取集合中键值对映射关系
		Map.Entry entry = (Map.Entry) (it.next());
		Object key = entry.getKey();     // 获取Entry中的键
		Object value = entry.getValue();// 获取Entry中的值
		System.out.println(key + ":" + value);
	} 
}

# 7.6.2  HashMap

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.6.2  HashMap

Map中操作集合的常用方法

Map还提供了一些操作集合的常用方法，例如，values()方法用于获取map实例中所有的value，返回值类型为Collection；size()方法获取map集合的大小；containsKey()方法用于判断是否包含传入的键；containsValue()方法用于判断是否包含传入的值；remove()方法用于根据key移除map中的与该key对应的value等。

# 7.6.2  HashMap

案例演示

下面通过一个案例演示这些方法的使用，具体代码如下所示。

public static void main(String[] args) {
        Map map = new HashMap();      // 创建HashMap集合
        map.put("1", "张三");     	 // 存储键和值
        map.put("3", "李四");
        map.put("2", "王五");
        map.put("4", "赵六");
        System.out.println("集合大小为："+map.size());
        System.out.println("判断是否包含传入的键（2）："+map.containsKey("2"));
        System.out.println("判断是否包含传入的值（王五）："+map.containsValue("王五"));
        System.out.println("移除键为1的值是："+map.remove("1"));
        Collection values = map.values();
        Iterator it = values.iterator();
        while (it.hasNext()) {
            Object value = it.next();
            System.out.println(value);
        }
}

# 7.6.2  HashMap

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.6.3  LinkedHashMap

先定一个小目标！

# 7.6.3  LinkedHashMap

HashMap集合迭代出来元素的顺序和存入的顺序是不一致的。如果想让这Map集合中的元素迭代顺序与存入顺序一致，可以使用LinkedHashMap集合，LinkedHashMap是HashMap的子类，与LinkedList一样，LinkedHashMap集合也使用双向链表维护内部元素的关系，使Map集合元素迭代顺序与存入顺序一致。

# 7.6.3  LinkedHashMap

案例演示

下面通过一个案例学习LinkedHashMap的用法，具体代码如下所示。

import java.util.*;
public class Example18 {
    public static void main(String[] args) {
        Map map = new LinkedHashMap();             // 创建LinkedHashMap集合
        map.put("3", "李四");              	                 // 存储键和值
        map.put("2", "王五");
        map.put("4", "赵六");
        Set keySet = map.keySet();
        Iterator it = keySet.iterator();
        while (it.hasNext()) {
            Object key = it.next();
            Object value = map.get(key); // 获取每个键所对应的值
            System.out.println(key + ":" + value);
        }
    }
}

# 7.6.3  LinkedHashMap

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

由图可知，元素迭代出来的顺序和存入的顺序是一致的。

# 7.6.4  TreeMap

先定一个小目标！

# 7.6.4  TreeMap

TreeMap集合

HashMap集合存储的元素的键值是无序的和不可重复的，为了对集合中的元素的键值进行排序，Map接口还有了另一个可以对集合中元素键和值进行排序的实现类TreeMap。

# 7.6.4  TreeMap

案例演示

下面通过一个案例学习TreeMap的用法，具体代码如下所示。

public class Example19 {
    public static void main(String[] args) {
         Map map = new TreeMap();      // 创建TreeMap集合
         map.put(3, "李四");                  // 存储键和值
         map.put(2, "王五");
         map.put(4, "赵六");
         map.put(3, "张三");       
         Set keySet = map.keySet();
         Iterator it = keySet.iterator();
        while (it.hasNext()) {
            Object key = it.next();
            Object value = map.get(key); // 获取每个键所对应的值
            System.out.println(key+":"+value);
        }
    }
}

# 7.6.4  TreeMap

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.6.4  TreeMap

案例结果分析

由上图可知，添加的元素已经按键值从小到大进行自动排序，并且键值重复存入的整数3只有一个，只是后来添加的值“张三”覆盖了原来的值“李四”。这也证实了TreeMap中的键必须是唯一的，不能重复并且有序，如果存储了相同的键，后存储的值则会覆盖原有的值。

# 7.6.4  TreeMap

案例演示

下面通过一个案例实现按键值排序，在该案例中，键是自定义类，值是String类，具体步骤如下所示。

class Student {
    private String name;
    private int age;
    //省略getter/setter方法
    public Student(String name, int age) {
        super();
        this.name = name;
        this.age = age;
    }
    public String toString() {
        return "Student [name=" + name + ", age=" + age + "]";
    }
}

步骤一：定义Student类，声明name和age属性，代码如下所示：

# 7.6.4  TreeMap

public static void main(String[] args) {
        TreeMap tm = new TreeMap(new Comparator<Student>() {
            public int compare(Student s1, Student s2) {
                int num = s1.getName().compareTo(s2.getName());//按照姓名比较
                return num == 0 ? num:s1.getAge() - s2.getAge();
            }
        });
        tm.put(new Student("张三", 23), "北京");
        tm.put(new Student("李四", 13), "上海");
        tm.put(new Student("赵六", 43), "深圳");
        tm.put(new Student("王五", 33), "广州");
        Set keySet = tm.keySet();
        Iterator it = keySet.iterator();
        while (it.hasNext()) {
            Object key = it.next();
            Object value = tm.get(key); // 获取每个键所对应的值
            System.out.println(key+":"+value);
        }
    }

步骤二：定义main()方法，代码如下所示：

# 7.6.4  TreeMap

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.6.5  Properties

先定一个小目标！

# 7.6.5  Properties

Properties集合

Map接口还有一个实现类Hashtable，它和HashMap十分相似，区别在于Hashtable是线程安全的。Hashtable存取元素时速度很慢，目前基本上被HashMap类所取代。但Hashtable类有一个很重要的子类Properties，应用非常广泛。Properties主要用于存储字符串类型的键和值，在实际开发中，经常使用Properties集合存储应用的配置项。

# 7.6.5  Properties

假设有一个文本编辑工具，要求默认背景色是红色，字体大小为14px，语言为中文，其配置项如下面的代码。 要求使用Properties集合对这些配置项进行存储。

Backgroup-color = red
Font-size = 14px
Language = chinese

# 7.6.5  Properties

案例演示

下面通过一个案例演示应用配置项的存取，具体代码如下所示。

import java.util.*;
public class Example21 {
   public static void main(String[] args) {
        Properties p=new Properties();         // 创建Properties对象
        p.setProperty("Backgroup-color", "red");
        p.setProperty("Font-size", "14px");
        p.setProperty("Language", "chinese");
        Enumeration names = p.propertyNames();//获取Enumeration对象所有键枚举
        while(names.hasMoreElements()){        //循环遍历所有的键
	    String key=(String) names.nextElement();
	    String value=p.getProperty(key);   // 获取对应键的值
	    System.out.println(key+" = "+value);
      }
   }
}

# 7.6.5  Properties

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 常用工具类

7.7

# 7.7.1  Collections工具类

先定一个小目标！

# 7.7.1  Collections工具类

1. 添加、排序操作

Collections类提供了一系列方法用于对List集合进行添加和排序操作，常用的方法如下表所示。

| 方法声明 | 功能描述 |
|---|---|
| static <T> boolean addAll(Collection<? super T> c, T...    elements) | 将所有指定元素添加到指定集合c中 |
| static void reverse(List list) | 反转指定List集合中元素的顺序 |
| static void shuffle(List list) | 随机打乱List集合中元素的顺序 |
| static void sort(List list) | 根据元素的自然顺序（从小到大）对List集合中的元素进行排序 |
| static void swap(List list,int i,int j) | 将指定List集合中索引为i的元素和索引为j的元素进行交换 |

# 7.7.1  Collections工具类

案例演示

下面通过一个案例学习上述表中的方法，具体代码如下表所示。

import java.util.ArrayList;
import java.util.Collections;
public class Example22 {
            public static void main(String[] args) {
	ArrayList<String> list = new ArrayList<>();
	Collections.addAll(list, "C","Z","B","K");    // 添加元素
	System.out.println("排序前: " + list);
	Collections.reverse(list);                       // 反转集合
	System.out.println("反转后： " + list); 
	Collections.sort(list);                           // 按自然顺序排列
	System.out.println("按自然顺序排序后: " + list);
	Collections.shuffle(list);                       // 随机打乱集合元素
	System.out.println("按随机顺序排序后:  " + list); 
	Collections.swap(list, 0, list.size()-1);     // 将集合首尾元素交换
	System.out.println("集合首尾元素交换后: " + list); 
            }
}

# 7.7.1  Collections工具类

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.7.1  Collections工具类

2. 查找、替换操作

Collections类还提供了一些常用方法用于操作Set集合、
List集合和Map集合等，常用的方法如下表所示。

| 方法声明 | 功能描述 |
|---|---|
| static int binarySearch(List list,Object key) | 使用二分法搜索指定对象在List集合中的索引，要求查找的List集合中的元素必须是有序的 |
| static Object max(Collection col) | 根据元素的自然顺序，返回给定集合中最大的元素 |
| static Object min(Collection col) | 根据元素的自然顺序，返回给定集合中最小的元素 |
| static boolean replaceAll(List list,Object oldVal,Object newVal) | 用一个新值newVal替换List集合中所有的旧值oldVal |

# 7.7.1  Collections工具类

案例演示

下面通过一个案例学习Collections类中常用的方法，具体代码如下表所示。

import java.util.ArrayList;
import java.util.Collections;
public class Example23 {
       public static void main(String[] args) {
	ArrayList<Integer> list = new ArrayList<>();
	Collections.addAll(list, -3,2,9,5,8);// 向集合中添加所有指定元素
	System.out.println("集合中的元素: " + list);
	System.out.println("集合中的最大元素: " + Collections.max(list));
	System.out.println("集合中的最小元素: " + Collections.min(list));
	Collections.replaceAll(list, 8, 0); // 将集合中的8用0替换掉
	System.out.println("替换后的集合: " + list);
	Collections.sort(list);               //使用二分查找前，必须保证元素有序
	System.out.println("集合排序后为： "+list);
	int index = Collections.binarySearch(list, 9);
	System.out.println("集合通过二分查找方法查找元素9所在索引为："+index);
     }
}

# 7.7.1  Collections工具类

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.7.2  Arrays工具类

先定一个小目标！

# 7.7.2  Arrays工具类

1. 使用sort()方法排序

Arrays工具类中的静态方法sort()来实现数组排序。下面通过一个案例来学习sort()方法的使用，具体步骤如下所示。

public static void printArray(int[] arr) {  
	System.out.print("[");
	for (int x = 0; x < arr.length; x++) {
		if (x != arr.length - 1) {
			System.out.print(arr[x] + ", ");
		} else {
			System.out.println(arr[x] + "]");
		}
	}
}

步骤一：定义打印数组元素方法，代码如下所示：

# 7.7.2  Arrays工具类

import java.util.Arrays;
public class Example24 {
	public static void main(String[] args) {
		int[] arr = { 9, 8, 3, 5, 2 };   // 初始化一个数组
		System.out.print("排序前：");
		printArray(arr);                    // 打印原数组
		Arrays.sort(arr);                   // 调用Arrays的sort()方法排序
		System.out.print("排序后：");
		printArray(arr);                    // 打印排序后数组
	}
}

步骤二：定义main()方法，调用打印数组元素方法printArray()。代码如下所示：

# 7.7.2  Arrays工具类

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.7.2  Arrays工具类

案例结果分析

由上图可知，使用Arrays的sort()方法时将会按照自然顺序对数组元素进行从小到大排序，使用非常方便。针对数组排序，数组工具类Arrays还提供了其他多个重载的sort()方法，既可以按照自然顺序进行排序，也可以传入比较器参数按照定制规则排序，同时还支持选择排序的元素范围。

# 7.7.2  Arrays工具类

2. 使用binarySearch()方法查找元素

在程序开发中，经常会在数组中查找某些特定的元素，如果数组中元素较多时查找某个元素，效率会非常低。为此，Arrays工具类中提供了一个binarySearch()方法用于查找元素。binarySearch()方法声明如下所示。

binarySearch(Object[] a, Object key);

在上述语法中，参数a是指被查询的集合，参数key指被查询的元素值。

# 7.7.2  Arrays工具类

二分法查找元素的过程

所谓二分法查找就是每次将指定元素和数组中间位置的元素进行比较，从而排除掉其中的一半元素，这样的查找是非常高效的。右图中的start、end和mid（mid=(start+end)/2）分别代表在数组中查找区间的开始索引、结束索引和中间索引。

# 7.7.2  Arrays工具类

案例演示

下面通过一个案例来学习binarySearch()方法的使用，具体代码如下表所示。

import java.util.Arrays;
public class Example25 {
	public static void main(String[] args) {
		int[] arr = { 9, 8, 3, 5, 2 };
		Arrays.sort(arr);                            // 对数组进行排序
		int index = Arrays.binarySearch(arr, 3); // 查找指定元素3
		System.out.println("元素3的索引是:" + index);
	}
}

# 7.7.2  Arrays工具类

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

由上图可知，使用Arrays的bianrySearch()方法查找出了3在数组中的索引为1（排序后的数组索引）。

# 7.7.2  Arrays工具类

3.使用copyOfRange()方法复制元素

在程序开发中，经常需要在不破坏原数组的情况下使用数组中的部分元素，这时可以使用Arrays工具类的copyOfRange()方法，copyOfRange()方法可以将数组中指定范围的元素复制到一个新的数组中。copyOfRange()方法声明格式如下所示。

copyOfRange(int[] original, int from,int to);

在上述语法中，参数original表示被复制的数组，from表示被复制元素的初始索引（包括），to表示被复制元素的最后索引（不包括）。

# 7.7.2  Arrays工具类

案例演示

下面通过一个案例来学习如何通过调用copyOfRange()方法实现数组的复制，具体代码如下表所示。

import java.util.Arrays;
public class Example26 {
	public static void main(String[] args) {
	            int[] arr = { 9, 8, 3, 5, 2 };
                                        // 复制一个指定范围的数组
	            int[] copied = Arrays.copyOfRange(arr, 1, 7);
	            for (int i = 0; i < copied.length; i++) {
		System.out.print(copied[i] + " ");
		}
	}
}

# 7.7.2  Arrays工具类

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 7.7.2  Arrays工具类

4. 使用fill()方法替换元素

程序开发中，可能会需要将一个数组中的所有元素替换成同一个元素，此时可以使用Arrays工具类的fill()方法，该方法可以将指定的值赋给数组中的每一个元素，fill()方法声明如下所示。

fill(Object[] a,Object val);

在上述语法中，参数a表示被修改的数组，val表示需要被替换成的元素。

# 7.7.2  Arrays工具类

案例演示

下面通过一个案例来演示如何调用fill()方法实现元素替换，具体代码如下表所示。

import java.util.Arrays;
public class Example27 {
	public static void main(String[] args) {
		int[] arr = { 1, 2, 3, 4 };
		Arrays.fill(arr, 8);       // 用8替换数组中的每个元素
		for (int i = 0; i < arr.length; i++) {
			System.out.println(i + ": " + arr[i]);
		}
	}
}

# 7.7.2  Arrays工具类

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

从上图可以看出，在调用了Arrays工具类的fill(arr,8)方法后，数组arr中的元素全部
被替换为8。

# Lambda表达式

7.8

# 7.8  Lambda表达式

先定一个小目标！

# 7.8  Lambda表达式

Lambda表达式介绍

Lambda表达式是JDK 8之后新增的一个新特性，Lambda可以取代大部分的匿名内部类，写出更优雅的Java代码，尤其在集合的遍历和其他集合操作中，可以极大地优化代码结构。JDK也提供了大量的内置函数式接口供我们使用，使得 Lambda 表达式的运用更加方便、高效。Lambda表达式由参数列表、箭头符号 -> 和方法体组成。方法体既可以是一个表达式，也可以是一个语句块。

# 7.8  Lambda表达式

Lambda表达式常用的语法格式

| 语法格式 | 描述 |
|---|---|
| ()-> System.out.println("Hello Lambda!"); | 无参数，无返回值 |
| (x) -> System.out.println(x) | 有一个参数，并且无返回值 |
| x -> System.out.println(x) | 若只有一个参数，小括号可以省略不写 |
| Comparator<Integer> com = (x, y) -> {
System.out.println("函数式接口");
return Integer.compare(x, y); }; | 有两个以上的参数，有返回值，并且 Lambda 方法体中有多条语句 |
| Comparator<Integer> com = (x, y) -> Integer.compare(x, y); | 若Lambda 体中只有一条语句，return 和大括号都可以省略不写 |
| (Integer x, Integer y) -> Integer.compare(x, y); | Lambda 表达式的参数列表的数据类型可以省略不写，因为JVM编译器通过上下文推断出，数据类型，即“类型推断” |

# 7.8  Lambda表达式

案例演示

上述表中给出了6种Lambda表达式的格式，下面通过一个案例学习Lambda表达式语法，具体代码如下表所示。

import java.util.Arrays;
public class Example28 {
    public static void main(String[] args) {
       String[] arr = {"program", "creek", "is", "a", "java", "site"};
       Arrays.sort(arr, (m, n) -> Integer.compare(m.length(), n.length()));
       System.out.println("Lambda语句体中只有一条语句，参数类型可推断："+
                              Arrays.toString(arr));
       Arrays.sort(arr, (String m, String n) -> {
         if (m.length() > n.length())
                return -1;
            else
                return 0;
        });
        System.out.println("Lambda语句体中有多条语句："+Arrays.toString(arr));
    }
}

# 7.8  Lambda表达式

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 本章小结

本章详细介绍了几种Java常用集合类，首先介绍了集合的概念和Collection接口；其次介绍了List接口，包括ArrayList集合、LinkedList集合、Iterator迭代器和foreach循环；接着介绍了Set接口，包括HashSet集合、LinkedHashSet集合和TreeSet集合；然后介绍了Map接口，包括HashMap集合、LinkedHashMap集合、TreeMap集合和Properties集合；接着又介绍了集合的常用工具类，包括Collections工具类和Arrays工具类；最后介绍了Lambda表达式。通过本章的学习，读者可以熟练掌握各种集合类的使用场景，以及需要注意的细节，同时可以掌握Lambda表达式的使用。熟练掌握本章知识，对Java实际开发非常重要。

本

章

小

结
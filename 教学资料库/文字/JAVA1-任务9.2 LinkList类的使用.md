# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

创建一个LinkedList集合，向集合中添加4个元素，输出集合元素及其长度，向link集合中索引2处插入元素“周洋”，向link集合第一个位置处插入元素“王娜”，取出link集合中第一个元素，移除link集合中指定索引位置为1的元素，移除link集合中最后一个元素，输出新的集合元素及长度。

# ..

模块二 知识链接

LinkedList集合

# LinkedList集合

模块二 
知识链接

ArrayList集合在查询元素时速度很快，但在增删元素时效率较低，为了克服这种局限性，可以使用List接口的另一个实现类 LinkedList。LinkedList内部维护了一个双向循环链表，链表中的每一个元素都使用引用的方式来记住它的前一个元素和后一个元素，从而可以将所有的元素彼此连接起来。当插入一个新元素时只需要修改元素之间的这种引用关系即可，删除一个节点也是如此。

# LinkedList集合

模块二 
知识链接

正因为这样的存储结构，所以 Linkedlist集合对于元素的增删操作表现出很高的效率，LinkedList 集合添加元素和删除元素的过程如图9-3所示。

图9-3 LinkedList集合添加、删除元素过程图

# LinkedList集合

模块二 
知识链接

# ，

过渡页

模块三  任务实现

创建一个LinkedList集合，向集合中添加4个元素，输出集合元素及其长度，向link集合中索引2处插入元素“周洋”，向link集合第一个位置处插入元素“王娜”，取出link集合中第一个元素，移除link集合中指定索引位置为1的元素，移除link集合中最后一个元素，输出新的集合元素及长度。

模块三 
任务实现

# 任务源码

结合任务描述和知识链接中相关知识点可以得到文件9-2所示的代码。：

模块三 
任务实现

文件9-2 Example02.Java

1import java.util.*;
2public class Example02 {
3	publicstaticvoidmain（String[] args） {
4		 LinkedList link = new LinkedList（）;   // 创建LinkedList集合
5	link.add（"李宏"）;
6	link.add（"赵芳"）;
7	link.add（"王磊"）;
8	link.add（"刘丽"）;
9	System.out.println（link）; // 获取并打印该集合中的元素
10System.out.println（"集合的长度：" + link.size（））;

# 任务源码

结合任务描述和知识链接中相关知识点可以得到文件9-2所示的代码。：

模块三 
任务实现

11          link.add（2， "周洋"）;     // 向link集合中索引2处插入元素周洋
12	link.addFirst（"王娜"）;    // 向link集合第一个位置插入元素王娜
13	        System.out.println（link）;
14	        System.out.println（link.getFirst（））; // 取出link集合中第一个元素
15	        link.remove（1）;            // 移除link集合中指定索引位置为1的元素
16	        link.removeLast（）;          // 移除link集合中第一个元素
17	        System.out.println（link）;
18	}
19	}

# 运行结果

文件9-2的运行结果如图9-4所示:

模块三 
任务实现

图9-4 文件9-2的运行结果

# 感谢关注
# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务1：创建一个TreeSet集合，向该集合添加元素55、81、99、80；获取首尾元素；比较并获取集合中小于或等于80的最大的一个元素和集合中大于80的最小的一个元素；删除第一个元素。
子任务2：定义Student类并实现Comparable接口，声明属性name和age以及构造方法Student（String name， int age），重写toString( )方法，重写Comparable接口的compareTo( )方法。创建一个TreeSet集合，向该集合添加元素并输出。

# ..

模块二 知识链接

TreeSet类

TreeSet类存储方式

TreeSet类的特有方法

向TreeSet集合添加元素机制

# TreeSet类

模块二 
知识链接

TreeSet是Set接口的另一个实现类，它内部采用平衡二叉树来存储元素，这样的结构可以保证TreeSet集合中没有重复的元素，并且可以对元素进行排序。所谓二叉树就是说每个节点最多有两个子节点的有序树，每个节点及其子节点组成的树称为子树，通常左侧的子节点称为“左子树”，右侧的节点称为“右子树”，其中左子树上的元素小于它的根结点，而右子树上的元素大于它的根结点。二叉树中元素的存储结构如图9-17所示。

# TreeSet类

模块二 
知识链接

图9-17所示是一个二叉树模型。在二叉树中，对于同一层的元素，左边的元素总是小于右边的元素。为了更好地理解TreeSet中二叉树存放元素的原理，接下来分析二叉树中元素的存储过程。当二叉树中存入新元素时，新元素首先会与第1个元素（最顶层元素）进行比较。如果小于第1个元素，就执行左边的分支，继续和该分支的元素进行比较；如果大于第1个元素，就执行右边的分支，继续和该分支的元素进行比较。如此进行下去，直到与最后一个元素进行比较。如果新元素小于最后一个元素，就将其放在最后一个元素的左子树上，如果大于最后一个元素就将其放在最后一个元素的右子树上。

图9-17 二叉树中元素的存储结构

# TreeSet类存储方式

模块二 
知识链接

上面通过文字描述的方式对二叉树的存储原理进行了讲解，接下来通过一个具体的例子演示二叉树的存储方式。假设向集合中存入8个元素，依次为13、8、17、17、1、11、15、25如果以二叉树的方式存储，在集合中会形成树状结构，如图9-18所示。

# TreeSet类

模块二 
知识链接

从图9-12可以看出，在向集合中依次存入元素时，首先将第一个元素放在二叉树的最顶端。随后存入的元素与第一个元素比较。如果小于第一个元素，就将该元素放左子树上;如果大于第一个元素，就将该元素放在右子树上。以此类推，按照左子树元素小于右子树元素的顺序进行排序。当二叉树中已经存入一个为17的元素，再向集合中存入一个为17的元素时，TreeSet会将重复的元素去掉。

图9-18 二叉树中元素的存储方式

# TreeSet类的特有方法

模块二 
知识链接

针对TreeSet集合存储元素的特殊性，TreeSet在继承Set接口的基础上实现了一些特有的方法。具体如表9-5所示。

表9-5 TreeSet类的特有方法

| 方法声明 | 功能描述 |
|---|---|
| Object first（） | 返回TreeSet集合的首个元素 |
| Object last（） | 返回TreeSet集合的最后一个元素 |
| Object lower（Object o） | 返回TreeSet集合中小于给定元素的最大元素，如果没有返回null |
| Object floor（Object o） | 返回TreeSet集合中小于或等于给定元素的最大元素，如果没有返回null |
| Object higher（Object o） | 返回TreeSet集合中大于给定元素的最小元素，如果没有返回null |
| Object ceiling（Object o） | 返回TreeSet集合中大于或等于给定元素的最小元素，如果没有返回null |
| Object pollFirst（） | 移除并返回集合的第一个元素 |
| Object pollLast（） | 移除并返回集合的最后一个元素 |

# 向TreeSet集合添加元素机制

模块二 
知识链接

TreeSet集合添加元素时，不论元素的添加顺序如何，这些元素都能够按照一定的顺序进行排列，比如子任务1。其原因是每次向TreeSet集合中存入一个元素时，就会将该元素与其他元素进行比较，最后将它插入到有序的对象序列中。集合中的元素在进行比较时。都会调用compareTo( )方法，该方法是Comparable接口中定义的，因此要想对集合中的元素进行排序，就必须实现Comparable接口。Java中大部分的类都实现了Comparable 接口，并默认实现了接口中的 CompareTo( )方法，如Integer、Double 和 String 等。

# 向TreeSet集合添加元素机制

模块二 
知识链接

在实际开发中，除了会向TreeSet集合中存储一些Java中默认的类型数据外，还会存储一些用户自定义的类型数据，如 Student 类型数据、Teacher 类型数据等。由于这些自定义类型的数据没有实现Comparable接口，因此也就无法直接在TreeSet集合中进行排序操作。为了解决这个问题，Java提供了两种TreeSet的排序规则，分别为：自然排序和自定义排序。
在默认情况下，TreeSet集合都是采用自然排序，接下来将对这两种排序规则进行详细讲解。

# 向TreeSet集合添加元素机制

模块二 
知识链接

1.自然排序
自然排序要求向 TreeSet.集合中存储的元素所在类必须实现Comparable接口，并重写compareTo( )方法，然后TreeSet集合就会对该类型元素使用compareTo( )方法进行比较，并默认进行升序排序。具体应用见子任务1。
2.自定义排序
有时候，用户自定义的类型数据所在的类没有实现Comparable接口或者对于实现了Comparable接口的类而不想按照定义的compareTo( )方法进行排序。例如，希望存储在TreeSet集合中的字符串可以按照长度而不是英文字母的顺序来进行排序，这时，可以通过在创建 TreeSet集合时就自定义一个比较器来对元素进行定制排序。具体应用见子任务2。

# ，

过渡页

模块三  任务实现

子任务1：创建一个TreeSet集合，向该集合添加元素55、81、99、80；获取首尾元素；比较并获取集合中小于或等于80的最大的一个元素和集合中大于80的最小的一个元素；删除第一个元素。
子任务2：定义Student类并实现Comparable接口，声明属性name和age以及构造方法Student（String name， int age），重写toString( )方法，重写Comparable接口的compareTo( )方法。创建一个TreeSet集合，向该集合添加元素并输出。

模块三 
任务实现

# 任务源码

子任务1：结合任务描述和知识链接中TreeSet类的特有方法知识点可以得到文件9-11所示的代码。

文件9-11 Example10.java

模块三 
任务实现

1import java.util.TreeSet;
2public class Example10 {
3   public static void main（String[] args） {
4      TreeSet ts = new TreeSet（）; // 创建TreeSet集合
// 1、向TreeSet集合中添加元素
5     ts.add（55）;
6     ts.add（81）;
7     ts.add（99）;
8     ts.add（80）;
9     System.out.println（"创建的TreeSet集合为："+ts）;

# 任务源码

子任务1：结合任务描述和知识链接中TreeSet类的特有方法知识点可以得到文件9-11所示的代码。
文件9-11 Example10.java

模块三 
任务实现

// 2、获取首尾元素
10    System.out.println（"TreeSet集合首元素为："+ts.first（））;
11    System.out.println（"TreeSet集合尾部元素为："+ts.last（））;
// 3、比较并获取元素
12   System.out.println（"集合中小于或等于80的最大的一个元素为："+ts.floor（80））; 
13   System.out.println（"集合中大于80的最小的一个元素为："+ts.higher（80））;
// 4、删除元素
14   Object first = ts.pollFirst（）;
15   System.out.println（"删除的第一个元素是："+first）;
16   System.out.println（"删除第一个元素后TreeSet集合变为："+ts）;
17  }
18  }

# 运行结果

模块三 
任务实现

文件9-11的运行结果如图9-19所示。

图9-19 文件9-11的运行结果

# 任务源码

子任务2：结合任务描述和知识链接中自然排序知识点可以得到文件9-12所示的代码。

文件9-12 Example11.java

模块三 
任务实现

1public class Student implements Comparable {
2	private String name;
3	private int age;
4	publicStudent（String name， int age）{
5	  this.name=name;
6	  this.age=age;
7	}
// 重写toString( )方法
8   public String toString（） {
9      return name+":"+age;
10  }

# 任务源码

子任务2：结合任务描述和知识链接中自然排序知识点可以得到文件9-12所示的代码。

文件9-12 Example11.java

模块三 
任务实现

//重写Comparable接口的compareTo( )方法
11  public int compareTo（Object obj） {
12      Student stu = （Student）obj;
   //定义比较方式，先比较age，再比较name
13      if（this.age-stu.age>0）{
14          return 1;
15      }
16      if（this.age-stu.age==0）{
17          return this.name.compareTo（stu.name）;
18      }
19      return -1;
20  }

# 任务源码

子任务2：结合任务描述和知识链接中自然排序知识点可以得到文件9-12所示的代码。

文件9-12 Example11.java

模块三 
任务实现

21 }
22import java.util.TreeSet;
23public class Example11 {
24	public staticvoidmain（String[] args） {
25	TreeSet ts = new TreeSet（）;
26    ts.add（new Student（"Tom"，18））;
27    ts.add（new Student（"Mike"，20））;
28    ts.add（new Student（"Rose"，20））;
29    ts.add（new Student（"Mike"，20））;
30    System.out.println（ts）;
31	}
32 }

# 运行结果

模块三 
任务实现

文件9-12的运行结果如图9-20所示。

图9-20 文件9-12的运行结果

# 感谢关注
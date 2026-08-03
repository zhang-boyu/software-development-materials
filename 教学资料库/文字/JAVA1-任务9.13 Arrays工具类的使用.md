# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务1：创建一个整型数组，调用集合Array的sort( )方法对该整型数组元素进行排序；定义一个输出数组元素的方法；输出排序前的数组元素和排序后的数组元素。
子任务2：在子任务1的基础上，利用二分法查找出集合中某个元素的索引并输出。

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务3：创建一个整型数组int[]arr ={11，32，94，29，88，41，52，69，77}，复制该整型数组元素索引从3到10的元素到新的数组arr2中，并输出数组arr2的所有数组元素。
子任务4：定义一个输出数组元素的方法；创建一个整型数组并输出，用一个指定元素替换该整型数组中的元素并输出。

# ..

模块二 知识链接

Arrays工具类简介

‌‌常用方法

# ‌‌‌常用方法

模块二 
知识链接

1.使用sort( )方法排序
在前面学习数组时，要想对数组进行排序就需要自定义一个排序方法，其实也可以使用Arrays工具类中的静态方法sort（ ）来实现这个功能，格式如下：
Arrays.sort（arr）;

# ‌‌‌常用方法

模块二 
知识链接

2.使用binarySearch( )方法查找元素
在程序开发中，经常会在数组中查找某些特定的元素，如果数组中元素较多时查找某个元素，效率会非常低。为此，Arrays工具类中提供了一个binarySearch( )方法用于查找元素。binarySearch( )方法声明的格式如下：
binarySearch（Object[] a， Object key）;
在上述语法中，参数a是指被查询的集合，参数key指被查询的元素值。binarySearch( )方法只能针对有序数组进行元素查找，因为该方法采用的是二分查找。所谓二分法查找就是每次将指定元素和数组中间位置的元素进行比较，从而排除掉其中的一半元素，这样的查找是非常高效的。

# ‌‌‌常用方法

模块二 
知识链接

3.使用copyOfRange（ ）方法复制元素
在程序开发中，经常需要在不破坏原数组的情况下使用数组中的部分元素，这时可以使用Arrays工具类的copyOfRange( )方法，copyOfRange( )方法可以将数组中指定范围的元素复制到一个新的数组中。copyOfRange( )方法声明格式如下所示。
copyOfRange（int[] original， int from，int to）;
在上述语法中，参数original表示被复制的数组，from表示被复制元素的初始索引（包括），to表示被复制元素的最后索引（不包括）。

# ‌‌‌常用方法

模块二 
知识链接

4.使用fill（ ）方法替换元素
程序开发中，可能会需要将一个数组中的所有元素替换成同一个元素，此时可以使用Arrays工具类的fill( )方法，该方法可以将指定的值赋给数组中的每一个元素，fill( )方法声明如下所示。
fill（Object[] a，Object val）;
在上述语法中，参数a表示被修改的数组，val表示需要被替换成的元素。

# ，

过渡页

模块三  任务实现

子任务1：创建一个整型数组，调用集合Array的sort( )方法对该整型数组元素进行排序；定义一个输出数组元素的方法；输出排序前的数组元素和排序后的数组元素。
子任务2：在子任务1的基础上，利用二分法查找出集合中某个元素的索引并输出。

模块三 
任务实现

# ，

过渡页

模块三  任务实现

子任务3：创建一个整型数组int[]arr ={11，32，94，29，88，41，52，69，77}，复制该整型数组元素索引从3到10的元素到新的数组arr2中，并输出数组arr2的所有数组元素。
子任务4：定义一个输出数组元素的方法；创建一个整型数组并输出，用一个指定元素替换该整型数组中的元素并输出。

模块三 
任务实现

# 任务源码

子任务1：根据任务描述以及sort( )方法排序知识点可以得到文件9-23所示的代码。

文件9-23 Example22.java

模块三 
任务实现

1import java.util.Arrays;
2public class Example22 {
3public static void main（String[] args） {
4   int[]arr ={11，32，94，29，88，41，52，69，77};
5   System.out.print（"排序前："）;
6   printArray（arr）;
7   Arrays.sort（arr）;
8   System.out.print（"排序后："）;
9   printArray（arr）;
10 }

# 任务源码

子任务1：根据任务描述以及sort( )方法排序知识点可以得到文件9-23所示的代码。

文件9-23 Example22.java

模块三 
任务实现

11  public static void printArray（int[] arr） { 
12  System.out.print（"["）;
13  for （int x = 0; x < arr.length; x++） {
14  if （x != arr.length - 1） {
15  System.out.print（arr[x] + "， "）;
16  } 
16 else {
17 System.out.println（arr[x] + "]"）;
18   }
19  }
20 }
21 }

# 运行结果

模块三 
任务实现

文件9-23的运行结果如图9-32所示。

图9-32 文件9-23的运行结果

# 任务源码

子任务2：根据任务描述以及使用binarySearch( )方法查找元素知识点可以得到文件9-24所示的代码。
文件9-24 Example23.java

模块三 
任务实现

1import java.util.Arrays;
2public class Example23 {
3  public static void main（String[] args） {
4    int[]arr ={11，32，94，29，88，41，52，69，77};
5    System.out.print（"排序前："）;
6    printArray（arr）;
7    Arrays.sort（arr）;
8    System.out.print（"排序后："）;
9    printArray（arr）; // 对数组进行排序
10   int index=Arrays.binarySearch（arr， 41）; // 查找指定元素41
11   System.out.println（"元素41的索引是：" + index）;
12 }

# 任务源码

子任务2：根据任务描述以及使用binarySearch( )方法查找元素知识点可以得到文件9-24所示的代码。
文件9-24 Example23.java

模块三 
任务实现

13 public static void printArray（int[] arr） { 
14   System.out.print（"["）;
15   for （int x = 0; x < arr.length; x++） {
16        if （x != arr.length - 1） {
17            System.out.print（arr[x] + "， "）;
18        } 
19        else {
20            System.out.println（arr[x] + "]"）;
21   }
22  }
23 }
24 }

# 运行结果

模块三 
任务实现

文件9-24的运行结果如图9-33所示。

图9-33文件9-24的运行结果

# 任务源码

子任务3：根据任务描述以及使用copyOfRange( )方法复制元素知识点可以得到文件9-25所示的代码。
文件9-25 Example24.java

模块三 
任务实现

1public class Example24 {
2public static void main（String[] args） {
3   int[]arr ={11，32，94，29，88，41，52，69，77};
// 复制一个指定范围索引3-10的数组元素到arr2中
4   int[] arr2 = Arrays.copyOfRange（arr， 3， 10）;
5   for （int i = 0; i < arr2.length; i++） {
6      System.out.print（arr2[i] + " "）;
7  }
8 }
9}

# 运行结果

模块三 
任务实现

文件9-25的运行结果如图9-33所示。

图9-33 文件9-25的运行结果

# 任务源码

子任务4：根据任务描述以及使用fill( )方法替换元素知识点可以得到文件9-26所示的代码。

文件9-26 Example25.java

模块三 
任务实现

1import java.util.Arrays;
2public class Example25 {
3  public static void main（String[] args） {
4    int[]arr ={11，32，94，29，88，41，52，69，77};
5    System.out.print（"替换前的数组："）;
6    printArray（arr）;
7    Arrays.fill（arr， 18）; // 用18替换数组中的每个元素
8    System.out.print（"替换后的数组："）;
9    printArray（arr）;
10  }

# 任务源码

子任务4：根据任务描述以及使用fill( )方法替换元素知识点可以得到文件9-26所示的代码。

文件9-26 Example25.java

模块三 
任务实现

11  public static void printArray（int[] arr） { 
12    System.out.print（"["）;
13    for （int x = 0; x < arr.length; x++） {
14      if （x != arr.length - 1） {
15         System.out.print（arr[x] + "， "）;
16      } 
17      else {
18        System.out.println（arr[x] + "]"）;
19  }
20 }
21}
22}

# 运行结果

模块三 
任务实现

文件9-26的运行结果如图9-34所示。

图9-34 文件9-26的运行结果

# 感谢关注
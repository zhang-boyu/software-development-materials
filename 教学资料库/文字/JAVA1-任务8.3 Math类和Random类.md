# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

子任务1 计算-4的绝对值和4的平方根。
子任务2 求大于4.5的最小整数和小于4.5的最大整数。
子任务3 求2.3和4.5中的较大值和较小值。
子任务4 随机产生10个[0，100)区间的整数。

# ..

模块二 知识链接

Math类

Random类

# Math类

模块二 
知识链接

Math类是一个工具类，类中包含许多用于进行科学计算的方法，如计算一个数的平方根、绝对值或获取一个随机数等。因为Math类构造方法的访问权限是private，所以无法创建Math类的对象。Math类中所有方法都是静态方法，可以直接通过类名调用Math类中的方法。除静态方法外，Math类中还定义了两个静态常量PI和E，分别代表数学中的π和e。

# Math类

模块二 
知识链接

Math类的常用方法如下：

| 方法声明 | 功能描述 |
|---|---|
| abs(double a) | 用于计算a的绝对值 |
| sqrt(double a) | 用于计算a的方根 |
| ceil(double a) | 用于计算大于a的最小整数，并将该整数转化为double型数据。例如Math.ceil(15.2)的值是16.0 |
| floor(double a) | 用于计算小于a的最大整数，并将该整数转化为double型数据。例如Math.ceil(-15.2)的值是-16.0 |
| round(double a) | 用于计算小数a进行四舍五入后的值 |
| max(double a,double b) | 用于返回a和b的较大值 |

# Math类

模块二 
知识链接

Math类的常用方法如下：

| 方法声明 | 功能描述 |
|---|---|
| min(double a,double b) | 用于返回a和b的较小值 |
| random() | 用于生成一个大于0.0小于1.0的随机值（包括0不包括1） |
| sin(double a) | 返回a的正弦值 |
| asin(double a) | 返回a的反正弦值 |
| pow(double a,double b) | 用于计算a的b次幂，即ab的值 |

# Random类

模块二 
知识链接

Random类可以产生指定取值范围的随机数字。Random类提供了两个构造方法，如下表所示。

| 方法声明 | 功能描述 |
|---|---|
| Random() | 使用当前机器时间创建一个Random对象 |
| Random(long seed) | 使用参数seed指定的种子创建一个Random对象 |

# Random类

模块二 
知识链接

Random类的常用方法如下：

| 方法声明 | 功能描述 |
|---|---|
| boolean nextBoolean() | 随机生成boolean类型的随机数 |
| double nextDouble() | 随机生成double类型的随机数 |
| float nextFloat() | 随机生成float类型的随机数 |
| long nextLong() | 随机生成long类型的随机数 |
| int nextInt() | 随机生成int类型的随机数 |
| int nextInt(int n) | 随机生成[0~n)之间int类型的随机数 |

# ，

模块三  任务实现

子任务1 计算-4的绝对值和4的平方根。
子任务2 求大于4.5的最小整数和小于4.5的最大整数。
子任务3 求2.3和4.5中的较大值和较小值。
子任务4 随机产生10个[0，100)区间的整数。

# 子任务1-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

public class Example11 {
    public static void main(String[] args) {
        System.out.println("计算-4的绝对值: " + Math.abs(-4));
        System.out.println("计算4的开平方的结果: "+Math.sqrt(4));
        }
}

# 子任务1-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 子任务2-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

public class Example12 {
    public static void main(String[] args) {
        System.out.println("求大于4.5的最小整数: " + Math.ceil(4.5));
        System.out.println("求小于4.5的最大整数: " + Math.floor(4.5));
    }
}

# 子任务2-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 子任务3-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

public class Example13 {
    public static void main(String[] args) {
    	System.out.println("求2.3和4.5中的较大值: " + Math.max(2.3, 4.5));
   	    System.out.println("求2.3和4.5中的较小值: " + Math.min(2.3, 4.5));
    }
}

# 子任务3-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 子任务4-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

import java.util.Random;
public class Example14 {
    public static void main(String args[]) {
        Random random = new Random(); // 不传入种子
        // 随机产生10个[0,100)之间的整数
        for (int x = 0; x < 10; x++) {
            System.out.println(random.nextInt(100));
        }
    }
}

# 子任务4-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 感谢关注
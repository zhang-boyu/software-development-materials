
## 第1页幻灯片
无锡职业技术学院内部资料
JAVA程序设计项目教程

## 第2页幻灯片
*
任务描述
知识链接
任务实现
目录

## 第3页幻灯片
*
模块一  任务描述
子任务1 计算-4的绝对值和4的平方根。
子任务2 求大于4.5的最小整数和小于4.5的最大整数。
子任务3 求2.3和4.5中的较大值和较小值。
子任务4 随机产生10个[0，100)区间的整数。

## 第4页幻灯片
..
*
模块二 知识链接
Math类
Random类

## 第5页幻灯片
Math类
模块二 
知识链接
Math类是一个工具类，类中包含许多用于进行科学计算的方法，如计算一个数的平方根、绝对值或获取一个随机数等。因为Math类构造方法的访问权限是private，所以无法创建Math类的对象。Math类中所有方法都是静态方法，可以直接通过类名调用Math类中的方法。除静态方法外，Math类中还定义了两个静态常量PI和E，分别代表数学中的π和e。

## 第6页幻灯片
Math类
模块二 
知识链接
Math类的常用方法如下：

## 第7页幻灯片
Math类
模块二 
知识链接
Math类的常用方法如下：

## 第8页幻灯片
Random类
模块二 
知识链接
Random类可以产生指定取值范围的随机数字。Random类提供了两个构造方法，如下表所示。

## 第9页幻灯片
Random类
模块二 
知识链接
Random类的常用方法如下：

## 第10页幻灯片
，
*
模块三  任务实现
子任务1 计算-4的绝对值和4的平方根。
子任务2 求大于4.5的最小整数和小于4.5的最大整数。
子任务3 求2.3和4.5中的较大值和较小值。
子任务4 随机产生10个[0，100)区间的整数。

## 第11页幻灯片
子任务1-代码实现
结合任务描述和知识链接中相关知识点可以得到如下代码。
模块三 
任务实现
public class Example11 {
    public static void main(String[] args) {
        System.out.println("计算-4的绝对值: " + Math.abs(-4));
        System.out.println("计算4的开平方的结果: "+Math.sqrt(4));
        }
}

## 第12页幻灯片
子任务1-运行结果
代码运行结果如图所示:
模块三 
任务实现

## 第13页幻灯片
子任务2-代码实现
结合任务描述和知识链接中相关知识点可以得到如下代码。
模块三 
任务实现
public class Example12 {
    public static void main(String[] args) {
        System.out.println("求大于4.5的最小整数: " + Math.ceil(4.5));
        System.out.println("求小于4.5的最大整数: " + Math.floor(4.5));
    }
}

## 第14页幻灯片
子任务2-运行结果
代码运行结果如图所示:
模块三 
任务实现

## 第15页幻灯片
子任务3-代码实现
结合任务描述和知识链接中相关知识点可以得到如下代码。
模块三 
任务实现
public class Example13 {
    public static void main(String[] args) {
    	System.out.println("求2.3和4.5中的较大值: " + Math.max(2.3, 4.5));
   	    System.out.println("求2.3和4.5中的较小值: " + Math.min(2.3, 4.5));
    }
}

## 第16页幻灯片
子任务3-运行结果
代码运行结果如图所示:
模块三 
任务实现

## 第17页幻灯片
子任务4-代码实现
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

## 第18页幻灯片
子任务4-运行结果
代码运行结果如图所示:
模块三 
任务实现

## 第19页幻灯片
感谢关注
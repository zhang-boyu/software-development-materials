
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
子任务1 使用Instant类中的方法从系统中获取当前的时刻。
子任务2 使用LocalData类中的方法获取当前的年份、月份和获取的当天为本月的第几天。

## 第4页幻灯片
..
*
模块二 知识链接
Instant类
LocalData类

## 第5页幻灯片
Instant类
模块二 
知识链接
Instant 类代表的是某个瞬间的时间。其内部由两个部分组成，第一部分保存的是标准Java计算时代（就是1970年1月1日开始）到现在的秒数，第二部分保存的是纳秒数。

## 第6页幻灯片
Instant类
模块二 
知识链接
Instant类的常用方法：

## 第7页幻灯片
LocalData类
模块二 
知识链接
LocalDate类表示不带时区的日期，它所表示的日期包括年份和月份两部分。LocalDate类不能代表时间线上的即时信息，只是描述日期。LocalDate类提供了两个获取日期对象的方法now()和of(int year, int month, int dayOfMonth)，具体如下所示。

## 第8页幻灯片
LocalData类
模块二 
知识链接
LocalData类的常用方法：

## 第9页幻灯片
LocalData类
模块二 
知识链接
LocalData类的常用方法：

## 第10页幻灯片
LocalData类
模块二 
知识链接
LocalData类的常用方法：

## 第11页幻灯片
，
*
模块三  任务实现
子任务1 使用Instant类中的方法从系统中获取当前的时刻。
子任务2 使用LocalData类中的方法获取当前的年份、月份和获取的当 	 天为本月的第几天。

## 第12页幻灯片
子任务1-代码实现
结合任务描述和知识链接中相关知识点可以得到如下代码。
模块三 
任务实现
import java.time.Instant;
public class Example19 {
    public static void main(String[] args) {
        //  Instant 类的时间戳类从1970-01-01 00:00:00 截止到当前时间的毫秒值
        Instant now = Instant.now();
        System.out.println("从系统获取的当前时刻为："+now);
    }
}

## 第13页幻灯片
子任务1-运行结果
代码运行结果如图所示:
模块三 
任务实现

## 第14页幻灯片
子任务2-代码实现
结合任务描述和知识链接中相关知识点可以得到如下代码。
模块三 
任务实现
import java.time.LocalDate;
public class Example20 {
    public static void main(String[] args) {
        //获取日期时分秒
        LocalDate now = LocalDate.now();
        LocalDate of = LocalDate.of(2015, 12, 12);
        System.out.println("从LocalDate实例获取当前的年份是："+now.getYear());
        System.out.println("从LocalDate实例获取当前的月份是：" +now.getMonthValue());
        System.out.println("从LocalDate实例获取当天为本月的第几天：" +now.getDayOfMonth());
  } }

## 第15页幻灯片
子任务2-运行结果
代码运行结果如图所示:
模块三 
任务实现

## 第16页幻灯片
感谢关注
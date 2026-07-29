
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
子任务1 使用Duration类中的方法计算两个时间的间隔。
子任务2 使用Period类中方法计算了两个日期的间隔。

## 第4页幻灯片
..
*
模块二 知识链接
Duration类
Period类

## 第5页幻灯片
Duration类
模块二 
知识链接
Duration类表示两个时间之间的间隔，间隔时间的单位可以是天、时、分、秒、毫秒和纳秒，例如今天的12:00:00与13:00:00之间，间隔1小时，或者60分钟，或者3600秒。

## 第6页幻灯片
Duration类
模块二 
知识链接
Duration类的常用方法：

## 第7页幻灯片
Period类
模块二 
知识链接
Period类主要用于计算两个日期的间隔，与Duration类相同，Period类也是通过between()方法计算日期间隔，并提供了获取年月日的三个常用方法，分别是 getYears()、getMonths()和getDays()。

## 第8页幻灯片
，
*
模块三  任务实现
子任务1 使用Duration类中的方法计算两个时间的间隔。
子任务2 使用Period类中方法计算了两个日期的间隔。

## 第9页幻灯片
子任务1-代码实现
结合任务描述和知识链接中相关知识点可以得到如下代码。
模块三 
任务实现
import java.time.Duration;
import java.time.LocalTime;
public class Example23 {
    public static void main(String[] args) {
        LocalTime start = LocalTime.now();
        LocalTime end = LocalTime.of(20,13,23);
        Duration duration = Duration.between(start, end);
        //间隔的时间
        System.out.println("时间间隔为："+duration.toNanos()+"纳秒");
        System.out.println("时间间隔为："+duration.toMillis()+"毫秒");
        System.out.println("时间间隔为："+duration.toHours()+"小时"); } }

## 第10页幻灯片
子任务1-运行结果
代码运行结果如图所示:
模块三 
任务实现

## 第11页幻灯片
子任务2-代码实现
结合任务描述和知识链接中相关知识点可以得到如下代码。
模块三 
任务实现
import java.time.LocalDate;
import java.time.Period;
public class Example24 {
    public static void main(String[] args) {
        LocalDate birthday = LocalDate.of(2018, 12, 12);
        LocalDate now = LocalDate.now();
        //计算两个日期的间隔
        Period between = Period.between(birthday, now);
        System.out.println("时间间隔为"+between.getYears()+"年");
        System.out.println("时间间隔为"+between.getMonths()+"月");
        System.out.println("时间间隔为"+between.getDays()+"天");  }  }

## 第12页幻灯片
子任务2-运行结果
代码运行结果如图所示:
模块三 
任务实现

## 第13页幻灯片
感谢关注
# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

子任务1 使用Duration类中的方法计算两个时间的间隔。
子任务2 使用Period类中方法计算了两个日期的间隔。

# ..

模块二 知识链接

Duration类

Period类

# Duration类

模块二 
知识链接

Duration类表示两个时间之间的间隔，间隔时间的单位可以是天、时、分、秒、毫秒和纳秒，例如今天的12:00:00与13:00:00之间，间隔1小时，或者60分钟，或者3600秒。

# Duration类

模块二 
知识链接

Duration类的常用方法：

| 方法声明 | 功能描述 |
|---|---|
| between(Temporal startInclusive, Temporal endExclusive) | 获取一个Duration实例，表示两个时间对象之间的持续时间 |
| toDays() | 将间隔时间转换为以天为单位 |
| toHours() | 将间隔时间转换为以时为单位 |
| toMinutes() | 将间隔时间转换为以分钟为单位 |
| toMillis() | 将间隔时间转换为以毫秒为单位 |
| toNanos() | 将间隔时间转换为以纳秒为单位 |

# Period类

模块二 
知识链接

Period类主要用于计算两个日期的间隔，与Duration类相同，Period类也是通过between()方法计算日期间隔，并提供了获取年月日的三个常用方法，分别是 getYears()、getMonths()和getDays()。

# ，

模块三  任务实现

子任务1 使用Duration类中的方法计算两个时间的间隔。
子任务2 使用Period类中方法计算了两个日期的间隔。

# 子任务1-代码实现

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

# 子任务1-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 子任务2-代码实现

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

# 子任务2-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 感谢关注
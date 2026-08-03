# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

子任务1 使用LocalTime类中的方法获取当前时间，包含毫秒数。
子任务2 使用LocalDataTime类中方法获取系统当前年月日时分秒。

# ..

模块二 知识链接

LocalTime类

LocalDataTime类

# LocalTime类

模块二 
知识链接

LocalTime类用来表示时间，通常表示的是小时分钟秒。与LocalDate类一样，LocalTime类不能代表时间线上的即时信息，只是时间的描述。LocalTime类中提供了获取时间对象的方法，与LocalDate类用法类似。
此外，LocalTime类也提供了时间格式化、增减时分秒等常用方法，这些方法与LocalDate类的方法用法相同，这里不再详细列举。

# LocalDataTime类

模块二 
知识链接

LocalDateTime类是LocalDate类与LocalTime类的综合，它既包含日期也包含时间，查看Java API可以知道，LocalDateTime类包含了LocalDate类与LocalTime类的所有方法。
LocalDateTime类表示不带时区的日期和时间，默认的日期时间格式是年-月-日T时:分:秒.纳秒，这与日常使用的日期时间格式不太符合，所以LocalDateTime类通常和DataTimeFormatter类一起使用，DataTimeFormatter类用于指定日期时间格式。LocalDateTime类还额外提供了日期时间的转换方法。

# ，

模块三  任务实现

子任务1 使用LocalTime类中的方法获取当前时间，包含毫秒数。
子任务2 使用LocalDataTime类中方法获取系统当前年月日时分秒。

# 子任务1-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

import java.time.LocalTime;
import java.time.format.DateTimeFormatter;
public class Example21 {
    public static void main(String[] args) {
        // 获取当前时间，包含毫秒数
        LocalTime time = LocalTime.now();
        LocalTime of = LocalTime.of(9,23,23);
        System.out.println("从LocalTime获取的小时为："+time.getHour());
        System.out.println("将获取到的LoacalTime实例格式化为："+
                time.format(DateTimeFormatter.ofPattern("HH:mm:ss")));
  } }

# 子任务1-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 子任务2-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;
public class Example22 {
    public static void main(String[] args) {
        //获取系统当前年月日时分秒
        LocalDateTime now = LocalDateTime.now();
        System.out.println("获取的当前日期时间为:"+now);
        System.out.println("将目标LocalDateTime转换为相应的LocalDate实例:"+
                now.toLocalDate());

# 子任务2-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

System.out.println("将目标LocalDateTime转换为相应的LocalTime实例:"+
                now.toLocalTime());
        //指定格式
        DateTimeFormatter ofPattern = DateTimeFormatter.ofPattern
                ("yyyy年MM月dd日 HH时mm分ss秒");
        System.out.println("格式化后的日期时间为:"+now.format(ofPattern));
    }
}

# 子任务2-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 感谢关注
# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

子任务1 使用Instant类中的方法从系统中获取当前的时刻。
子任务2 使用LocalData类中的方法获取当前的年份、月份和获取的当天为本月的第几天。

# ..

模块二 知识链接

Instant类

LocalData类

# Instant类

模块二 
知识链接

Instant 类代表的是某个瞬间的时间。其内部由两个部分组成，第一部分保存的是标准Java计算时代（就是1970年1月1日开始）到现在的秒数，第二部分保存的是纳秒数。

# Instant类

模块二 
知识链接

Instant类的常用方法：

| 方法声明 | 功能描述 |
|---|---|
| now() | 从系统时钟获取当前瞬间的时间。 |
| now(Clock clock) | 从指定时钟获取当前时刻。 |
| ofEpochSecond(long epochSecond) | 使用从自标准Java计算时代开始的秒数获取一个Instant的实例。 |
|---|---|
| ofEpochMilli(long epochMilli) | 从1970-01-01T00:00:00Z的纪元中使用毫秒获取Instant的实例。 |
| getEpochSecond() | 从1970-01-01T00:00:00Z的Java时代获取秒数。 |
| getNano() | 用于从第二秒开始在此瞬间表示的时间轴中返回纳秒数。 |
| parse(CharSequence text) | 从一个时间文本字符串（如2007-12-03T10:15:30.00Z）获取一个Instant的实例。 |
| from(TemporalAccessor tenporal) | 从时间对象获取一个Instant的实例。 |

# LocalData类

模块二 
知识链接

LocalDate类表示不带时区的日期，它所表示的日期包括年份和月份两部分。LocalDate类不能代表时间线上的即时信息，只是描述日期。LocalDate类提供了两个获取日期对象的方法now()和of(int year, int month, int dayOfMonth)，具体如下所示。

# LocalData类

模块二 
知识链接

LocalData类的常用方法：

| 方法声明 | 功能描述 |
|---|---|
| getYear() | 获取年份字段 |
| getMonth() | 使用Month枚举获取月份字段 |
| getMonthValue() | 获取当前日期的月份 |
| getDayOfMonth() | 获取当月第几天字段 |
| format(DateTimeFormatter formatter) | 使用指定的格式化程序格式化此日期 |
| isBefore(ChronoLocalDate other) | 检查此日期是否在指定日期之前 |

# LocalData类

模块二 
知识链接

LocalData类的常用方法：

| 方法声明 | 功能描述 |
|---|---|
| isAfter(ChronoLocalDate other) | 检查此日期是否在指定日期之后 |
| isEqual(ChronoLocalDate other) | 检查此日期是否等于指定的日期 |
| isLeapYear() | 根据ISO培训日历系统规则，检查年份是否是闰年 |
| parse(CharSequence text) | 从一个文本字获取一个 LocalDate的实例 |
| parse(CharSequence text, DateTimeFormatter formatter) | 使用特定格式格式化 LocalDate从文本字符串获取的 LocalDate实例 |
| plusYears(long yearsToAdd) | 增加指定年份 |
| plusMonths(long monthsToAdd) | 增加指定月份 |

# LocalData类

模块二 
知识链接

LocalData类的常用方法：

| 方法声明 | 功能描述 |
|---|---|
| plusDays(long daysToAdd) | 增加指定日数 |
| minusYears(long yearsToSubtract) | 减少指定年份 |
| minusMonths(long monthsToSubtract) | 减少指定月份 |
| minusDays(long daysToSubtract) | 减少指定日数 |
| withYear(int year) | 指定年 |
| withMonth(int month) | 指定月 |
| withDayOfYear(int dayOfYear) | 指定日 |

# ，

模块三  任务实现

子任务1 使用Instant类中的方法从系统中获取当前的时刻。
子任务2 使用LocalData类中的方法获取当前的年份、月份和获取的当 	 天为本月的第几天。

# 子任务1-代码实现

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

# 子任务1-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 子任务2-代码实现

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

# 子任务2-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 感谢关注
# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

子任务1：用Data类中的方法获取当前日期和时间以及当前日期和时间后1s的时间。
子任务2：用Calendar类中的方法获取当前的年月日时分秒。

# ..

模块二 知识链接

Data类

Calendar类

# Data类

模块二 
知识链接

JDK的java.util包提供了一个Date类用于表示日期和时间，Date类在JDK 1.0时就已经开始使用。随着JDK版本的不断升级和发展，Date类中大部分的构造方法和普通方法都已经不再推荐使用。在JDK 11中，Date类只有下面两个构造方法是实际开发中经常被应用到的。
 Date()：用于创建当前日期时间的Date对象。
 Date(long date)：用于创建指定时间的Date对象，其中date参数表示1970年1月1日0时0分0（称为历元）以来的毫秒数，即时间戳。

# Calendar类

模块二 
知识链接

使用Date类可以获取计算机的当前日期和时间，但是Date类输出的日期格式不符合国内的日期标准格式。所以从 JDK 1.1 开始，Java提供了Calendar类，用Calendar类中的方法取代了Date类的相应功能。Calendar类也用于完成日期和时间字段的操作，它可以通过特定的方法设置和读取日期的特定部分，比如年、月、日、时、分、秒等。

# Calendar类

模块二 
知识链接

Calendar类是一个抽象类，不可以被实例化，如果想在程序中获取一个Calendar实例，则需要调用Calendar类的静态方法getInstance()。通过调用getInstance()方法获取Calendar实例的具体示例如下。

# Calendar类

模块二 
知识链接

Calendar类的常用方法：

| 方法声明 | 功能描述 |
|---|---|
| int get(int field) | 返回指定日历字段field的值 |
| void add(int field,int amount) | 根据日历规则，为指定的日历字段增加或减去指定的时间量 |
| void set(int field,int value) | 将指定日历字段field的值设置为value |
| void set(int year,int month,int date) | 设置Calendar对象的年、月、日三个字段的值 |
| void set(int year.int month,int date,int hourOfDay,int minute,int second) | 设置Calendar对象的年、月、日、时、分、秒六个字段的值 |

# Calendar类

模块二 
知识链接

表中的大多数方法都用到了int类型的参数field，该参数需要接收Calendar类中定义的常量值，这些常量值分别表示不同的字段，Calendar类常用的常量值如下所示。
Calendar.YEAR：用于获取当前年份。
Calendar.MONTH：用于获取当前月份，需要注意的是，在使Calendar.MONTH
             字段时，月份的起始值是从0开始的，而不是从1开始，因此要获取当前的月
             需要在Calendar.MONTH的基础上加1。
Calendar.DATE：用于获取当前日。
Calendar.HOUR：用于获取时。
Calendar.MINUTE：用于获取分。
Calendar.SECOND：用于获取秒。

# ，

模块三  任务实现

子任务1：用Data类中的方法获取当前日期和时间以及当前日期和时间后1s的时间。
子任务2：用Calendar类中的方法获取当前的年月日时分秒。

# 子任务1-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

import java.util.Date;
public class Example17 {
    public static void main(String[] args) {
        // 创建表示当前时间的Date对象
        Date date1 = new Date();
        // 获取当前时间后1秒的时间
        Date date2 = new Date(System.currentTimeMillis() + 1000);
        System.out.println(date1);
        System.out.println(date2);
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

import java.util.Calendar;
public class Example18 {
    public static void main(String[] args) {
        // 获取表示当前时间的Calendar对象
        Calendar calendar = Calendar.getInstance();
        int year = calendar.get(Calendar.YEAR);       // 获取当前年份
        int month = calendar.get(Calendar.MONTH) + 1; // 获取当前月份
        int date = calendar.get(Calendar.DATE);       // 获取当前日
        int hour = calendar.get(Calendar.HOUR);       // 获取时

# 子任务2-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

int minute = calendar.get(Calendar.MINUTE);   // 获取分
        int second = calendar.get(Calendar.SECOND);   // 获取秒
        System.out.println("当前时间为:" + year + "年 " + month + "月 "
                + date + "日 "+ hour + "时 " + minute + "分 " + second + "秒");
    }
}

# 子任务2-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 感谢关注
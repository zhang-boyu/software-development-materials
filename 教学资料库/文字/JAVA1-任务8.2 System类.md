# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

子任务1：使用arraycopy( )方法用于将源数组中的元素复制到目标数   	组。
子任务2：使用currentTimeMillis( )方法用于获取当前系统的时间，		返回值类型是long。
子任务3：使用getProperties( )方法用于获取当前系统的全部属性。		使用getProperty( )方法可以根据系统的属性名获取对应的属性值。
子任务4：使用System.gc( )方法通知Java虚拟机立即进行垃圾回收。

# ..

模块二 知识链接

System类

# System类

模块二 
知识链接

在之前所学知识中，需要打印结果时，使用的打印语句“System.out.println（）;”中就用到了System类。System类定义了一些与系统相关的属性和方法，它提供的属性和方法都是静态的，因此，可以使用System类直接引用类中的属性和方法。

# System类

模块二 
知识链接

System类的常用方法如下：

| 方法名称 | 功能描述 |
|---|---|
| static void exit(int status) | 该方法用于终止当前正在运行的Java虚拟机，其中参数status表示状态码，若状态码非0 ，则表示异常终止 |
| static void gc() | 运行垃圾回收器，并对内存中的垃圾进行回收 |
| static void currentTimeMillis() | 返回以毫秒为单位的当前时间 |
| static void arraycopy(Object src,int srcPos,Object dest,int destPos,int length) | 从src引用的指定源数组的srcPos位置，复制length个元素，到dest引用的数组的destPos位置 |
| static Properties getProperties() | 获取当前系统全部属性 |
| static String getProperty(String key) | 获取指定键描述的系统属性 |

# ，

过渡页

模块三  任务实现

模块三 
任务实现

子任务1：使用arraycopy( )方法用于将源数组中的元素复制到目标数   	组。
子任务2：使用currentTimeMillis( )方法用于获取当前系统的时间，		返回值类型是long。
子任务3：使用getProperties( )方法用于获取当前系统的全部属性。		使用getProperty( )方法可以根据系统的属性名获取对应的属性值。
子任务4：使用System.gc( )方法通知Java虚拟机立即进行垃圾回收。

# 子任务1-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

public class Example07 {
    public static void main(String[] args) {
        int[] fromArray = { 10, 11, 12, 13, 14, 15 };    // 源数组
        int[] toArray = { 20, 21, 22, 23, 24, 25, 26 }; // 目标数组
        System.arraycopy(fromArray, 2, toArray, 3, 4);  // 复制数组元素
        // 打印复制后数组的元素
        System.out.println("复制后的数组元素为：");
        for (int i = 0; i < toArray.length; i++) {
            System.out.print(toArray[i]+" ");
 }  }  }

# 子任务1-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 子任务2-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

public class Example08 {
    public static void main(String[] args) {
        long startTime = System.currentTimeMillis();// 循环开始时的当前时间
        int sum = 0;
        for (int i = 0; i < 1000000000; i++) {
            sum += i;
        }
        long endTime = System.currentTimeMillis();// 循环结束后的当前时间
        System.out.println("程序运行的时间为："+(endTime - startTime)+
                "ms");
} }

# 子任务2-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 子任务3-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

import java.util.Enumeration;
import java.util.Properties;
public class Example09{
    public static void main(String[] args) {
        // 获取当前系统属性
        Properties properties = System.getProperties();
        // 获取所有系统属性的key，返回Enumeration对象
        Enumeration propertyNames = properties.propertyNames();

# 子任务3-代码实现

模块三 
任务实现

while (propertyNames.hasMoreElements()) {
            // 获取系统属性的键key
            String key = (String) propertyNames.nextElement();
            // 获取当前键key对应的值value
            String value = System.getProperty(key);
            System.out.println(key + "--->" + value);
        }
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

class Person{
    private String name;
    private int age;
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    //    System.out.println("对象被创建-->"+this);
    }

# 子任务4-代码实现

模块三 
任务实现

@Override
    public String toString() {
        return "姓名:"+this.name+"，年龄:"+this.age;
    }
    // 下面定义的finalize()方法会在垃圾回收前被调用
    public void finalize() throws Throwable {
        System.out.println("对象被释放-->"+this);
    }
}

# 子任务4-代码实现

模块三 
任务实现

public class Example10{
    public static void main(String[] args){
        // 下面是创建Person对象
       Person p = new Person("张三",20);
        // 下面将变量置为null，让对象p成为垃圾
        p = null;
        // 调用方法进行垃圾回收
        System.gc();
        for (int i = 0; i < 10000000; i++) {
            // 为了延长程序运行的时间，执行空循环
        }  }  }

# 子任务4-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 感谢关注
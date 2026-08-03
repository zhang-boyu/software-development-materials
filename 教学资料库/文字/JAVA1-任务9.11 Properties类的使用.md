# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

创建一个Properties类的对象，设置该对象的属性如下：Backgroup-color：blue；Font-size：16px；Language：chinese；通过遍历输出Properties类对象的键和值。

# ..

模块二 知识链接

‌Properties类

‌‌Properties类常用方法

# Properties类

模块二 
知识链接

‌Properties类是Java中用于处理配置文件的一个实用工具类，它继承自Hashtable，具备键值对的存储结构。Properties类主要用于读取和写入配置信息，广泛应用于配置文件的读写、数据库连接参数的管理、国际化资源的管理等场景。Properties主要用于存储字符串类型的键和值。

# ‌‌Properties类常用方法

模块二 
知识链接

（1）设置属性方法：setProperty（）
使用setProperty方法添加或修改属性，如：
Properties p=new Properties（）;  
p.setProperty（"database.username"， "user123"）;
（2）获取属性方法：getProperty（）
使用getProperty方法按键名获取对应的值，如：
Properties p=new Properties（）;  
String value = p.getProperty（"key1"）;
如果指定的键不存在，也可以提供一个默认值，如：Properties p=new Properties（）;
String value=p.getProperty（"key2"， "defaultValue"）;

# ，

过渡页

模块三  任务实现

创建一个Properties类的对象，设置该对象的属性如下：Backgroup-color：blue；Font-size：16px；Language：chinese；通过遍历输出Properties类对象的键和值。

模块三 
任务实现

# 任务源码

根据任务描述以及‌Properties类常用方法知识点可以得到文件9-20所示的代码。
文件9-20 Example19.java

模块三 
任务实现

1import java.util.*;
2public class Example19 {
3public static void main（String[] args） {
4   Properties p=new Properties（）; // 创建Properties对象
5   p.setProperty（"Backgroup-color"， "blue"）;
6   p.setProperty（"Font-size"， "16px"）;
7   p.setProperty（"Language"， "chinese"）;
8   Enumeration names = p.propertyNames（）;//获取Enumeration对象所有键枚举
9   while（names.hasMoreElements（））{ //循环遍历所有的键
10      String key=（String） names.nextElement（）;
11      String value=p.getProperty（key）; // 获取对应键的值
12      System.out.println（key+" = "+value）;
13  }
14 }
15 }

# 运行结果

模块三 
任务实现

文件9-20的运行结果如图9-29所示。

图9-29 文件9-19的运行结果

# 感谢关注
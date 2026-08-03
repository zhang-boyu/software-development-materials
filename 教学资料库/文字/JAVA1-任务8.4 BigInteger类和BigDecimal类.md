# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

子任务1 计算用BigInteger定义的两个大整数的和、差、积、商，并比较出两个数字的较大值与较小值。
子任务2 计算用BigDecimal定义的两个小数的和、差、积、商，并比较出两个数字的较大值与较小值。

# ..

模块二 知识链接

BigInteger类

BigDecimal类

# BigInteger类

模块二 
知识链接

当程序需要处理一个非常大的整数时，如果这个数值超出了long类型的取值范围，则无法使用基本类型接收。早期程序开发者使用String类进行大整数的接收，使用String类接收大整数之后，再采用拆分的方式进行计算，操作过程非常麻烦。为了解决这个问题，Java提供了BigInteger类。BigInteger表示大整数类，定义在java.math包中，如果在开发时需要定义一个超出long类型的整型数据，可以使用BigInteger类的对象接收该数据。

# BigInteger类

模块二 
知识链接

BigInteger类的常用方法如下：

| 方法声明 | 功能描述 |
|---|---|
| BigInteger(String val) | 将字符串val变为BigInteger类型的数据 |
| BigInteger add(BigInteger val) | 返回当前对象与val的和 |
| BigInteger subtract(BigInteger val) | 返回当前对象与val的差 |
| BigInteger multiply(BigInteger val) | 返回当前对象与val的积 |
| BigInteger divide(BigInteger val) | 返回当前对象与val的商 |

# BigInteger类

模块二 
知识链接

BigInteger类的常用方法如下：

| 方法声明 | 功能描述 |
|---|---|
| BigInteger max(BigInteger val) | 返回当前对象与val之中的较大值 |
| BigInteger min(BigInteger val) | 返回当前对象与val之中的较小值 |
| BigInteger[] divideAndRemainder(BigInteger val) | 除法操作，计算当前对象/val的结果，返回一个数组，数组的第1个元素为商，第2个元素为余数 |

# BigDecimal类

模块二 
知识链接

在进行浮点数运算的时候，float类型和double类型很容易丢失精度，为了能够精确的表示、计算浮点数，Java提供了BigDecimal类。BigDecimal类可以表示任意精度的小数，多用于数字精度要求高的场景，例如商业计算、货币值计算等。

# BigDecimal类

模块二 
知识链接

BigDecimal类的常用方法如下：

| 方法声明 | 功能描述 |
|---|---|
| BigDecimal BigDecimal(String val) | 将字符串val转为BigDecimal类型的数据 |
| static BigDecimal valueOf(double d) | 将double类型的数据转为BigDecimal类型的数据 |
| BigDecimal add(BigDecimal val) | 返回当前对象与val的和 |
| BigDecimal subtract(BigDecimal val) | 返回当前对象与val的差 |
| BigDecimal multiply(BigDecimal val) | 返回当前对象与val的积 |
| BigDecimal divide(BigDecimal val) | 返回当前对象与val的商 |
| BigDecimal max(BigDecimal val) | 返回当前对象与val之中的较大值 |
| BigDecimal min(BigDecimal val) | 返回当前对象与val之中的较小值 |

# ，

模块三  任务实现

子任务1 计算用BigInteger定义的两个大整数的和、差、积、商，并比较出两个数字的较大值与较小值。
子任务2 计算用BigDecimal定义的两个小数的和、差、积、商，并比较出两个数字的较大值与较小值。

# 子任务1-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

import java.math.BigInteger;
public class Example15 {
    public static void main(String[] args) {
        BigInteger bi1 = new BigInteger("123456789");  // 创建BigInteger对象
        BigInteger bi2 = new BigInteger("987654321");  // 创建BigInteger对象
        System.out.println("bi2与bi1的和: " + bi2.add(bi1));
        System.out.println("bi2与bi1的差: " + bi2.subtract(bi1));
        System.out.println("bi2与bi1的积: " + bi2.multiply(bi1));

# 子任务1-代码实现

模块三 
任务实现

System.out.println("bi2与bi1的商: " + bi2.divide(bi1));
        System.out.println("bi2与bi1之间的较大值: " + bi2.max(bi1));
        System.out.println("bi2与bi1之间的较小值: " + bi2.min(bi1));
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

import java.math.BigDecimal;
public class Example16 {
    public static void main(String[] args) {
        BigDecimal bd1 = new BigDecimal("0.001");  // 创建BigDecimal对象
        BigDecimal bd2 = BigDecimal.valueOf(0.009);// 创建BigDecimal对象
        System.out.println("bd2与bd1的和: " + bd2.add(bd1));
        System.out.println("bd2与bd1的差: " + bd2.subtract(bd1));
        System.out.println("bd2与bd1的积: " + bd2.multiply(bd1));

# 子任务2-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

System.out.println("bd2与bd1的商: " + bd2.divide(bd1));
        System.out.println("bd2与bd1之间的较大值: " + bd2.max(bd1));
        System.out.println("bd2与bd1之间的较小值: " + bd2.min(bd1));
    }
}

# 子任务2-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 感谢关注
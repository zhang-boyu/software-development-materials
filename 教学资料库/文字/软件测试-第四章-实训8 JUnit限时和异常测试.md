JUnit限时和异常测试实训指导书

# 任务说明

## 1.1任务内容

根据指导书，学习JUnit限时和异常测试方法的使用。

## 1.2知识点/技能点

学习JUnit限时和异常测试方法。

## 1.3任务目标

对JUnit的限时和异常测试方基本使用进行练习，正确结果对照—实训任务答案。

# 任务准备

## 2.1 背景知识

在实际测试中，测试一些逻辑复杂、循环嵌套较深的程序，很可能会出现死循环，进入死循环就无法自动终止。因此在测试中需要采取一些预防措施，@Test注解提供1个参数“timeout”可以使用在该场景。使用“timeout”就是给测试函数设定一个执行时间，如果测试运行时间长于定义的时间，执行方法会被系统强行终止，测试失败。并且系统还会汇报该测试方法是因为超时才结束。@Test(timeout = 1000)表示如1000ms未执行完成，就因为超时而自动终止。

在开发过程中，JAVA中的异常处理也是重点，异常的捕获、抛出和异常处理是维持代码健壮性的重要条件，灵活使用异常以及处理异常，不仅能最大限度的避免出错而且也能增加软件的容错能力。在进行单元测试时，我们除了需要测试正常流程和正确的程序功能置外，可能还需要测试异常场景。如果一个函数应该抛出异常但是却没有抛出异常这说明程序有Bug。在JUnit中@Test注解提供一个参数测试异常情况，@Test(expected…)定义测试方法应该抛出的异常类型，如果方法调用中抛出了这个异常则测试通过，如果测试方法没有抛出异常或者抛出了一个不同的异常，测试失败。

步骤：

被测代码段：

public class TimeException {

private static int result;

//无限while循环

public void time(){

while(true);

}

public void divide(int m, int n) {

result = m / n;

}

public int getResult() {

return result;

}

}

测试类代码段：

超时设置timeout=1000，1000毫秒未执行完成显示测试失败；

除法输入数据计算后如为ArithmeticException类异常，测试成功。（ArithmeticException为"数学运算异常"）

import org.junit.Test;

public class TimeExceptionTest {

private static TimeException timeexception = new TimeException();

@Test(timeout=1000)

public void testTime() {

timeexception.time();

}

@Test(expected = ArithmeticException.class)

public void testDivide() {

timeexception.divide(10, 0);

}

}

执行结果：

testTime执行失败。testDivide执行成功

# 任务步骤

按照上面的JUnit限时和异常测试知识讲解，根据下面的代码段按照要求来设计测试类。

要求如下：

sum测试方法设置超时时间为500毫秒；

array测试方法传入数组下标越界，判断数组下标越界异常。

public class TimeException {

private static String result;

public void sum(){

for(;;);

}

public void array(int m) {

String[] array = {"abc","def","ghi","gkl"};

result = array[m];

}

public String getResult() {

return result;

}

}

# 任务总结

通过本次实训，完成JUnit限时和异常测试的使用，为进行白盒测试奠定基础。实训难度较低，知识点主要在于了解限时和异常测试的使用场景和使用方法，要求学生熟练掌握JUnit限时和异常测试的知识点。

# 考核标准

教师可以参考下列标准对学生成绩评分。满分为100分。

参考的评分表如下：

| 项次 | 内     容 | 分 值 | 评分细则 | 分 数 |
|---|---|---|---|---|
| 1 | 运行结果 | 100 | 与答案一致，运行结果通过 |  |
| 评鉴教师
评审意见 | 评鉴教师
评审意见 | 分 数 总 计： | 分 数 总 计： | 分 数 总 计： |
| 评鉴教师
评审意见 | 评鉴教师
评审意见 |  |  |  |
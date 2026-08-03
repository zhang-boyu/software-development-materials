JUnit中Failure和Error讲解实训指导书

# 任务说明

## 1.1任务内容

根据指导书，学习JUnit中Failure和Error的区别。

## 1.2知识点/技能点

学习JUnit中的Failure和Error。

## 1.3任务目标

对JUnit的Failure和Error进行学习，正确结果对照—实训任务答案。

# 任务准备

## 2.1 背景知识

在执行测试时，我们会发现有Failure和Error两种测试未通过的信息。下面我们讲解下这两种测试未通过信息的区别。

Failure指的是测试失败，就是预期的结果与实际运行结果不同而导致的失败。例如当使用assertXXX()方法断言失败时，就会报Failure。表示所测试的单元方法中的逻辑设计可能有问题，也就是被测的单元代码可能没有正确的实现设计上所要求的功能。或者预期结果表达错误。排除了预期结果错误的情况下这时候就需要检查单元测试方法中的逻辑设计是否有误。

Error指的是测试程序本身出错，代码异常引起的，测试程序中没有考虑到的情况，在断言之前程序就代码异常而终止。例如存取某个阵列因为超过索引而引发数组越界异常。或者传入数值类型不正确等。这会使单元测试无法正确完成，在测试运行到assertXXX()前就提前结束，这时候就需要检查单元方法中的的设计是否有误。

如果JUnit测试后报告有若干的Failure和Error，我们应该首先查找产生Error的原因，并加以修复，保证测试程序正确。在修复Error之后，重新执行JUnit测试，如果Error问题全部解决，我们在对Failure进行查找原因和修复。

通过下面实例对Failure进行讲解

准备需测试类

代码段：

add()方法为加法，计算两个值相加求和。substract()方法为减法，计算两个值详见求差。

public class Calculator {

private static int result;

public void add(int m, int n) {

result = m + n;

}

public void substract(int m, int n) {

result = m - n - 1;

}

public void clear() {

result = 0;

}

public int getResult() {

return result;

}

}

编写测试类

代码段：

import static org.junit.Assert.*;

import org.junit.After;

import org.junit.Before;

import org.junit.Test;

public class CalculatorTest {

private static Calculator calculator = new Calculator();

@Before

public void setUp() throws Exception {

calculator.clear();

}

@After

public void tearDown() throws Exception {

}

@Test

public void testAdd() {

calculator.add(3, 4);

//assertEquals判断对象中的值是否是期待的值7

assertEquals(5, calculator.getResult());

}

@Test

public void testSubstract() {

calculator.substract(10,3);

assertEquals(7, calculator.getResult());

}

}

执行结果

显示结果有2个Failure。

如下图，testAdd执行失败。testAdd测试的是3+4，正确结果应该为7。assert中填写的预期结果为5，assert判断不一致执行失败。

如下图，testSubstract执行失败。testSubstract测试的是10-3，正确结果应该为7。assert中填写的预期结果为7，assert判断不一致执行失败。预期结果正确实际结果不正确，查看所测试的被测类中发现Substract编写错误，多减了1。

通过下面实例对Error进行讲解

准备需测试类

代码段：

public class Calculator {

private static int result;

public void multiply(int m, int n){

result = m * n;

}

public void divide(int m, int n) {

result = m / n;

}

public void clear() {

result = 0;

}

public int getResult() {

return result;

}

}

编写测试类

代码段：

import static org.junit.Assert.*;

import org.junit.Before;

import org.junit.Test;

public class CalculatorTest {

private static Calculator calculator = new Calculator();

@Before

public void setUp() throws Exception {

calculator.clear();

}

@Test

public void testMultiply() {

int n = Integer.parseInt("abc");

calculator.multiply(n,5);

assertEquals(25, calculator.getResult());

}

@Test

public void testDivide() {

calculator.divide(8,0);

assertEquals(2, calculator.getResult());

}

}

执行结果

显示结果有2个执行Error。

如下图，testDivide执行Error。testDivide测试的是8/0，除数不能为0，测试用例类编写错误。提示java.lang.ArithmeticException: / by zero异常。

如下图，testMultiply执行Error。testMultiply测试的是n*5，n传入的是”abc”，测试用例类编写错误。提示java.lang.NumberFormatException: For input string: "abc"异常。

# 任务步骤

按照上面的JUnit中的Failure和Error知识讲解，按照下面的要求更深入的了解的Failure和Error知识。

Failure练习：

需测试的代码需求如下，（1）输入一组学生成绩，计算学生成绩平均值。最多计算4个学生成绩。（2）如输入的学生成绩个数少于4个，输入“-1”为结束；（3）只输入了“-1”平均值返回“-1”。

设计测试类，测试3种情况：（1）输入“-1”，（2）输入"80,102",-2",40",-1"，（3）输入“80,100,90,40,60，-1”，根据预期结果和实际结果找出被测程序中的错误，标出错误代码并写出正确代码。

代码段

public class Average {

double average = 0;

public void Score(String... iscore) {

String[] scorces1 = iscore;

int[] scorces = new int[scorces1.length];

for (int j = 0; j < scorces1.length; j++) {

scorces[j] = Integer.valueOf(scorces1[j]);

}

int sum = 0;

int n1 = 0;

int n2 = 0;

int i = 0;

while (scorces[i] != -1 && n2 < 5) {

n2 = n2 + 1;

if (scorces[i] >= 0 && scorces[i] <= 100) {

n1 = n1 + 1;

sum = sum + scorces[i];

}

i = i + 1;

}

if (n1 > 0) {

average = sum * 1.0/ n1;

} else {

average = 0;

}

}

public double getAverage() {

return average;

}

}

Error练习：

需测试的代码需求如下，输入登录用户名和密码，用户名为“Student”并且密码为“123456”，登录成功返回true，否则返回false。

使用参数化设计测试类，输入3组数据，3组数据：第一组正确的用户名、密码和预期结果；第二组无预期结果，第三组预期结果和实际结果不一致。

代码段

public class Register {

public boolean LogOn(String username, String password) {

if (username == "Student" && password == "123456") {

return true;

} else {

return false;

}

}

}

# 任务总结

通过本次实训，了解JUnit中Failure和Error的区别，为进行白盒测试判断问题奠定基础。实训难度较低，知识点主要在于JUnit中Failure和Error的区别，要求学生熟悉错误信息的区别。

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
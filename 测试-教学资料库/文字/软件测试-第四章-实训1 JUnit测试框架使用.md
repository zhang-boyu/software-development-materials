JUnit测试框架使用实训指导书

# 任务说明

## 1.1任务内容

根据指导书，学习安装JUnit和生成JUnit测试框架。

## 1.2知识点/技能点

学习Eclipse中配置JUnit和生成JUnit的测试用例框架。

## 1.3任务目标

对JUnit的测试框架使用进行练习，正确结果对照—实训任务答案。

# 任务准备

## 2.1 背景知识

JUnit是一个Java语言的单元测试框架，它是由 Erich Gamma 和 Kent Beck 建立的。JUnit测试是程序员测试，即所谓白盒测试，因为程序员知道被测试的软件如何（How）完成功能和完成什么样（What）的功能。JUnit用于编写和运行可重复的测试，是用于单元测试框架体系xUnit的一个实例（用于Java语言）。主要用于白盒测试，回归测试。

单元级测试在面向对象的开发中变得越来越重要，而一个简明易学、适用广泛、高效稳定的单元级测试框架对成功的实施测试有着至关重要的作用。在java编程环境中，JUnit 框架是一个已经被多数java程序员采用和实证的优秀的测试框架。开发人员只需要按照JUnit的约定编写测试代码，就可以对自己要测试的代码进行测试。

下面介绍如何生成JUnit单元测试框架。

准备需测试类

新建名称为Test的项目，在Test项目中新建一个Calculator.java，写入下面代码段，代码段中为加、减、乘、除运算。

代码段：

public class Calculator {

private static int result;

public void add(int m, int n) {

result = m + n;

}

public void substract(int m, int n) {

result = m - n;

}

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

在Eclipse项目中引入JUnit单元测试包

JUnit是Java的一个框架，所以要求机器中已经安装好JDK并且配置好了Java运行环境。

在该项目上点右键，选择“Bulid Path”---->“Add Libraries...”。

弹出“Add Library”窗口，选择“JUnit”，点“Next”。选择JUnit4，点“Finish”，JUnit测试包导入成功。

生成JUnit测试框架

在Eclipse的Package Explorer中用右键点击Calculator.java类弹出菜单，选择“New”---->“JUnit Test Case”。如下图所示：

在弹出的对话框中，进行相应的选择，如下图所示：

点击“Next”后，系统会自动列出Calculator这个类中包含的方法，选择要进行测试的方法。在该例中我们需要对“加、减、乘、除”四个方法进行测试，勾选相应的方法。如下图所示：

系统会自动生成一个新类CalculatorTest，里面包含一些空的测试用例。如下图所示：

编写测试类

编写测试用例类。完整的CalculatorTest代码如下：

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

assertEquals(7, calculator.getResult());

}

@Test

public void testSubstract() {

calculator.substract(10,3);

assertEquals(7, calculator.getResult());

}

@Test

public void testMultiply() {

calculator.multiply(5,5);

assertEquals(25, calculator.getResult());

}

@Test

public void testDivide() {

calculator.divide(8,4);

assertEquals(2, calculator.getResult());

}

}

运行测试代码

按照上述代码修改完毕后，我们在CalculatorTest类上点右键，选择“Run As”----->“JUnit Test”来运行我们的测试，如下图所示：

运行结果如下：

具体的测试结果在进度条上面有表示“共进行了4个测试”，4个均测试通过。

# 任务步骤

按照上面的JUnit知识讲解，使用JUnit框架给下面的代码段生成测试框架，并按照上面的代码样例编写测试类，并执行测试。

要求如下：

加法方法计算2次，输入的值分别为7和2；

减法方法计算2次，输入的值分别为2和6；

乘法方法计算2次，输入的值分别为3和3；

除法方法计算2次，输入的值分别为2和12。

public class Calculator{

private static int result;

public void add(int n) {

result = result + n;

}

public void substract(int n) {

result = n- result;

}

public void multiply(int n){

result = result * n;

}

public void divide(int n) {

result =n/result;

}

public void clear() {

result = 1;

}

public int getResult() {

return result;

}

}

# 任务总结

通过本次实训，完成JUnit的安装以及测试框架的使用，为进行白盒测试奠定基础。实训难度较低，知识点主要在于生成JUnit测试框架，要求学生熟练掌握JUnit的安装以及生成测试框架的知识点。

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
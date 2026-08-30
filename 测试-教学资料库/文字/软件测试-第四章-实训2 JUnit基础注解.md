JUnit常用注释实训指导书

# 任务说明

## 1.1任务内容

根据指导书，学习JUnit常用注释的使用。

## 1.2知识点/技能点

JUnit中一些常用注释的理解和使用。

## 1.3任务目标

对JUnit的常用注释的使用进行练习，正确结果对照—实训任务答案。

# 任务准备

## 2.1 背景知识

JUnit之前对测试类测试方法命名限制比较多，到了 JUnit4 引入了注解，在 JUnit4 中对类名称和方法名称不再限制，可以根据各人的编程习惯命名，只需要加上对应的注解，导入相应的包就可以了。Java注解（(Annotation）的使用方法是@注解名，能通过简单的词语来实现一些功能。在测试过程中测试执行所需要的固定环境称为Test Fixture，Fixtures主要目的是建议一个固定/已知的环境状态确保测试可重复并且按照预期结果来运行。JUnit提供有两个类级别（@BeforeClass、@AfterClass），两个方法级别（@Before、@After）的fixture注释。

在JUnit4 中常用的注解有@Test、@BeforeClass、@AfterClass、@Before、@After。

方法注解：

@BeforeClass：它会在所有的测试方法执行之前被执行，只执行一次该方法，且必须为 public static void。当运行一些关联的用例时，可能会需要执行一些相同的操作，这时可将共用的部分提取出来，放在一个方法里，并且这个方法注解为@BeforeClass。意思是在测试类里所有用例运行之前，运行一次这个方法。例如创建数据库连接、读取文件等。

@AfterClass：同@BeforeClass对应，在所有的测试方法执行完成后被执行，只执行一次该方法，且必须为 public static void。例如关闭数据量连接、释放 IO 连接资源，恢复现场等。

@Before：与@BeforeClass的区别在于，@Before不止运行一次，会在每一个测试方法被运行前执行一次，运行次数根据用例数而定，且必须为 public void。常用于一些独立于用例之间的准备工作，如进行测试环境或数据的准备。例如两个用例都需要读取数据库里的相同一条数据，但第一个用例会删除这条数据，而第二个用例需要编辑这条数据。就可以用	@BeforeClass来创建数据库连接。用@Before来执行插入这条数据。也可以用 @Before 来注释多个方法，这些方法都在每个测试之前运行。

@After：同@Before对应，会在每一个测试方法被运行结束后执行一次，且必须为 public void。常用与进行一些数据清理工作。
	@Test：将一个普通的方法修饰成为一个测试方法，在方法前添加@Test注释，就把这个方法标记为一个单元测试方法。测试方法必须为 public void。方法名字可以随便取，没有任何限制，但是规范写法是test+方法名，方法名第一个子母大写。方法不能有任何参数。

@Ignore：该注解标记的测试方法会被忽略，所修饰的测试方法不会被运行器执行。比如当测试的方法还没有实现，或者测试的方法已经过时。忽略或者禁止junit测试类上的所有方法的执行，则在测试类上添加@Ignore注解即可。@Ignore("message")，message可以备注为什么忽略。
	一个JUnit 4 的单元测试用例执行顺序为：

@BeforeClass--> （@Before –> @Test –> @After ）–>（@Before –> @Test –> @After ）–> @AfterClass
	每一个测试方法的调用顺序为：@Before –> @Test –> @After

需测试类代码段：需测试类Calculator代码如下：

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

代码段：测试用例类CalculatorTest代码如下：

import static org.junit.Assert.*;

import org.junit.After;

import org.junit.AfterClass;

import org.junit.Before;

import org.junit.BeforeClass;

import org.junit.Ignore;

import org.junit.Test;

public class CalculatorTest {

private static Calculator calculator = new Calculator();

@BeforeClass

public static void setUpBeforeClass() throws Exception {

System.out.println("beforeClass");

}

@AfterClass

public static void tearDownAfterClass() throws Exception {

System.out.println("AfterClass");

}

@Before

public void setUp() throws Exception {

calculator.clear();

System.out.println("before");

}

@After

public void tearDown() throws Exception {

System.out.println("After");

}

@Test

public void testAdd() {

calculator.add(3, 4);

assertEquals(7, calculator.getResult());

System.out.println("testAdd");

}

@Test

public void testSubstract() {

calculator.substract(10,3);

assertEquals(7, calculator.getResult());

System.out.println("testSubstract");

}

@Ignore

@Test

public void testMultiply() {

System.out.println("testMultiply");

}

@Test

public void testDivide() {

calculator.divide(8,4);

assertEquals(2, calculator.getResult());

System.out.println("testDivide");

}

}

执行结果：

执行结果显示有3个测试通过，1个测试忽略。

打印结果可看出@BeforeClass和@AfterClass只执行了一次，@Before和@After每个测试方法被运行就执行一次，@Ignore注释的testMultiply方法被忽略未执行。

beforeClass

before

testAdd

After

before

testSubstract

After

before

testDivide

After

AfterClass

# 任务步骤

按照上面讲解的JUnit基础注释的知识，使用JUnit框架给下面的代码段设计测试类，并且测试代码中添加@BeforeClass、@Before、@After、@AfterClass注释，方法中打印方法名称；被测代码中未完成的方法在执行测试时需忽略。

要求如下：

测试代码中添加@BeforeClass、@Before、@After、@AfterClass注释；

@BeforeClass、@Before、@After、@AfterClass方法中打印注释名称，每个测试方法中打印方法名称；

加法方法输入值7；

乘法方法输入值3；

除法方法输入值2。

public class Calculator{

private static int result;

public void add(int n) {

result = result + n;

}

public void substract(int n) {

//方法还未完成

}

public void multiply(int n){

result = result * n;

}

public void divide(int n) {

result = n / result;

}

public void clear() {

result = 1;

}

public int getResult() {

return result;

}

}

# 任务总结

通过本次实训，完成JUnit的常用注释的学习，为进行白盒测试奠定基础。实训难度较低，知识点主要在于JUnit常用注释的理解和练习，要求学生熟练掌握JUnit常用注释的知识点。

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
JUnit的TestRunner使用实训指导书

# 任务说明

## 1.1任务内容

根据指导书，学习JUnit的TestRunner相关知识。

## 1.2知识点/技能点

学习JUnit的TestRunner的使用。

## 1.3任务目标

对JUnit的TestRunner使用进行练习，正确结果对照—实训任务答案。

# 任务准备

## 2.1 背景知识

在前面的JUnit的学习过程中，了解了JUnit核心的测试类（TestCase）、测试集（TestSuite），本指导书主要讲解JUnit核心的测试运行器（TestRunner）。

在JUnit测试执行过程中，我们把测试代码提交给JUnit框架后，框架是通过什么来运行代码呢？答案就是TestRunner。TestRunner就是执行测试集的程序，在JUnit中有很多TestRunner，它们负责调用测试代码，每一个TestRunner都有自己的特殊功能，在实际使用中，我们需要根据不同的要求来选择不同的TestRunner。使用测试运行器的的方式也比较简单，主要使用JUnit的@RunWith注解。

在前面的学习中，大部分的测试都未指定TestRunner，但是也能正常执行。这是因为如果未指定TestRunner，那么执行时JUnit会自动使用默认的Runner，即BlockJUnit4ClassRunner。

JUnit包含的测试运行器：

JUnit38ClassRunner：为了兼容JUnit3.8的运行器

BlockJunit4ClassRunner：JUnit4的默认测试运行器

Parameterized：参数化测试，使用不同参数来运行相同测试集的运行器。

Suite：实现打包测试。新建一个类把很多测试类放在一起，执行这个新建的类，就会把所有的测试类一起执行。

Categories：分类执行，可以使用Categories运行器来制定一组测试被包含或排除。

JUnit4默认Runner

在代码中如未指定Runner，执行的时候就使用默认的Runner。默认执行器叫BlockJUnit4ClassRunner。

代码段：

import static org.junit.Assert.*;

import org.junit.Test;

public class Calculator01MainTest2 {

private static Calculator01Main calculator = new Calculator01Main();

@Test

public void testAdd() {

calculator.add(3, 4);

assertEquals(7, calculator.getResult());

}

@Test

public void testSubstract() {

calculator.substract(10,3);

assertEquals(7, calculator.getResult());

}

}

这段代码相当于下面的加了@RunWith注释的代码段：

import static org.junit.Assert.*;

import org.junit.Test;

import org.junit.runner.RunWith;

import org.junit.runners.BlockJUnit4ClassRunner;

@RunWith(BlockJUnit4ClassRunner.class)

public class Calculator01MainTest2 {

private static Calculator01Main calculator = new Calculator01Main();

@Test

public void testAdd() {

calculator.add(3, 4);

assertEquals(7, calculator.getResult());

}

@Test

public void testSubstract() {

calculator.substract(10,3);

assertEquals(7, calculator.getResult());

}

}

Parameterized

在实训9 JUnit参数化设置指导书中已经介绍。

Suite

实训10 JUnit测试套件指导书中已经介绍。

Categories

Categories是分类执行，比如有2个测试类A.java、B.java。A.java中有2个方式A.a()、A.b()，B.java中有2个方式B.c()、B.d()，我们有一个类来执行这两个类的test case，但是只执行A.a()、B.c()，不执行A.b()、B.d()，就可以使用Categories来达成目的。

Categories进行分类测试步骤：

创建接口

我们创建了2个接口用于测试方法的分类，一个方法为ClassifyOTests.java，一个方法为ClassifyTTests.java。

ClassifyOTests.java代码段

public interface ClassifyOTests {

}

ClassifyTTests.java代码段

public interface ClassifyTTests {

}

准备的测试类一

测试类AssertionsTest 中添加Categories注释，将整个类前添加Category注释，注释@Category(ClassifyOTests.class)。

import static org.junit.Assert.*;

import org.junit.Test;

import org.junit.experimental.categories.Category;

@Category(ClassifyOTests.class)

public class AssertionsTest {

@Test

public void testAssertArrayEquals() {

int[] expected = { 3 };

int[] actual = { 3 };

assertArrayEquals("failure - not same", expected, actual);

}

@Test

public void testAssertEquals() {

long long1 = 50;

long long2 = 50;

assertEquals("failure - not same", long1, long2);

}

@Test

public void testAssertSame() {

String str1 = "hello world!!";

String str2 = "hello world!!";

assertSame("failure - not same", str2, str1);

}

@Test

public void testAssertNotSame() {

String str1 = "hello world!!";

String str2 = "hello java!!";

assertNotSame("failure - same", str1, str2);

}

}

准备的测试类二

需测试类代码段：

public class AssertThat {

private static int result;

public void add(int m, int n) {

result = m + n;

}

public void clear() {

result = 0;

}

public int getResult() {

return result;

}

public String getName(String name) {

return name;

}

}

测试类代码段：

测试类AssertThatTest 中添加Categories注释，在测试方法前添加Category注释；

testAdd()方法添加注释@Category(ClassifyOTests.class)；

testAdd1()方法添加注释@Category(ClassifyOTests.class)；

testGetName方法添加注释@Category(ClassifyTTests.class)。

import static org.hamcrest.MatcherAssert.assertThat;

import static org.hamcrest.Matchers.*;

import org.junit.Before;

import org.junit.Test;

import org.junit.experimental.categories.Category;

public class AssertThatTest {

private static AssertThat ass = new AssertThat();

@Before

public void setUp() throws Exception{

ass.clear();

}

@Test

@Category(ClassifyOTests.class)

public void testAdd() {

ass.add(3, 4);

//allOf：所有条件必须都成立，测试才通过  ，结果在6和8之间

assertThat(ass.getResult(), allOf(greaterThan(6), lessThan(8)));

//anyOf只要有一个条件成立，测试就通过

assertThat(ass.getResult(), anyOf(greaterThan(6), lessThan(5)));

//anyOf只要有一个条件成立，测试就通过

assertThat(ass.getResult(), anyOf(greaterThan(8), lessThan(9)));

//anything：无论什么条件，测试都通过

assertThat(ass.getResult(), anything());

}

@Test

@Category(ClassifyOTests.class)

public void testAdd1() {

ass.add(3, 4);

//is：变量的值等于指定值时，测试通过

assertThat(ass.getResult(), is(7));

//not：和is相反，变量的值不等于指定值时，测试通过

assertThat(ass.getResult(), not(2));

//euqalTo：相加结果为7，测试通过

assertThat(ass.getResult(), equalTo(7));

}

@Test

@Category(ClassifyTTests.class)

public void testGetName() {

//containsString：字符串变量中包含指定字符串时，测试通过

assertThat(ass.getName("Monika"), containsString("ni"));

//startsWith：字符串变量以指定字符串开头时，测试通过

assertThat(ass.getName("Monika"), startsWith("Mo"));

//endsWith：字符串变量以指定字符串结尾时，测试通过

assertThat(ass.getName("Monika"), endsWith("ka"));

//euqalTo：字符串变量等于指定字符串时，测试通过

assertThat(ass.getName("Monika"), equalTo("Monika"));

}

}

添加测试集类（方法一）

要求：只执行标注了@Category(ClassifyOTests.class)的方法和类，@IncludeCategory标注要执行的那个分类的方法。第一种书写方法：

import org.junit.experimental.categories.Categories;

import org.junit.experimental.categories.Categories.IncludeCategory;

import org.junit.runner.RunWith;

import org.junit.runners.Suite.SuiteClasses;

@RunWith(Categories.class)

@IncludeCategory(ClassifyOTests.class)

@SuiteClasses({ AssertionsTest.class, AssertThatTest.class })

public class AllTests {

}

方法一执行结果

只执行标注了@Category(ClassifyOTests.class)的方法和类，执行结果。AssertionsTest 整个类标注@Category(ClassifyOTests.class)，这个类的所有方法都执行。AssertThatTest 执行标注了@Category(ClassifyOTests.class)的testAdd()和testAdd1()方法，testGetName()方法未执行。

添加测试集类（方法二）

只执行标注了@Category(ClassifyOTests.class)的方法和类。第二种书写方法，ExcludeCategory(ClassifyOTests.class)除了运行ClassifyOTests方法之外的方法都运行：

import org.junit.experimental.categories.Categories;

import org.junit.experimental.categories.Categories.ExcludeCategory;

import org.junit.runner.RunWith;

import org.junit.runners.Suite.SuiteClasses;

@RunWith(Categories.class)

@ExcludeCategory(ClassifyTTests.class)

@SuiteClasses({ AssertionsTest.class, AssertThatTest.class })

public class AllTests {

}

方法二执行结果

# 任务步骤

按照上面的JUnit测试套件知识讲解，使用JUnit测试套件完成下面的测试要求。

新建两个接口CalculatorOTest.java、CalculatorTTest.java。

测试类1为： “实训4 JUnit断言方法-assertThat-一般匹配符”任务的测试类，减法测试为CalculatorOTest分类，除法测试为CalculatorTTest分类。

测试类2为“实训5 JUnit断言方法-assertThat-字符串相关匹配符”任务的测试类，姓名判断测试为CalculatorOTest分类，年龄测试为CalculatorTTest分类。

新建一个测试集“CategoryTestO.java”运行上面2个测试类，只运行CalculatorOTest分类方法。

新建一个测试集“CategoryTestT.java”运行上面2个测试类，运行除了CalculatorOTest分类之外的方法。

# 任务总结

通过本次实训，完成JUnit中TestRunner的使用，为进行白盒测试奠定基础。实训难度较低，知识点主要在于JUnit中BlockJunit4ClassRunner、Parameterized、Suite、Categories运行器的理解和使用，要求学生掌握JUnit运行器相关的知识点。

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
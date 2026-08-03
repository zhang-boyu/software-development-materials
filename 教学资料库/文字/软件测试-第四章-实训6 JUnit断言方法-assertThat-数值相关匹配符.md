JUnit断言assertThat-数值相关匹配符实训指导书

# 任务说明

## 1.1任务内容

根据指导书，学习JUnit新的断言语法assertThat数值相关匹配符的使用。

## 1.2知识点/技能点

学习JUnit断言语法assertThat。

## 1.3任务目标

对JUnit的断言方法assertThat进行练习，正确结果对照—实训任务答案。

# 任务准备

## 2.1 背景知识

JUnit4结合Hamcrest提供了一个全新的断言语法--assertThat。程序员使用assertThat的一个断言语句并且结合Hamcrest提供的匹配符，就可以表达出全部的测试思想，这些匹配符更接近自然语言，可读性高，更加灵活。

assertThat的有点如下：

使用一条assertThat可以替代所有的实训3中的所有断言语句，这样可以在所有的单元测试中只是用一种断言方法，使得编写测试用例变得简单，代码风格统一，测试代码也更易维护。

assertThat使用了Hamcrest的Matcher 匹配符，用户可以使用匹配符规定的匹配准则精确的指定一些想设定满足的条件，具有很强的易读性，而且使用起来更加灵活，可以达到更多的目的。

assertEquals使用的是比较难懂的“谓宾主”语法模式，期望值在前，实际值在后 （如：assertEquals(expecteds,actuals);）不易于理解和记忆；assertThat 使用了类似于“主谓宾”的易读语法模式（如：assertThat(actuals,is(expecteds));），使得代码更加直观、易读。

assertThat错误信息更加易懂、可读且具有描述性，assertEquals 默认出错后不会抛出额外提示信息，错误信息不明确。
	数值相关匹配符

closeTo

assertThat( testedDouble, closeTo( 10.0, 0.5 ) );

匹配符表明如果所测试的浮点型数testedDouble在10.0±0.5范围之内则测试通过。

greaterThan

assertThat( testedNumber, greaterThan(10.0) );

匹配符表明如果所测试的数值testedNumber大于10.0则测试通过。

lessThan

assertThat( testedNumber, lessThan (8.0) );

匹配符表明如果所测试的数值testedNumber小于8.0则测试通过。

greaterThanOrEqualTo

assertThat( testedNumber, greaterThanOrEqualTo (10.0) );

匹配符表明如果所测试的数值testedNumber大于等于10.0则测试通过。

lessThanOrEqualTo

assertThat( testedNumber, lessThanOrEqualTo (10.0) );

匹配符表明如果所测试的数值testedNumber小于等于10.0则测试通过。

步骤：

被测代码段：

public class AssertThat {

private static double result;

public void div(double a, double b) {

result = a / b;

}

public void clear() {

result = 0;

}

public double getResult() {

return result;

}

}

测试类代码段：

import static org.hamcrest.MatcherAssert.assertThat;

import static org.hamcrest.Matchers.*;

import org.junit.Before;

import org.junit.Test;

public class AssertThatTest {

private static AssertThat ass = new AssertThat();

@Before

public void setUp() throws Exception {

ass.clear();

}

@Test

public void testDiv() {

ass.div(20, 3);

//closeTo：计算结果值在6.0±0.8范围内，测试通过

assertThat(ass.getResult(), closeTo(6.0, 0.8));

//greaterThan：计算结果值大于6时，测试通过

assertThat(ass.getResult(), greaterThan(6.0));

//lessThan：计算结果值小于8时，测试通过

assertThat(ass.getResult(), lessThan(8.0));

//greaterThanOrEuqalTo：计算结果值大于等于6.6时，测试通过

assertThat(ass.getResult(), greaterThanOrEqualTo(6.6));

//lessThanOrEqualTo：计算结果值小于等于6.7时，测试通过

assertThat(ass.getResult(), lessThanOrEqualTo(6.7));

}

}

执行结果：

执行结果显示测试通过。

# 任务步骤

按照上面讲解的JUnit新的断言assertThat的知识，给下面的代码段设计测试类，写出测试方法并执行测试，使用assertThat中的closeTo、greaterThan、lessThan、greaterThanOrEqualTo、lessThanOrEqualTo来进行判断。

要求如下：

减法方法计算8.8-7.5，判断计算的值大于1或者小于2；

减法方法计算8.8-7.5，判断计算的值大于等于1或者小于等于1.5；

减法方法计算8.8-7.5；判断计算的值在1±0.5范围内并且也在2±0.8范围内；

public class AssertThat {

private static double result;

public void substract(double m, double n) {

result = m - n;

}

public void clear() {

result = 0;

}

public double getResultOne() {

return result;

}

}

# 任务总结

通过本次实训，完成JUnitJUnit新的断言assertThat中的closeTo、greaterThan、lessThan、greaterThanOrEqualTo、lessThanOrEqualTo学习，为进行白盒测试奠定基础。实训难度一般，知识点主要在于assertThat中的数值相关匹配符断言方法的理解和练习，要求学生熟练掌握JUnit新的断言assertThat方法的知识点。

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
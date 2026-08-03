JUnit断言assertTha-一般匹配符

实训指导书

# 任务说明

## 1.1任务内容

根据指导书，学习JUnit新的断言语法assertThat一般匹配符的使用。

## 1.2知识点/技能点

学习JUnit断言语法assertThat。

## 1.3任务目标

对JUnit的断言方法assertThat进行练习，正确结果对照—实训任务答案。

# 任务准备

## 2.1 背景知识

JUnit4结合Hamcrest提供了一个全新的断言语法--assertThat。程序员使用assertThat的一个断言语句并且结合Hamcrest提供的匹配符，就可以表达出全部的测试思想，这些匹配符更接近自然语言，可读性高，更加灵活。

assertThat的优点如下：

使用一条assertThat可以替代所有的实训3中的所有断言语句，这样可以在所有的单元测试中只是用一种断言方法，使得编写测试用例变得简单，代码风格统一，测试代码也更易维护。

assertThat使用了Hamcrest的Matcher 匹配符，用户可以使用匹配符规定的匹配准则精确的指定一些想设定满足的条件，具有很强的易读性，而且使用起来更加灵活，可以达到更多的目的。

assertEquals使用的是比较难懂的“谓宾主”语法模式，期望值在前，实际值在后 （如：assertEquals(expecteds,actuals);）不易于理解和记忆；assertThat 使用了类似于“主谓宾”的易读语法模式（如：assertThat(actuals,is(expecteds));），使得代码更加直观、易读。

assertThat错误信息更加易懂、可读且具有描述性，assertEquals 默认出错后不会抛出额外提示信息，错误信息不明确。

一般匹配符：

allOf

匹配符表明如果接下来的所有条件必须都成立测试才通过，相当于“与”（&&）；
 assertThat( testedNumber, allOf( greaterThan(4), lessThan(10) ) );。

anyOf

匹配符表明如果接下来的所有条件只要有一个成立则测试通过，相当于“或”（||）；assertThat( testedNumber, anyOf( greaterThan(10), lessThan(4) ) );。

anything

匹配符表明无论什么条件，永远为true；
 assertThat( testedNumber, anything() );。

is

匹配符表明如果前面待测的object等于后面给出的object，则测试通过；
 assertThat( testedString, is( "developerWorks" ) );。

not

匹配符和is匹配符正好相反，表明如果前面待测的object不等于后面给出的object，则测试通过；
   	 assertThat( testedString, not( "developerWorks" ) );。

步骤：

下载Hamcrest包

下载hamcrest-library.jar、hamcrest-core.jar包。

在Eclipse项目中引入Hamcrest包

项目上点右键，选择“Bulid Path”---->“Add External Archives...”。

选择下载的hamcrest-library.jar、hamcrest-core.jar包，引入成功。在测试的class中导入后就可以使用assertThat方法了。

import static org.hamcrest.MatcherAssert.assertThat;

import static org.hamcrest.Matchers.*;

被测代码段：

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

}

测试类代码段：

import static org.hamcrest.MatcherAssert.assertThat;

import static org.hamcrest.Matchers.*;

import org.junit.Before;

import org.junit.Test;

public class AssertThatTest {

private static AssertThat ass = new AssertThat();

@Before

public void setUp() throws Exception{

ass.clear();

}

@Test

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

//is：变量的值等于指定值时，测试通过

assertThat(ass.getResult(), is(7));

//not：和is相反，变量的值不等于指定值时，测试通过

assertThat(ass.getResult(), not(2));

}

}

执行结果：

执行结果显示测试通过。

# 任务步骤

按照上面讲解的JUnit新的断言assertThat中一般匹配符的知识，给下面的代码段设计测试类，写出测试方法并执行测试，使用assertThat中的allof、anyof、anthing、is、not来进行判断。

要求如下：

减法方法计算10-7，判断计算的值在2和4之间；

减法方法计算10-7，判断计算的值大于2或者小于1；

减法方法计算10-7，判断计算的值大于4或者小于7；

减法方法计算10-7，判断无论什么条件都测试通过；

减法方法计算10-7，判断是否等于3；

减法方法计算10-7，判断不等于2；

除法方法计算8/4，判断计算的值在1和3之间；

除法方法计算8/4，判断计算的值大于1或者小于1；

除法方法计算8/4，判断计算的值大于8或者小于3；

除法方法计算8/4，判断无论什么条件都测试通过；

除法方法计算8/4，判断是否等于2；

除法方法计算8/4，判断不等于1。

public class AssertThat2 {

private static int result;

public void substract(int m, int n) {

result = m - n;

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

# 任务总结

通过本次实训，完成JUnitJUnit新的断言assertThat中的allof、anyof、anthing、is、not学习，为进行白盒测试奠定基础。实训难度一般，知识点主要在于assertThat中的一般匹配符断言方法的理解和练习，要求学生熟练掌握JUnit新的断言assertThat方法的知识点。

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
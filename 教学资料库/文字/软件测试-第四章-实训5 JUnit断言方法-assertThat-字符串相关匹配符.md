JUnit断言assertThat-字符串相关匹配符实训指导书

# 任务说明

## 1.1任务内容

根据指导书，学习JUnit新的断言语法assertThat字符串相关匹配符的使用。

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

字符串相关匹配符：

containsString

assertThat( testedString, containsString( "developerWorks" ) );

匹配符表明如果测试的字符串testedString 包含子字符串"developerWorks"则测试通过。

endsWith

assertThat( testedString, endsWith( "developerWorks" ) );

匹配符表明如果测试的字符串testedString以子字符串"developerWorks"结尾则测试通过。

startsWith

assertThat( testedString, startsWith( "developerWorks" ) );

匹配符表明如果测试的字符串testedString以子字符串"developerWorks"开始则测试通过。

equalTo

assertThat( testedValue, equalTo( expectedValue ) );

匹配符表明如果测试的testedValue等于expectedValue则测试通过，equalTo可以测试数值之间，字符串之间和对象之间是否相等，相当于Object的equals方法。

equalToIgnoringCase

assertThat( testedString, equalToIgnoringCase( "developerWorks" ) ); 
匹配符表明如果测试的字符串testedString在忽略大小写的情况下等于"developerWorks"则测试通过。

equalToIgnoringWhiteSpace

assertThat( testedString, equalToIgnoringWhiteSpace( "developerWorks" ) );

匹配符表明如果测试的字符串testedString在忽略头尾的任意个空格的情况下等于"developerWorks"则测试通过，注意：字符串中的空格不能被忽略。

步骤：

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

public String getName(String name) {

return name;

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

//euqalTo：相加结果为7，测试通过

assertThat(ass.getResult(), equalTo(7));

}

@Test

public void testGetName() {

//containsString：字符串变量中包含指定字符串时，测试通过

assertThat(ass.getName("Monika"), containsString("ni"));

//startsWith：字符串变量以指定字符串开头时，测试通过

assertThat(ass.getName("Monika"), startsWith("Mo"));

//endsWith：字符串变量以指定字符串结尾时，测试通过

assertThat(ass.getName("Monika"), endsWith("ka"));

//euqalTo：字符串变量等于指定字符串时，测试通过

assertThat(ass.getName("Monika"), equalTo("Monika"));

//equalToIgnoringCase：忽略大小写的情况下等于指定字符串时，测试通过

assertThat(ass.getName("Monika"), equalToIgnoringCase("monikA"));

//equalToIgnoringWhiteSpace：忽略头尾任意空格的情况下等于指定字符串时，测试通过

assertThat(ass.getName("Monika"), equalToIgnoringWhiteSpace(" Monika   "));

}

}

执行结果：

执行结果显示测试通过。

# 任务步骤

按照上面讲解的JUnit新的断言assertThat的知识，给下面的代码段设计测试类，写出测试方法并执行测试，使用assertThat中的containsString、endsWith、startsWith、equalTo、equalToIgnoringCase、equalToIgnoringWhiteSpace来进行判断。

要求如下：

信息为：名称“Tomcat”、年龄“5”；

判断名称中是否包含“om”；

判断名称是否以“To”开头；

判断名称是否以“at”结束；

判断名称是否是“Tomcat”；

判断名称忽略大小写是否同“tomCat”一致；

判断名称忽略头尾空格是否同“  Tomcat  ”一致；

判断年龄是否是“5”。

public class Pet {

private static String name;

private static int age;

public Pet(String namep,int agep) {

name = namep;

age = agep;

}

//获取名称

public String getName() {

return name;

}

//获取年龄

public int getAge() {

return age;

}

}

# 任务总结

通过本次实训，完成JUnitJUnit新的断言assertThat中的containsString、endsWith、startsWith、equalTo、equalToIgnoringCase、equalToIgnoringWhiteSpace学习，为进行白盒测试奠定基础。实训难度一般，知识点主要在于assertThat中的字符串相关匹配符断言方法的理解和练习，要求学生熟练掌握JUnit新的断言assertThat方法的知识点。

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
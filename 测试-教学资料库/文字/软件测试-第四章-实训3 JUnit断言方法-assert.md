JUnit断言方法assert使用实训指导书

# 任务说明

## 1.1任务内容

根据指导书，学习JUnit中assert断言方法的使用。

## 1.2知识点/技能点

学习JUnit断言方法的使用。

## 1.3任务目标

对JUnit的断言方法进行练习，正确结果对照—实训任务答案。

# 任务准备

## 2.1 背景知识

编写代码时，我们总是会做出一些假设，断言就是用于在代码中捕捉这些假设。断言主要使用在代码开发和测试时期，用于对某些关键数据的判断，如果这个关键数据不是你程序所预期的数据，程序就提出警告或退出。

使用断言可以创建更稳定、品质更好且不易于出错的代码。当需要在一个值为FALSE时中断当前操作的话，可以使用断言。单元测试必须使用断言。

Junit 4断言方法允许检查测试方法的期望结果值和真实返回值，来帮助我们确定被测试的方法是否按照预期的效果正常工作。Junit的org.junit.Assert类提供了各种断言方法来。下面我们来介绍一下JUnit的各种断言。

assert断言方法

断言方法参数统一说明：message是个可选的消息，假如提供，将会在发生错误时报告这个消息。expected是期望值，通常都是用户指定的内容。 actual是被测试的代码返回的实际值。

assertArrayEquals(“message”,expecteds, actuals)

该断言用来比较两个数组是否相等。

assertEquals(“message”,expecteds,actuals)

该断言用来比较两个对象是否相等。与字符串比较中使用的equals()方法类似。

assertSame(“message”,expecteds,actuals)

该断言用来比较两个对象的引用是否相等。之前的assert方法是检查A与B是否有相同的值（使用了equals方法），而assertSame方法则是检查A与B就是同一个对象（使用的是==操作符）。

assertNotSame(“message”,expecteds,actuals)

该断言用来比较两个对象的引用是否相等和不相等，类似于通过“!=”比较两个对象。

assertTrue(“message”,condition)

该断言用来验证条件是否为真，查看的变量的值是true则测试成功，如果是false则失败。

assertFalse(“message”,condition)

该断言用来验证条件是否为假，查看的变量的值是false则测试成功，如果是true则失败。

assertNull(“message”,object)

该断言用来验证给定的对象是否为null，假如不为null，则验证失败。

assertNotNull(“message”,object)

该断言用来验证给定的对象是否为不为null，假如为null，则验证失败。

代码段：

JUnit断言使用方法演示代码：

import static org.junit.Assert.*;

import org.junit.Test;

public class AssertionsTest {

@Test

public void testAssertArrayEquals() {

int[] expected = {3};

int[] actual = {3};

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

assertSame("failure - not same",str2, str1);

}

@Test

public void testAssertNotSame() {

String str1 = "hello world!!";

String str2 = "hello java!!";

assertNotSame("failure - same",str1, str2);

}

@Test

public void testAssertTrue() {

assertTrue("failure - false",1==1);

}

@Test

public void testAssertFalse() {

assertFalse("failure - true",1==2);

}

@Test

public void testAssertNull() {

String str = null;

assertNull("failure - not null",str);

}

@Test

public void testAssertNotNull() {

String str = "hello Java!!";

assertNotNull("failure - null",str);

}

}

执行结果：

执行结果显示有8个测试通过。

# 任务步骤

按照上面讲解的JUnit断言的知识，给下面的代码段设计测试类，写出测试方法并执行测试。

要求如下：

用户信息为：名称“Fred”、年龄“18”、性别“男”、电话号码“13612251254”、其他属性为null、身高体重{170,65}；

使用assertSame判断用户名称为“Fred”；

使用assertNotSame判断用户名称不为“Hero”；

使用assertEquals判断年龄为18岁；

使用assertTrue验证性别为男；

使用assertFalse验证性别不为女；

使用assertNull验证其他属性为null；

使用assertNotNull验证电话号码不为空；

使用assertArrayEquals验证身高和体重为170，65。

public class Person {

String name;//姓名

int age;//年龄

String sex;//身高

String no;//电话号码

int[] heigwei;//身高体重

String code;//其他属性

public Person(String namec, int agec, String sexc, String noc, String codec, int... heigweic) {

name = namec;

age= agec;

sex = sexc;

no = noc;

code = codec;

heigwei = heigweic;

}

//获取名称

public String getName() {

return name;

}

//获取年龄

public int getAge() {

return age;

}

//获取性别

public int getSex() {

if(sex=="男") {

return 1;

}else {

return 0;

}

}

//获取其他属性

public String getCode(){

return code;

}

//获取电话号码

public String getNo(){

return no;

}

//获取身高体重

public int[] getHeigwei() {

return heigwei;

}

}

# 任务总结

通过本次实训，完成JUnit的assert断言方法学习，为进行白盒测试奠定基础。实训难度一般，知识点主要在于JUnit的assert各种断言方法的理解和练习，要求学生熟练掌握assert断言方法的知识点。

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
JUnit参数化设置使用实训指导书

# 任务说明

## 1.1任务内容

根据指导书，学习JUnit参数化设置相关知识。

## 1.2知识点/技能点

学习JUnit参数化设置的使用。

## 1.3任务目标

对JUnit的参数化使用进行练习，正确结果对照—实训任务答案。

# 任务准备

## 2.1 背景知识

在测试过程中，我们可能会遇到这样的函数，它的参数有许多特殊值，我们需要把这些特殊值都要进行测试。比如测试“登录”函数，测试中比如需要测试用户名密码正确、用户名不正确、密码不正确。在编写测试类的时候，至少要写3个测试方法，才能把这3种情况都包含，测试代码如下：

被测代码段：

public class Register {

public boolean LogOn(String username, String password) {

if (username == "Admin" && password == "123456") {

return true;

} else {

return false;

}

}

}

测试代码段：

import static org.junit.Assert.*;

import org.junit.Test;

public class RegisterTest {

private Register register = new Register();

@Test

public void testLogOn() {

assertEquals(true,register.LogOn("Admin", "123456"));

}

@Test

public void testLogOn1() {

assertEquals(false,register.LogOn("student", "123456"));

}

@Test

public void testLogOn2() {

assertEquals(false,register.LogOn("Admin", "123"));

}

}

通过上面的例子，我们发现编写多个测试方法进行各类数据测试时，除了传入参数不同，其他代码都相同，写了大量重复的代码。为了简化类似的测试，JUnit4提出了“参数化测试”的概念，就是只写一个测试函数，把多种情况作为参数传递进去，使用不同的值反复运行同一个测试，就可以避免写大量重复的代码。下面介绍参数化测试的流程

采用参数化测试的步骤：

为测试类指定特殊运行器，用@RunWith(Parameterized.class)来注释测试类。

import org.junit.runner.RunWith;

import org.junit.runners.Parameterized;

@RunWith(Parameterized.class)

public class RegisterTest{

...............

}

在测试类中，声明变量，用来保存测试数据，也可保存期望值。

import org.junit.runner.RunWith;

import org.junit.runners.Parameterized;

@RunWith(Parameterized.class)

public class RegisterTest {

private String username;

private String password;

private boolean expected;

......

}

创建一个由@Parameters注释的公共静态方法，返回类型为Collection，初始化需要测试的数据。

import java.util.Arrays;

import java.util.Collection;

import org.junit.runner.RunWith;

import org.junit.runners.Parameterized;

import org.junit.runners.Parameterized.Parameters;

@RunWith(Parameterized.class)

public class RegisterTest {

private Register register = new Register();

private String username;

private String password;

private boolean expected;

//测试数据集合，方法名可以随意定义，返回类型可变，但是必须用@Parameters标注

@Parameters

public static Collection userData() {

// 数组中，包含了传入参数和期望结果，数组参数顺序与构造函数参数顺序一致即可

return Arrays.asList(new Object[][]{

{"Admin","123456",true},

{"student","123456",false},

{"Admin","123",false}});

......

}

}

声明一个公共的构造函数，构造函数的参数为第2步的变量。构造函数参数的赋值顺序，同第3步中初始化数据对的参数顺序一致。

import java.util.Arrays;

import java.util.Collection;

import org.junit.runner.RunWith;

import org.junit.runners.Parameterized;

import org.junit.runners.Parameterized.Parameters;

@RunWith(Parameterized.class)

public class RegisterTest {

private Register register = new Register();

private String username;

private String password;

private boolean expected;

//测试数据集合，方法名可以随意定义，返回类型可变，但是必须用@Parameters标注

@Parameters

public static Collection userData() {

// 数组中,包含了传入参数和期望结果，数组参数顺序与构造函数参数顺序一致即可

return Arrays.asList(new Object[][]{

{"Admin","123456",true},

{"student","123456",false},

{"Admin","123",false}});

}

//构造函数，参数赋值顺序与测试数据集合一致

public RegisterTest(String username,String password,boolean expected) {

this.username = username;

this.password = password;

this.expected = expected;

}

......

}

编写测试代码，用初始化的参数进行测试。

import static org.junit.Assert.assertEquals;

import java.util.Arrays;

import java.util.Collection;

import org.junit.Test;

import org.junit.runner.RunWith;

import org.junit.runners.Parameterized;

import org.junit.runners.Parameterized.Parameters;

@RunWith(Parameterized.class)

public class RegisterTest {

private Register register = new Register();

private String username;

private String password;

private boolean expected;

//测试数据集合，方法名可以随意定义，返回类型可变，但是必须用@Parameters标注

@Parameters

public static Collection userData() {

// 数组中,包含了传入参数和期望结果，数组参数顺序与构造函数参数顺序一致即可

return Arrays.asList(new Object[][]{

{"Admin","123456",true},

{"student","123456",false},

{"Admin","123",false}});

}

//构造函数，参数赋值顺序与测试数据集合一致

public RegisterTest(String username,String password,boolean expected) {

this.username = username;

this.password = password;

this.expected = expected;

}

@Test

public void testLogOn() {

assertEquals(expected,register.LogOn(username,password));

}

}

执行结果

执行了3次登录操作，并且验证结果同预置结果相同。

# 任务步骤

按照上面讲解的参数化知识，按照要求给下面的代码段设计测试类，写出测试方法并执行测试。

要求如下： 使用条件组合覆盖来设计数据和测试方法。

public class Function {

public int function(int x, int y, int z) {

{

if ((y > 1) && (z == 0)) {

x = x / y;

return x;

}

if ((y == 2) || (x > 1)) {

x = x + 1;

return x;

}

y = x + z;

return y;

}

}

}

# 任务总结

通过本次实训，完成JUnit中参数化的使用，为进行白盒测试奠定基础。实训难度较低，知识点主要在于参数化的使用，要求学生熟练掌握JUnit的参数化设置过程和方法知识点。

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
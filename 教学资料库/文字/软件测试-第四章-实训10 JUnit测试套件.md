JUnit测试套件(Test Suite)使用实训指导书

# 任务说明

## 1.1任务内容

根据指导书，学习JUnit测试套件知识。

## 1.2知识点/技能点

学习JUnit测试套件的使用。

## 1.3任务目标

对JUnit的测试套件使用进行练习，正确结果对照—实训任务答案。

# 任务准备

## 2.1 背景知识

在前面的实训讲解中，我们执行测试类都是一个一个单独运行的，但是在实际项目实践中，测试类会非常的多，一个一个的单独执行是不可行的，为了解决这个问题，JUnit提供了一种批量运行测试类的方法，叫做测试套件。

通常把一组相关的测试称为一个测试套件（test suite）。测试套件会将类似测试用例集合在一起，例如测试套件可以是一个只包含冒烟测试测试用例的测试套件，或者是针对系统特定功能的测试套件。一个测试套件也可以包括所有的测试，并且标明其用途为冒烟测试或是针对特定的功能。

使用测试套件之后，每次验证系统功能正确性时，只需要执行一个或几个测试套件就可以。编写测试套件的方法比较简单，需要遵循以下规则：

创建一个空类作为测试套件的入口

使用注解org.junit.runner.RunWith和org.junit.runners.Suite.SuiteClasses修饰这个空类

将org.junit.runners.Suite作为参数传入注释RunWith，以提示JUnit为此类使用条件运行器执行。

将需要放入此测试套件的测试类组成数组作为注解SuiteClasses的参数。

保证这个空类使用public修饰，并且存在公开的不带有任何参数的构造函数。

组合一组测试类

准备测试类一，代码段：（实训9 参数化设置中的代码段）

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

准备测试类二，代码段：（实训6 断言方法assertThat数值相关匹配符中的代码段）

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

新建测试套件类

在该项目上点右键，选择“New”---->“Other”。如下图所示：

在“New”窗口，选择“JUnit”--->“JUnit Test Suite”，点“Next>”。如下图所示：

在“New JUnit Test Suite”窗口中，可以设置测试套件的类名称，选择该测试套件需要的测试类，我们选择RegisterTest 和AssertThatTest ，测试套件的类名称：AllTests，点“Finish”。如下图所示：

测试套件类生成代码段如下：

import org.junit.runner.RunWith;

import org.junit.runners.Suite;

import org.junit.runners.Suite.SuiteClasses;

@RunWith(Suite.class)

@SuiteClasses({ AssertThatTest.class, RegisterTest.class })

public class AllTests {

}

执行测试套件类，运行结果如下：

具体的测试结果在进度条上面有表示“共进行了4个测试”，4个均测试通过。

在上面的步骤中，是将2个测试类放入了一个测试套件AllTests中，在Eclipse中运行这个测试套件，测试套件中的2个测试类都被执行了。测试套件中不仅可以包含基本的测试类，而且可以包含其他的测试套件，这样能方便的分层管理不同模块的单元测试代码。

组合一组测试集

测试套件一“AllTests1.java”，包含的测试类为：“AssertThatTest.class”、“RegisterTest.class”。代码段如下：

import org.junit.runner.RunWith;

import org.junit.runners.Suite;

import org.junit.runners.Suite.SuiteClasses;

@RunWith(Suite.class)

@SuiteClasses({ AssertThatTest1.class, TTest.class })

public class AllTests2 {

}

测试套件二“AllTests2.java”，包含的测试类为：“AssertThatTest1.class”、“TTest.class”。代码段如下：

import org.junit.runner.RunWith;

import org.junit.runners.Suite;

import org.junit.runners.Suite.SuiteClasses;

@RunWith(Suite.class)

@SuiteClasses({ AssertThatTest1.class, TTest.class })

public class AllTests2 {

}

按照上面的步骤新建测试套件，测试套件名称为“AllTests”，选择测试套件一“AllTests1.java”和测试套件二“AllTests2.java”。代码段如下：

import org.junit.runner.RunWith;

import org.junit.runners.Suite;

import org.junit.runners.Suite.SuiteClasses;

@RunWith(Suite.class)

@SuiteClasses({ AllTests1.class, AllTests2.class })

public class AllTests {

}

执行测试套件类，运行结果如下：

具体的测试结果在进度条上面有表示“共进行了7个测试”，7个均测试通过。

# 任务步骤

按照上面的JUnit测试套件知识讲解，使用JUnit测试套件完成下面的测试要求。

新建一个测试套件“AllTest1.java”运行2个测试类，测试类分别为： “实训4 JUnit断言方法-assertThat-一般匹配符”任务的测试类和“实训5 JUnit断言方法-assertThat-字符串相关匹配符”任务的测试类。

新建一个测试套件“AllTest2.java”运行2个测试类，测试类分别为： “实训6 JUnit断言方法-assertThat-数值相关匹配符”任务的测试类和“实训7 JUnit断言方法-assertThat-集合相关匹配符”任务的测试类。

新建一个测试套件“AllTest.java”运行2个测试套件，测试套件为“AllTest1.java”和“AllTest2.java”。

# 任务总结

通过本次实训，完成JUnit测试套件的使用，为进行白盒测试奠定基础。实训难度较低，知识点主要在于JUnit测试套件的理解和使用，要求学生熟练掌握JUnit测试套件相关的知识点。

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
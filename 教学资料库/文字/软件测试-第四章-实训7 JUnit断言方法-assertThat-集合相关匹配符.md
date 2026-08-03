JUnit断言assertThat-集合相关匹配符

实训指导书

# 任务说明

## 1.1任务内容

根据指导书，学习JUnit新的断言语法assertThat的使用。

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

集合相关匹配符

hasItemInArray

assertThat( Array, hasItemInArray( "element" ) );

匹配符表明如果测试的数组Array含有元素“element”项则测试通过。

hasItem

assertThat( iterableObject, hasItem ( "element" ) );

匹配符表明如果测试的迭代对象iterableObject含有元素“element”项则测试通过。

hasItems

assertThat(iterableObject, hasItems("element1", "element2"));

匹配符表明如果测试的迭代对象iterableObject中至少含有元素“element1”、“element2”则测试通过。

containsInAnyOrder

assertThat(iterableObject,containsInAnyOrder("element1","element2","element3"));

匹配符表明如果测试的迭代对象iterableObject只含有元素为“element1”、“element2”和“element3”项则测试通过。

hasEntry

assertThat( mapObject, hasEntry( "key", "value" ) );

匹配符表明如果测试的Map对象mapObject含有一个键值为"key"对应元素值为"value"的Entry项则测试通过。

hasKey

assertThat( mapObject, hasKey ( "key" ) );

匹配符表明如果测试的Map对象mapObject含有键值“key”则测试通过。

hasValue

assertThat( mapObject, hasValue ( "value" ) );

匹配符表明如果测试的Map对象mapObject含有元素值“value”则测试通过。

步骤：

被测代码段：

import java.util.ArrayList;

import java.util.HashMap;

import java.util.List;

import java.util.Map;

public class AssertThat {

public String[] getString(String a,String b,String c) {

String[] s = {a,b,c};

return s;

}

public List<String> getList(String al,String bl,String cl) {

List<String> l = new ArrayList<String>();

l.add(al);

l.add(bl);

l.add(cl);

return l;

}

public Map<String, String> getMap(String key, String value) {

Map<String, String> m = new HashMap<String, String>();

m.put(key, value);

return m;

}

}

测试类代码段：

import static org.hamcrest.MatcherAssert.assertThat;

import static org.hamcrest.Matchers.*;

import java.util.List;

import java.util.Map;

import org.junit.Test;

public class AssertThatTest {

private static AssertThat ass = new AssertThat();

@Test

public void testGetString() {

String[] s = ass.getString("ABC", "DEF", "GHI");

// hasItemInArray：测试一个数组包含一个元素

assertThat(s, hasItemInArray(startsWith("DE")));

}

@Test

public void testGetList() {

List<String> l = ass.getList("Magci", "Fred", "Hero");

// hasItem：Iterable变量中含有指定元素时，测试通过

assertThat(l, hasItem(startsWith("F")));

// 检查多个元素是否在集合中

assertThat(l, hasItems("Fred", "Magci"));

// 检查集合中元素是否同多个元素一致

assertThat(l, containsInAnyOrder("Fred", "Hero", "Magci"));

}

@Test

public void testGetMap() {

Map<String, String> m = ass.getMap("name", "Fred");

// hasEntry：Map变量中含有指定键值对时，测试通过

assertThat(m, hasEntry("name", "Fred"));

// hasKey：Map变量中含有指定键时，测试通过

assertThat(m, hasKey("name"));

// hasValue：Map变量中含有指定值时，测试通过

assertThat(m, hasValue("Fred"));

}

}

执行结果：

执行结果显示测试通过。

# 任务步骤

按照上面讲解的JUnit新的断言assertThat的知识，给下面的代码段设计测试类，写出测试方法并执行测试，使用assertThat中的hasItemInArray、hasItem、hasItems、containsInAnyOrder、hasEntry、hasKey、hasValue来进行判断。

要求如下：

方法一传入数据("ABC", "DEF", "GHI")，判断数组中是否包含以“DE”开头的元素；

方法二传入数据("Magci", "Fred", "Hero","Alice")，判断集合中是否有“e”结尾的元素；

方法二传入数据("Magci", "Fred", "Hero","Alice")，判断"Magci", "Fred"在集合中并且"Tom", "Cat"不在集合中；

方法二传入数据("Magci", "Fred", "Hero","Alice")，判断集合中是否只包含"Magci", "Fred", "Hero","Alice"四个元素或者只包含"Fred", "Hero"两个元素；

方法三传入数据("name", "Fred","age","18")，判断集合中键值对"name", "Fred"或者键值对"age","18"；

方法三传入数据("name", "Fred","age","18")，判断集合中不包含键值"weight"；

方法三传入数据("name", "Fred","age","18")，判断集合中包含忽略大小写的元素值"fred"。

import java.util.ArrayList;

import java.util.HashMap;

import java.util.List;

import java.util.Map;

public class AssertThat {

//方法一

public String[] getString(String a,String b,String c) {

String[] s = {a,b,c};

return s;

}

//方法二

public List<String> getList(String al,String bl,String cl,String d1) {

List<String> l = new ArrayList<String>();

l.add(al);

l.add(bl);

l.add(cl);

l.add(d1);

return l;

}

//方法三

public Map<String, String> getMap(String keyo, String valueo,String keyt, String valuet) {

Map<String, String> m = new HashMap<String, String>();

m.put(keyo, valueo);

m.put(keyt, valuet);

return m;

}

}

# 任务总结

通过本次实训，完成JUnitJUnit新的断言assertThat中的hasItemInArray、hasItem、hasItems、containsInAnyOrder、hasEntry、hasKey、hasValue学习，为进行白盒测试奠定基础。实训难度一般，知识点主要在于assertThat中的集合相关匹配符断言方法的理解和练习，要求学生熟练掌握JUnit新的断言assertThat方法的知识点。

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
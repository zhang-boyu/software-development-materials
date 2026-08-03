JUnit测试优先级顺序使用实训指导书

# 任务说明

## 1.1任务内容

根据指导书，学习JUnit测试优先级顺序相关知识。

## 1.2知识点/技能点

学习JUnit的测试优先级顺序的使用。

## 1.3任务目标

对JUnit的测试优先级顺序使用进行练习，正确结果对照—实训任务答案。

# 任务准备

## 2.1 背景知识

在JUnit测试执行过程中，我们发现JUnit执行测试方法的顺序并不是按照测试类中写好的测试方法顺序来执行。在实际过程如果测试方法有执行的先后，比如在测试数据库相关的用例时候，按照插入数据，查询数据和删除数据的顺序来执行测试方法。如果未指定顺序，可能会先删除，那么测试就会不通过。

JUnit提供了@FixMethodOrder注解来控制测试方法的执行顺序。提供了3种执行顺序类型。

MethodSorters.JVM：按照JVM得到的方法顺序，也就是代码中定义的方法顺序；

MethodSorters.DEFAULT：JUnit默认的执行顺序；

MethodSorters.NAME_ASCENDING：按照方法名的字母顺序执行。

被测代码段

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

默认执行顺序

默认执行顺序测试类代码段

import static org.junit.Assert.*;

import org.junit.Before;

import org.junit.FixMethodOrder;

import org.junit.Test;

import org.junit.runners.MethodSorters;

public class CalculatorTest {

private static Calculator calculator = new Calculator();

@Before

public void setUp() throws Exception {

calculator.clear();

}

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

@Test

public void testMultiply() {

calculator.multiply(5,5);

assertEquals(25, calculator.getResult());

}

@Test

public void testDivide() {

calculator.divide(8,2);

assertEquals(4, calculator.getResult());

}

}

默认执行顺序结果

使用MethodSorters.JVM

使用MethodSorters.JVM顺序测试类代码段：

import static org.junit.Assert.*;

import org.junit.Before;

import org.junit.FixMethodOrder;

import org.junit.Test;

import org.junit.runners.MethodSorters;

@FixMethodOrder(MethodSorters.JVM)

public class CalculatorTest {

private static Calculator calculator = new Calculator();

@Before

public void setUp() throws Exception {

calculator.clear();

}

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

@Test

public void testMultiply() {

calculator.multiply(5,5);

assertEquals(25, calculator.getResult());

}

@Test

public void testDivide() {

calculator.divide(8,2);

assertEquals(4, calculator.getResult());

}

}

}

使用MethodSorters.JVM顺序执行结果，结果按照代码段中的测试方法的顺序执行。

使用MethodSorters.DEFAULT

使用MethodSorters.DEFAULT顺序测试类代码段：

import static org.junit.Assert.*;

import org.junit.Before;

import org.junit.FixMethodOrder;

import org.junit.Test;

import org.junit.runners.MethodSorters;

@FixMethodOrder(MethodSorters.DEFAULT)

public class CalculatorTest {

private static Calculator calculator = new Calculator();

@Before

public void setUp() throws Exception {

calculator.clear();

}

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

@Test

public void testMultiply() {

calculator.multiply(5,5);

assertEquals(25, calculator.getResult());

}

@Test

public void testDivide() {

calculator.divide(8,2);

assertEquals(4, calculator.getResult());

}

}

}

使用MethodSorters.DEFAULT顺序执行结果，结果随机执行。

使用MethodSorters.NAME_ASCENDING

使用MethodSorters.NAME_ASCENDING顺序测试类代码段：

import static org.junit.Assert.*;

import org.junit.Before;

import org.junit.FixMethodOrder;

import org.junit.Test;

import org.junit.runners.MethodSorters;

@FixMethodOrder(MethodSorters.NAME_ASCENDING)

public class CalculatorTest {

private static Calculator calculator = new Calculator();

@Before

public void setUp() throws Exception {

calculator.clear();

}

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

@Test

public void testMultiply() {

calculator.multiply(5,5);

assertEquals(25, calculator.getResult());

}

@Test

public void testDivide() {

calculator.divide(8,2);

assertEquals(4, calculator.getResult());

}

}

使用MethodSorters.NAME_ASCENDING顺序执行结果，结果按照代码段中的测试方法的字母顺序执行。

# 任务步骤

按照上面的JUnit测试执行顺序的知识讲解，使用JUnit测试执行顺序完成下面的测试要求。

使用下面的被测段，编写测试类，练习MethodSorters.JVM、MethodSorters.DEFAULT、MethodSorters.NAME_ASCENDING执行测试类方法。

public class Calculator{

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

# 任务总结

通过本次实训，完成JUnit测试执行顺序的使用，为进行白盒测试奠定基础。实训难度较低，知识点主要在于JUnit测试执行顺序的理解和使用，要求学生熟练掌握JUnit测试执行顺序相关的知识点。

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
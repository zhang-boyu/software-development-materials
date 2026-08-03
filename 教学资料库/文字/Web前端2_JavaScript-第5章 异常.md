# 第5章  异常

Java基础入门（第3版）

# 学习目标/Target

# 学习目标/Target

# 章节概述/ Summary

尽管人人希望自己身体健康，处理的事情都能顺利进行，但在实际生活中总会遇到各种状况，比如感冒发烧，工作时电脑蓝屏、死机等。同样，在程序运行的过程中，也会发生各种异常状况，例如，程序运行时磁盘空间不足、网络连接中断、加载的类不存在等。针对这种情况，Java语言引入了异常，以异常类的形式对这些非正常情况进行封装，通过异常处理机制对程序运行时发生的各种问题进行处理。本章将对异常进行详细讲解。

# 目录/Contents

# 什么是异常

5.1

# 5.1  什么是异常

先定一个小目标！

# 5.1  什么是异常

Java中的异常是指Java程序在运行时可能出现的错误或非正常情况，比如在程序中试图打开一个根本不存在的文件，在程序中除0等。异常是否出现，通常取决于程序的输入、程序中对象的当前状态以及程序所处的运行环境。程序抛出异常之后，会对异常进行处理。异常处理将会改变程序的控制流程，出于安全性考虑，同时避免异常程序影响到其他正常程序的运行，操作系统通常将出现异常的程序强行中止，并弹出系统错误提示。

异常的概念

# 5.1  什么是异常

案例演示

下面通过一个案例认识一下什么是异常，在本案例中，计算以0为除数的
表达式，运行程序并观察程序的运行结果。具体代码如下所示。

package com.itheima;
public class Example01 {                      
	public static void main(String[] args) {
		int result = divide(4, 0);    // 调用divide()方法，第2个参数为0
		System.out.println(result);    
	}
    	//下面的方法实现了两个整数相除
	public static int divide(int x, int y) { 
		int result = x / y;  // 定义一个变量result记录两个数相除的结果
		return result;        // 将结果返回
	}
 }

# 5.1  什么是异常

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 5.1  什么是异常

案例结果说明

由上图可知，程序发生了算术异常（ArithmeticException），提示运算时出现了被0除的情况。异常发生后，程序会立即结束，无法继续向下执行。

# 5.1  什么是异常

Throwable类

Java提供了大量的异常类，每一个异常类都表示一种预定义的异常，这些
异常类都继承自java.lang包下的Throwable类。Throwable类的继承体系
图如下所示。

# 5.1  什么是异常

Throwable类的子类

由上图中可知，Throwable类是所有异常类的父类，它有两个直接子类Error类和Exception类，其中，Error类代表程序中产生的错误，Exception类代表程序中产生的异常。

# 5.1  什么是异常

Throwable类的子类

Error类称为错误类，它表示Java程序运行时产生的系统内部错误或资源耗尽的错误，这类错误比较严重，仅靠修改程序本身是不能恢复执行的。例如，使用java命令去运行一个不存在的类就会出现Error错误。
 Exception类称为异常类，它表示程序本身可以处理的错误，在Java程序中进行的异常处理，都是针对Exception类及其子类的。在Exception类的众多子类中有一个特殊的子类——RuntimeException类，RuntimeException类及其子类用于表示运行时异常。 Exception类的其他子类都用于表示编译时异常。

# 5.1  什么是异常

Throwable类的常用方法

为了方便后面的学习，接下来进一步了解Throwable类中的常用方法，具体如下。

| 方法声明 | 功能描述 |
|---|---|
| String getMessage() | 返回异常的消息字符串 |
| String toString() | 返回异常的简单信息描述 |
| void printStackTrace() | 获取异常类名和异常信息，以及异常出现在程序中的位置，把信息输出在控制台。 |

# 运行时异常与编译时异常

5.2

# 5.2  运行时异常与编译时异常

先定一个小目标！

# 编译时异常

在实际开发中，经常会在程序编译时产生异常，这些异常必须要进行处理，否则程序无法正常运行，这种异常被称为编译时异常，也称为checked异常。在Exception类中，除了RuntimeException类及其子类，Exception的其他子类都是编译时异常。编译时异常的特点是Java编译器会对异常进行检查，如果出现异常就必须对异常进行处理，否则程序无法通过编译。

5.2  运行时异常与编译时异常

# 编译时异常

处理编译时期的异常有两种方式，具体如下：
（1）使用try…catch语句对异常进行捕获处理。
（2）使用throws关键字声明抛出异常，调用者对异常进行处理。

5.2  运行时异常与编译时异常

# 运行时异常

另外还有一种异常是在程序运行时产生的，这种异常即使不编写异常处理代码，依然可以通过编译，因此被称为运行时异常，也称为unchecked异常。RuntimeException类及其子类都是运行时异常。运行时异常的特点是在程序运行时由Java虚拟机自动进行捕获处理的，Java编译器不会对异常进行检查。也就是说，当程序中出现这类异常时，即使没有使用try…catch语句捕获或使用throws关键字声明抛出，程序也能编译通过，只是程序在运行过程中可能报错。

5.2  运行时异常与编译时异常

# 运行时异常

在Java中，常见的运行时异常有多种，具体如下所示。

5.2  运行时异常和编译时异常

| 方法声明 | 功能描述 |
|---|---|
| ArithmeticException | 算术异常 |
| IndexOutOfBoundsException | 索引越界异常 |
| ClassCastException | 类型转换异常 |
| NullPointerException | 空指针异常 |
| NumberFormatException | 数字格式化异常 |

# 运行时异常

运行时异常一般是由程序中的逻辑错误引起的，在程序运行时无法恢复。例如，通过数组的索引访问数组的元素时，如果索引超过了数组范围，就会发生索引越界异常，代码如下所示：
	int[] arr=new int[5];
	System.out.println(arr[6]); 

在上面的代码中，由于数组arr的length为5，最大索引应为4，当使用arr[6]访问数组中的元素就会发生数组索引越界的异常。

5.2  运行时异常和编译时异常

# 异常处理及语法

5.3

# 5.3.1  异常的产生及处理

先定一个小目标！

# 关键字描述

在Java中，通过try、catch、finally、throw、throws这5个关键字进行异常对象的处理。具体说明如下所示。

5.3.1  异常的产生及处理

| 关键字 | 功能描述 |
|---|---|
| try | 里面放置可能引发异常的代码 |
| catch | 后面对应异常类型和一个代码块，该关键字表明catch块是用于处理这种类型的代码块 |
| finally | 主要用于回收在try代码块里打开的物理资源，如数据库连接、网络连接和磁盘文件。异常机制保证finally块总是被执行 |
| throw | 用于抛出一个实际的异常。它可以单独作为语句来抛出一个具体的异常对象 |
| throws | 用在方法签名中，用于声明该方法可能抛出的异常 |

# 5.3.2  try...catch语句

先定一个小目标！

# try...catch语句的语法格式

为了使发生异常后的程序代码正常执行，程序需要捕获异常并进行处理，Java提供了try…catch语句用于捕获并处理异常。try…catch语句的语法格式如下所示：

5.3.2  try...catch语句

try{
    代码块
}catch(ExceptionType e){
             代码块
}

# try...catch语句编写注意事项

（1）try代码块是必需的。
（2）catch代码块和finally代码块都是可选的，但catch代码块和finally代码块至少要出现一个。
（3）catch代码块可以有多个，但捕获父类异常的catch代码块必须位于捕获子类异常的catch代码块后面。
（4）catch代码块必须位于try代码块之后。

5.3.2  try...catch语句

# try...catch语句异常处理流程

5.3.2  try...catch语句

# try...catch语句异常处理流程

5.3.2  try...catch语句

由上图可知，程序通过try语句捕获可能出现的异常，如果try语句没有捕获到异常，则直接跳出try…catch语句块执行其他程序；如果在try语句中捕获到了异常，则程序会自动跳转到catch语句中找到匹配的异常类型进行相应的处理。异常处理完毕，最后执行其他程序语句。

# 5.3.2  try...catch语句

案例演示

下面通过一个案例使用try…catch语句对异常进行捕获，在本案例中，计算
以0为除数的表达式，运行程序并观察程序的运行结果。具体代码如下所示。

public class Example02 {
       public static void main(String[] args) {       
	try {                               
		int result = divide(4, 0);    //调用divide()方法
		System.out.println(result);   
	} catch (Exception e) {            //对异常进行处理
		System.out.println("捕获的异常信息为：" + e.getMessage());
	}
	System.out.println("程序继续向下执行...");
	}
     //下面的方法实现了两个整数相除
     public static int divide(int x, int y) { 
	int result = x / y;    //定义一个变量result记录两个数相除的结果
	return result;                 //将结果返回
    }
}

# 5.3.2  try...catch语句

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

注意：在try代码块中，发生异常语句后面的代码是不会被执行的，如上述案例中第5行
代码的打印语句就没有执行。

# 5.3.3  finally语句

先定一个小目标！

# finally语句的语法格式

在程序中，有时候会希望一些语句无论程序是否发生异常都要执行，这时就可以在try…catch语句后，加一个finally代码块。finally语句的语法格式如下所示：

5.3.3  finally语句

try{
    代码块
} catch(ExceptionType e){
    代码块
}  finally{
    代码块
}

注意：finally代码块必须位于所有catch代码块之后。

# try…catch…finally语句的异常处理流程

5.3.3  finally语句

# try…catch…finally语句的异常处理流程

5.3.3  finally语句

由上图可知，在try…catch…finally语句中，不管程序是否发生异常，finally代码块中的代码都会被执行。需要注意的是，如果程序发生异常但是没有被捕获到，在执行完finally代码块中的代码之后，程序会中断执行。

# 5.3.3  finally语句

案例演示

下面通过一个案例演示try…catch...finally语句块的使用。具体代码如下
所示。

public static void main(String[] args) {
                    //下面的代码定义了一个try…catch…finally语句用于捕获异常
	try {
		int result = divide(4, 0);       //调用divide()方法
		System.out.println(result);
	} catch (Exception e) {               //对捕获到的异常进行处理
		System.out.println("捕获的异常信息为：" + e.getMessage());
              		return;                      //用于结束当前语句
	} finally {                             
		System.out.println("进入finally代码块");
	}
                    System.out.println("程序继续向下…");
     }
     //下面的方法实现了两个整数相除
     public static int divide(int x, int y) {
	int result = x / y;           //定义一个变量result记录两个数相除的结果
	return result;                 //将结果返回
     }

# 5.3.3  finally语句

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

注意：如果在try...catch中执行了System.exit(0)语句，finally代码块不再执行。
System.exit(0)表示退出当前的Java虚拟机，Java虚拟机停止了，任何代码都不能再执行了。

# 抛出异常

5.4

# 5.4.1  throws关键字

先定一个小目标！

# throws关键字

在实际开发中，大部分情况下我们会调用别人编写的方法，并不知道别人编写的方法是否会发生异常。针对这种情况，Java允许在方法的后面使用throws关键字声明该方法有可能发生的异常，这样调用者在调用方法时，就明确地知道该方法有异常，并且必须在程序中对异常进行处理，否则编译无法通过。

5.4.1  throws关键字

# throws关键字的语法格式

使用throws关键字抛出异常的语法格式如下所示：

5.4.1  throws关键字

修饰符 返回值类型 方法名(参数1，参数2，…)throws 异常类1, 异常类2...{
        方法体
}

throws关键字需要写在方法声明的后面，throws后面还需要声明方法中发生异常的类型。

# 5.4.1  throws关键字

案例一演示

下面通过一个案例演示throws关键字的使用。具体代码如下所示。

public class Example04 {
	public static void main(String[] args) {
		int result = divide(4, 2);    //调用divide()方法
		System.out.println(result);
	}
     	//下面的方法实现了两个整数相除，并使用throws关键字声明抛出异常
	public static int divide(int x, int y) throws Exception {
		int result = x / y;   //定义一个变量result记录两个数相除的结果
		return result;         //将结果返回
	}
}

# 5.4.1  throws关键字

案例一运行结果

运行代码，控制台显示的运行结果如下图所示。

# 案例一运行结果分析

在案例一中，第3行代码调用divide()方法时传入的第2个参数为2，程序在运行时不会发生被0除的异常。但是运行程序依然会提示错误，这是因为定义divide()方法时使用throws关键字声明了该方法可能抛出的异常，调用者必须在调用divide()方法时对抛出的异常进行处理，否则就会发生编译错误。

5.4.1  throws关键字

# 5.4.1  throws关键字

案例二演示

下面对案例一修改，使用try…catch语句处理divide()方法抛出异常。
具体代码如下所示。

public class Example05 {
	public static void main(String[] args) {
         		//下面的代码定义了一个try…catch语句用于捕获异常
		try {
			int result = divide(4, 2);   //调用divide()方法
			System.out.println(result); 
		} catch (Exception e) {                 //对捕获到的异常进行处理
			e.printStackTrace();   //打印捕获的异常信息
		}
	}
    	//下面的方法实现了两个整数相除，并使用throws关键字声明抛出异常
	public static int divide(int x, int y) throws Exception {
		int result = x / y;    //定义一个变量result记录两个数相除的结果
		return result;          //将结果返回
	}
}

# 5.4.1  throws关键字

案例二运行结果

运行代码，控制台显示的运行结果如下图所示。

注意：使用throws关键字重抛异常时，如果程序发生了异常，并且上一层调用者也无法
处理异常时，那么异常会继续被向上抛出，最终直到系统接收到异常，终止程序执行。

# 5.4.1  throws关键字

案例三演示

下面修改案例二将divide()方法抛出的异常继续抛出。具体代码如下所示。

public class Example06 {
	public static void main(String[] args)throws Exception {
		int result = divide(4, 0);   // 调用divide()方法
		System.out.println(result);
	}
    	// 下面的方法实现了两个整数相除，并使用throws关键字声明抛出异常
	public static int divide(int x, int y) throws Exception {
		int result = x / y;   // 定义一个变量result记录两个数相除的结果
		return result;         // 将结果返回
	}
}

# 5.4.1  throws关键字

案例三运行结果

运行代码，控制台显示的运行结果如下图所示。

# 案例三运行结果分析

在案例三中，main()方法继续使用throws关键字将Exception抛出，程序虽然可以通过编译，但从上图的运行结果可以看出，在运行时期由于没有对“/by zero”的异常进行处理，最终导致程序终止运行。

5.4.1  throws关键字

# 5.4.2  throw关键字

先定一个小目标！

# throw关键字

在Java程序中，除了throws关键字，还可以使用throw关键字抛出异常。与throws关键字不同的是，throw关键字用于方法体内，抛出的是一个异常实例，并且每次只能抛出一个异常实例。

5.4.2  throw关键字

# throw关键字的语法格式

使用throw关键字抛出异常的语法格式如下所示：

5.4.2  throw关键字

throw ExceptionInstance;

在方法中，通过throw关键字抛出异常后，还需要使用throws关键字或try…catch对异常进行处理。如果throw抛出的是error、RuntimeException或它们的子类异常对象，则无需使用throws关键字或try…catch对异常进行处理。

# throw关键字抛出异常

5.4.2  throw关键字

使用throw关键字抛出异常，通常有如下两种情况。
（1）当throw关键字抛出的异常是编译时异常时，第一种处理方式是在try代码块里使用throw关键字抛出异常，通过try代码块捕获该异常；第二种处理方式是在一个有throws声明的方法中使用throw关键字抛出异常，把异常交给该方法的调用者处理。
（2）当throw关键字抛出的异常是运行时异常时，程序既可以显式使用try…catch捕获并处理该异常，也可以完全不理会该异常，而把该异常交给方法的调用者处理。

# 5.4.2  throw关键字

案例演示

下面通过一个案例讲解throw关键字的使用。具体步骤如下所示。

// 定义printAge()输出年龄
public static void printAge(int age) throws Exception {
         if(age <= 0){
                  // 对业务逻辑进行判断，当输入年龄为负数时抛出异常
	throw new Exception("输入的年龄有误，必须是正整数！");
         }else {
	System.out.println("此人年龄为："+age);
         }
}

步骤一：定义方法printAge()输出年龄，代码如下所示：

# 5.4.2  throw关键字

public static void main(String[] args)  {
          // 下面的代码定义了一个try…catch语句用于捕获异常
          int age = -1;     
          try {
	printAge(age);
          } catch (Exception e) {  // 对捕获到的异常进行处理
	System.out.println("捕获的异常信息为：" + e.getMessage());
          }
}

步骤二：定义main()方法，定义try…catch语句用于捕获异常，在try{}中调用步骤一的方法。代码如下所示：

# 5.4.2  throw关键字

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 自定义异常类

5.5

# 5.5  自定义异常类

先定一个小目标！

# 自定义异常

Java中定义了大量的异常类，虽然这些异常类可以描述编程时出现的大部分异常情况，但是在程序开发中有时可能需要描述程序中特有的异常情况。例如，两数相除，不允许被除数为负数。此时，就无法使用Java提供的异常类表示该类异常，为了解决这个问题，Java允许用户自定义异常类，自定义的异常类必须继承自Exception或其子类。

5.5  自定义异常类

# 自定义异常示例代码

5.5  自定义异常类

自定义异常类的示例代码如下所示。

public class DivideByMinusException extends Exception{
	public DivideByMinusException (){
		super();          	// 调用Exception无参的构造方法
	}
	public DivideByMinusException (String message){
		super(message); 	// 调用Exception有参的构造方法
	}
}

在实际开发中，如果没有特殊的要求，自定义的异常类只需继承Exception类，在构造方法
中使用super()语句调用Exception的构造方法即可。

# 5.5  自定义异常类

使用自定义的异常类，需要用到throw关键字。使用throw关键字在方法中声明异常的实例
对象，语法格式如下：

throw Exception 异常对象

# 5.5  自定义异常类

案例一演示

修改5.4.2中案例的divide()方法，在divide()方法中判断被除数是否为负数，如果为负数，就使用throw关键字在方法中向调用者抛出自定义的DivideByMinusException异常对象。具体步骤如下所示。

public class DivideByMinusException extends Exception{
	public DivideByMinusException (){
		super();          	// 调用Exception无参的构造方法
	}
	public DivideByMinusException (String message){
		super(message); 	// 调用Exception有参的构造方法
	}
}

步骤一：自定义异常类DivideByMinusException，代码如下所示：

# 5.5  自定义异常类

public class Example08 {
	public static void main(String[] args) {
		int result = divide(4, -2);           
		System.out.println(result);
	}
	//下面的方法实现了两个整数相除
	public static int divide(int x, int y) {
		if(y<0){ 
		       throw new DivideByMinusException("除数是负数");	
         		}
		int result = x / y;   // 定义一个变量result记录两个数相除的结果
		return result;         // 将结果返回
	}
}

步骤二：定义两个整数相除的方法divide()，然后定义main()方法调用divide()方法，代码如下所示：

# 5.5  自定义异常类

案例一运行结果

运行代码，控制台显示的运行结果如下图所示。

# 案例一运行结果分析

从上图可以看出，程序在编译时就发生了异常。因为在一个方法内使用throw关键字抛出异常对象时，需要使用try…catch语句对抛出的异常进行处理，或者在divide()方法上使用throws关键字声明抛出异常，由该方法的调用者负责处理。但是案例一没有这样做。为了解决上图中出现的问题，对案例一进行修改，具体如下所示。

5.4.1  throws关键字

# 5.5  自定义异常类

案例二演示

修改案例一，在divide()方法上，使用throws关键字声明该方法抛出DivideByMinusException异常，并在调用divide()方法时使用try…catch语句对异常进行处理。具体步骤如下所示。

public class DivideByMinusException extends Exception{
	public DivideByMinusException (){
		super();          	// 调用Exception无参的构造方法
	}
	public DivideByMinusException (String message){
		super(message); 	// 调用Exception有参的构造方法
	}
}

步骤一：自定义异常类DivideByMinusException，代码如下所示：

# 5.5  自定义异常类

// 下面的方法实现了两个整数相除，并使用throws关键字声明抛出自定义异常
public static int divide(int x, int y) throws DivideByMinusException{
         if (y < 0) {
	throw new DivideByMinusException("除数是负数");
         }
         int result = x / y;  // 定义一个变量result记录两个数相除的结果
         return result;        // 将结果返回
         }
}

步骤二：两个整数相除方法divide()，并使用throws关键字声明抛出自定义异常，代码如下所示：

# 5.5  自定义异常类

public class Example09 {
          public static void main(String[] args) {
                           // 下面的代码定义了一个try…catch语句用于捕获异常
	         try {
		int result = divide(4, -2);  		
              		System.out.println(result);
	         } catch (DivideByMinusException e) {     // 对捕获到的异常进行处理
		System.out.println(e.getMessage()); // 打印捕获的异常信息
	         }
          }
}

步骤三：定义main()方法，在main()方法中定义try…catch语句用于捕获异常，并在try{}中调用步骤二的方法。代码如下所示：

# 5.5  自定义异常类

案例二运行结果

运行代码，控制台显示的运行结果如下图所示。

# 本章小结

本章主要介绍了异常的相关知识。首先简单介绍了什么是异常；然后介绍了运行时异常和编译时异常；接着介绍了异常的处理及语法和抛出异常；最后介绍了自定义异常。通过本章的学习，读者对Java中的异常会有一定的了解，掌握好这些知识，对以后的实际开发大有裨益。

本

章

小

结
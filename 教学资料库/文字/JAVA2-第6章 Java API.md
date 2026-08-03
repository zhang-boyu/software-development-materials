# 第6章  Java API

Java基础入门（第3版）

# 学习目标/Target

# 学习目标/Target

# 章节概述/ Summary

API（Application Programming Interface）指的是应用程序编程接口，API可以让编程变得更加方便简单。Java也提供了大量API供程序开发者使用，即Java API。Java API指的就是JDK提供的各种功能的Java类库，如之前所讲的Arrays、Collection类等，都是Java提供给开发者的类库。Java API非常多，无法针对所有的API都进行逐一讲解，本章将详细讲解实际开发中的常用API。

# 目录/Contents

# 目录/Contents

# 字符串类

6.1

# 6.1.1 String类

先定一个小目标！

# 6.1.1 String类

1. 使用字符串常量直接初始化一个String对象，语法格式如下。

String类对象进行初始化的方式

String 变量名 = 字符串;

使用上述语法格式初始化String对象,示例代码如下所示。

String str1 = null;   //将字符串str1设置为空
String str2 = "";     //将字符串str2设置为空字符串
String str3 = "abc"; //将字符串str3设置为abc

# 6.1.1 String类

每个字符串常量都可以当作一个String类的对象使用，因此字符串常量可以直接调用String类中提供的API，示例代码如下。

int len = "Hello World".length(); //len为11，即字符串包含字符的个数

# 6.1.1 String类

String类是专门用于处理字符串的类。字符串一旦被创建，其内容就不能再改变。例如下面的代码。

上述代码首先定义了一个类型为String的字符串s，并将其初始化为hello。接着为字符串s重新赋值为"helloworld"。

String s = "hello";
        s = "helloworld";

# 6.1.1 String类

字符串s的内存变化图：

在图中，s在初始化时，其内存地址指向的是字符串常量池的"hello"字符串的地址0x001。当为s重新赋值时为"helloworld"时，程序会在常量池分配一块内存空间存储"helloworld"字符串，然后将s指向"helloworld"字符串。由此可知，s的值发生了变化，是指s的指向发生了变化，但字符串"hello"被创建之后，存储在常量池中，它的值不能被改变。

# 6.1.1 String类

2. 调用String类的构造方法初始化字符串对象，其语法格式如下。

在上述语法中，字符串同样可以为空或是一个具体的字符串。当为具体字符串时，String会根据参数类型调用相应的构造方法来初始化字符串对象。

String 变量名 = new String(字符串);

# 6.1.1 String类

String类的常见构造方法

| 方法声明 | 功能描述 |
|---|---|
| String() | 创建一个内容为空的字符串 |
| String(String value) | String(String value) |
| String(char[] value) | 根据指定的字符数组value创建对象 |
| String(byte[] bytes) | 根据指定的字节数组bytes创建对象 |

# 6.1.1 String类

public class Example01 {
	public static void main(String[] args) throws Exception {
		// 创建一个空的字符串
		String str1 = new String();
		// 创建一个内容为abcd的字符串
		String str2 = new String("abcd");
		// 创建一个字符数组
		char[] charArray = new char[] { 'D', 'E', 'F' };
		String str3 = new String(charArray);
         		// 创建一个字节数组
         		byte[] arr = {97,98,99};		
		String str4 = new String(arr);
		System.out.println("a" + str1 + "b");
		System.out.println(str2);
		System.out.println(str3);
         		System.out.println(str4);
	}
}

案例演示

下面通过一个案例学习String类的使用。具体代码如下所示。

# 6.1.1 String类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 6.1.1 String类

小提示：字符串连接运算符

连接字符串可以通过运算符“+”来实现，例如文件6-1中，第13行代码中的（"a" + str1+ "b"），“+”的作用就是将两个字符串拼接到一起并生成一个新的字符串。在Java程序中，如果“+”的两边操作数中有一个为String类型，那么“+”就表示字符串连接运算符。

# 6.1.2 String类的常用方法

先定一个小目标！

# 6.1.2 String类的常用方法

String类的常用方法

| 方法声明 | 功能描述 |
|---|---|
| int length() | 返回当前字符串的长度，即字符串中字符的个数。 |
| int indexOf(int ch) | 返回指定字符ch在字符串中第一次出现位置的索引。 |
| int lastIndexOf(int ch) | 返回指定字符ch在字符串中最后一次出现位置的索引。 |
| int indexOf(String str) | 返回指定子字符串str在字符串第一次出现位置的索引。 |
| int lastIndexOf(String str) | 返回指定子字符串str在此字符串中最后一次出现位置的索引。 |
| char charAt(int index) | 返回字符串中index位置上的字符，其中index的取值范围是0~(字符串长度-1)。 |
| boolean endsWith(String suffix) | 判断此字符串是否以指定的字符串结尾。 |

# 6.1.2 String类的常用方法

| 方法声明 | 功能描述 |
|---|---|
| boolean equals(Object obj) | 比较obj与当前字符串对象的内容是否相同。 |
| boolean equalsIgnoreCase(String str) | 以忽略大小写的方式比较str与当前字符串对象的内容是否相同。 |
| int compareTo(String str) | 按对应字符的Unicode编码比较str与当前字符串对象的大小。若当前字符串对象比str大，返回正整数；若比str小，返回负整数；若相等则返回0。 |
| int compareToIgnoreCase(String str) | 按对应字符的Unicode编码以忽略大小写的方式比较str与当前字符串对象的大小。若当前字符串对象比str大，返回正整数；若比str小，返回负整数；若相等则返回0。 |
| boolean isEmpty() | 判断字符串长度是否为0，如果为0则返回true，反之则返回flase。 |
| boolean startsWith(String prefix) | 判断此字符串是否以指定的字符串prefix开始。 |

# 6.1.2 String类的常用方法

| 方法声明 | 功能描述 |
|---|---|
| boolean contains(CharSequence cs) | 判断此字符串中是否包含指定的字符序列cs。 |
| String toLowerCase() | 使用默认语言环境的规则将String中的所有字符都转换为小写。 |
| String toUpperCase() | 使用默认语言环境的规则将String中的所有字符都转换为大写。 |
| static String valueOf(int i) | 将int变量i转换成字符串。 |
| char[] toCharArray() | 将此字符串转换为一个字符数组。 |
| String replace(CharSequence oldstr, CharSequence newstr) | 使用newstr替换原字符串中的oldstr，返回一个新的字符串。 |
| String concat(String str) | 将str连接到当前字符串对象之后。 |

# 6.1.2 String类的常用方法

| 方法声明 | 功能描述 |
|---|---|
| String[] split(String regex) | 根据参数regex将原来的字符串分割为若干个子字符串。 |
| String substring(int beginIndex) | 返回一个新字符串，它包含从指定的beginIndex处开始，直到此字符串末尾的所有字符。 |
| String substring(int beginIndex, int endIndex) | 返回一个新字符串，它包含从指定的beginIndex处开始，直到索引endIndex-1处的所有字符。 |
| String trim() | 去除了原字符串首尾的空格。 |

# 6.1.2 String类的常用方法

1．获取字符串长度以及访问字符串中的字符

在Java程序中，有时需要获取字符串的一些信息，如获取字符串长度、获取指定索引位置的字符等。针对每一个操作，String类都提供了对应的方法。

# 6.1.2 String类的常用方法

public class Example02 {
 	public static void main(String[] args) {
 	       String s = "ababcdedcba"; // 定义字符串s
                       // 获取字符串长度，即字符个数
 	       System.out.println("字符串的长度为：" + s.length());
 	       System.out.println("字符串中第一个字符:" + s.charAt(0));
 	       System.out.println("字符c第一次出现的位置:" + s.indexOf('c'));
 	       System.out.println("字符c最后一次出现的位置:" + s.lastIndexOf('c'));
 	       System.out.println("子字符串ab第一次出现的位置：" + s.indexOf("ab")); 
 	       System.out.println("子字符串ab字符串最后一次出现的位置：" + 
           		s.lastIndexOf("ab"));
  	}
 }

案例演示

下面通过一个案例学习如何使用String类的方法获取字符串长度以及访问字符串中的字符。具体代码如下所示。

# 6.1.2 String类的常用方法

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 6.1.2 String类的常用方法

2．字符串的转换操作

程序开发中，经常需要对字符串进行转换操作。例如，将字符串转换成数组的形式，将字符串中的字符进行大小写转换等。

# 6.1.2 String类的常用方法

public static void main(String[] args) {
 	String str = "abcd";
 	System.out.print("将字符串转为字符数组后的结果:");
 	char[] charArray = str.toCharArray(); // 字符串转换为字符数组
 	for (int i = 0; i < charArray.length; i++) {
 		if (i != charArray.length - 1) {
 		// 如果不是数组的最后一个元素,在元素后面加逗号
 			System.out.print(charArray[i] + ",");
 		} else {
 		//如果不是数组的最后一个元素,则在元素后不加逗号
 			System.out.println(charArray[i]);
 		}
 	}
 	System.out.println("将int值转换为String类型之后的结果:String.valueOf(12));
 	System.out.println("将字符串转换成大写之后的结果:str.toUpperCase());
              	System.out.println("将字符串转换成小写之后的结果:str.toLowerCase());
}

案例演示

下面通过一个案例演示字符串的转换操作。具体代码如下所示。

# 6.1.2 String类的常用方法

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 6.1.2 String类的常用方法

3．字符串的替换和去除空格操作

程序开发中，用户输入数据时经常会不小心输入错误的数据和空格，这时可以调用String类的replace()和trim()方法，进行字符串的替换和去除空格操作。trim()方法用于去除字符串两端的空格，不能去除中间的空格。若想去除字符串中间的空格，需要调用String类的replace()方法。

# 6.1.2 String类的常用方法

public class Example04 {
       public static void main(String[] args) {
 	String s = "itcast";
 	// 字符串替换操作
 	System.out.println("将it替换成cn.it的结果:" + s.replace("it", "cn.it"));
 	// 字符串去除空格操作
 	String s1 = "     i t c a s t     ";
 	System.out.println("去除字符串两端空格后的结果:" + s1.trim());
 	System.out.println("去除字符串中所有空格后的结果:" + s1.replace(" ", ""));
       }
 }

案例演示

下面通过一个案例学习replace()和trim()方法的使用。具体代码如下所示。

# 6.1.2 String类的常用方法

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 6.1.2 String类的常用方法

4．字符串判断

操作字符串时，经常需要对字符串进行一些判断，例如判断字符串是否以指定的字符串开始、结束，判断字符串是否包含指定的字符串，字符串是否为空等。

# 6.1.2 String类的常用方法

public class Example05 {
          public static void main(String[] args) { 	
                    String s1 = "String"; // 定义一个字符串
 	String s2 = "string";
 	System.out.println("判断s1字符串对象是否以Str开头:" + s1.startsWith("Str"));
 	System.out.println("判断是否以字符串ng结尾:" + s1.endsWith("ng"));
 	System.out.println("判断是否包含字符串tri:" + s1.contains("tri"));
 	System.out.println("判断字符串是否为空:" + s1.isEmpty());
 	System.out.println("判断s1和s2内容是否相同:" + s1.equals(s2));
 	System.out.println("忽略大小写的情况下判断s1和s2内容是否相同:" + 
 				s1.equalsIgnoreCase(s2));
 	System.out.println("按对应字符的Unicode比较s1和s2的大小:" + s1.compareTo(s2));
         }
}

案例演示

下面通过一个案例演示如何调用string类提供的方法进行字符串判断。具体代码如下所示。

# 6.1.2 String类的常用方法

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 6.1.2 String类的常用方法

在判断两个字符串是否相等时，可以通过“==”和equals()方法两种方式对字符串进行比较，但这两种方式有明显的区别。equals()方法用于比较两个字符串内容是否相等，==方法用于比较两个字符串对象的地址是否相同。对于两个内容完全一样的字符串对象，调用equals()方法判断的结果是true，使用==判断的结果是false。为了便于理解，下面给出示例代码。

注意：“==”和equals()方法的区别

String str1 = new String("abc");
String str2 = new String("abc");
/*使用==判断的结果为false，因为
  *str1和str2是两个对象，地址不同*/
System.out.println(str1 == str2);
/*使用equals判断的结果为true，
 *因为str1和str2字符内容相同*/
System.out.println(str1.equals(str2));

# 6.1.2 String类的常用方法

5．字符串的截取和分割操作

在操作字符串时，截取和分割也是经常要执行的操作，例如，截取一个文本某一段内容，使用特殊的符号将字符串分割为若干段。String类提供了substring()方法和split()方法实现字符串的截取和分割操作，substring()方法用于截取字符串的一部分，split()方法用于将字符串按照某个字符进行分割。

# 6.1.2 String类的常用方法

public static void main(String[] args) {
 	String str = "石家庄-武汉-哈尔滨";
 	// 下面是字符串截取操作
 	System.out.println("从第5个字符截取到末尾的结果：str.substring(4));
 	System.out.println("从第5个字符截取到第6个字符的结果：str.substring(4, 6));
 	// 下面是字符串分割操作
 	System.out.print("分割后的字符串数组中的元素依次为:");
 	String[] strArray = str.split("-"); // 将字符串转换为字符串数组
	for (int i = 0; i < strArray.length; i++) {
	         if (i != strArray.length - 1) {
	             // 如果不是数组的最后一个元素,在元素后面加逗号
	             System.out.print(strArray[i] + ",");
	         } else {
	              System.out.println(strArray[i]);// 数组的最后一个元素后面不加逗号
	         }
	}
}

案例演示

下面通过一个案例学习substring()方法和split()方法的调用。具体代码如下所示。

# 6.1.2 String类的常用方法

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 脚下留心

字符串索引越界异常

String字符串在获取某个字符时，会用到字符的索引，当访问字符串中的字符时，如果字符的索引不存在，则会发生StringIndexOutOfBoundsException（字符串索引越界异常）。

# 脚下留心

字符串索引越界异常

public class Example07 {
 	public static void main(String[] args) {
 		String s = "itcast"; 
 		System.out.println(s.charAt(8));  
 	}
 }

案例演示

下面通过一个案例演示字符串索引越界异常。具体代码如下所示。

# 脚下留心

字符串索引越界异常

运行结果

运行代码，控制台显示的运行结果如下图所示。

由图可知，访问字符串中的字符时，不能超出字符的索引范围，否则会出现异常，这与数组中的索引越界异常非常相似。

# 6.1.3 StringBuffer类

先定一个小目标！

# 6.1.3 StringBuffer类

在Java中，因为String类是final类型的，所以使用String定义的字符串是一个常量，也就是说使用String定义的字符串一旦创建，其内容和长度是不可改变的。为了便于对字符串进行修改，Java提供了StringBuffer类（也称字符串缓冲区）来操作字符串。StringBuffer类和String类最大的区别在于它的内容和长度都是可以改变的。StringBuffer类似一个字符容器，当在其中添加或删除字符时，所操作的都是这个字符容器，因此并不会产生新的StringBuffer对象。

# 6.1.3 StringBuffer类

StringBuffer类的常用方法

| 方法声明 | 功能描述 |
|---|---|
| StringBuffer() | 创建初始容量为16，不含任何内容的字符串缓冲区 |
| StringBuffer(int capacity) | 创建初始容量为capacity，不含任何内容的字符串缓冲区 |
| StringBuffer(String s) | 创建初始容量为s.length()+16，内容为s的字符串缓冲区 |
| int length() | 获取缓冲区中字符串内容的长度 |
| int capacity() | 获取字符串缓冲区的当前容量 |
| StringBuffer append(char c) | 添加参数到StringBuffer对象中 |
| StringBuffer insert(int offset,String str) | 在字符串的offset位置插入字符串str |
| StringBuffer deleteCharAt(int index) | 移除此序列指定位置的字符 |

# 6.1.3 StringBuffer类

| 方法声明 | 功能描述 |
|---|---|
| StringBuffer delete(int start,int end) | 删除StringBuffer对象中指定范围的字符或字符串序列 |
| StringBuffer replace(int start,int end,String s) | 在StringBuffer对象中替换指定的字符或字符串序列 |
| void setCharAt(int index, char ch) | 修改指定位置index处的字符序列 |
| String toString() | 返回StringBuffer缓冲区中的字符串 |
| StringBuffer reverse() | 反转字符串 |
| String substring(int start) | 获取缓冲区中字符串从索引start（含）至末尾的子串 |
| String substring(int start,int end) | 获取缓冲区中字符串从索引start（含）至索引end（不含）的子串 |
| String toString() | 获取缓冲区中的字符串 |

# 6.1.3 StringBuffer类

案例演示

下面通过一个案例学习StringBuffer的一系列常用方法的具体使用。具体步骤如下。

步骤一：定义add()方法，用于实现字符串的添加操作，调用append()方法插入的新字符串始终位于字符串sb的末尾，调用insert()方法将新字符串插入指定位置。代码如下所示：

public static void add() {
 	StringBuffer sb = new StringBuffer(); // 定义一个字符串缓冲区
 	sb.append("abcdefg"); 	// 在末尾添加字符串
 	sb.append("hij").append("klmn"); // 连续调用append()方法添加字符串
 	System.out.println("append添加结果：" + sb);
 	sb.insert(2, "123"); 		// 在指定位置插入字符串
 	System.out.println("insert添加结果：" + sb);
 }

# 6.1.3 StringBuffer类

步骤二：定义remove()方法，用于删除字符串，调用delete()方法删除指定范围字符串，调用deleteCharAt()方法删除指定位置字符串。代码如下所示：

public static void remove() {
	StringBuffer sb = new StringBuffer("abcdefg");
	sb.delete(1, 5);    		 // 指定范围删除
	System.out.println("删除指定位置结果：" + sb);
	sb.deleteCharAt(2); 		// 指定位置删除
 	System.out.println("删除指定位置结果：" + sb);
	sb.delete(0, sb.length()); 	// 清空缓冲区
	System.out.println("清空缓冲区结果：" + sb);
}

# 6.1.3 StringBuffer类

步骤三：定义alter()方法，用于实现字符串的替换和反转操作，调用setCharAt()方法修改指定字符，调用replace()方法替换指定位置字符串或字符，调用reverse()方法将字符串反转。代码如下所示：

public static void alter() {
 	StringBuffer sb = new StringBuffer("abcdef");
 	sb.setCharAt(1, 'p');    	// 修改指定位置字符
 	System.out.println("修改指定位置字符结果：" + sb);
 	sb.replace(1, 3, "qq"); 		// 替换指定位置字符串或字符
 	System.out.println("替换指定位置字符（串）结果：" + sb);
 	System.out.println("字符串翻转结果：" + sb.reverse());
 }

# 6.1.3 StringBuffer类

步骤四：定义sub()方法，用于实现字符串的截取操作，调用capacity()方法获取了字符串缓冲区的初始容量，调用substring()方法截取指定字符串。代码如下所示：

public static void sub() {
 	StringBuffer sb = new StringBuffer(); // 定义一个字符串缓冲区
 	System.out.println("获取sb的初始容量：" + sb.capacity());
 	sb.append("itcast123"); 	// 在末尾添加字符串
 	System.out.println("append添加结果：" + sb);
 	System.out.println("截取第7~9个字符：" + sb.substring(6,9));}
}

# 6.1.3 StringBuffer类

public static void main(String[] args) {
	System.out.println("1、添加------------------------");
	add();
	System.out.println("2、删除------------------------");
	remove();
	System.out.println("3、修改------------------------");
	alter();
	System.out.println("4、截取------------------------");
	sub();
}

步骤五：定义main()方法，一次执行定义的添加、删除、修改、截取四个方法。代码如下所示：

# 6.1.3 StringBuffer类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 多学一招

StringBuilder类

除了StringBuffer类，还可以使用StringBuilder类修改字符串，StringBuffer类和StringBuilder类的对象都可以被多次修改，且不产生新的未使用对象。StringBuilder类与StringBuffer类的功能相似，且两个类中所提供的方法也基本相同。二者之间最大不同在于StringBuffer的方法是线程安全的，而StringBuilder没有实现线程安全功能，所以性能略高。通常情况下，如果创建一个内容可变的字符串对象，应该优先考虑使用StringBuilder类。

# 多学一招

StringBuilder类

StringBuilder同样提供了一系列添加（append）、插入（insert）、替换（raplace）和删除（delete）的方法，读者可以参考StringBuffer类的常用方法表学习StringBuilder常见操作。
StringBuilder类、StringBuffer类和String类有很多相似之处，初学者在使用时很容易混淆。接下来针对这三个类进行对比，简单归纳一下三者的不同，具体如下。

# 多学一招

StringBuilder类

（1）String类表示的字符串是常量，一旦创建后，内容和长度都是无法改变的。而StringBuilder和StringBuffer表示字符容器，其内容和长度可以随时修改。在操作字符串时，如果该字符串仅用于表示数据类型，则使用String类即可，但是如果需要对字符串中的字符进行增删操作，则使用StringBuffer与StringBuilder类。如果有大量字符串拼接操作，并且不要求线程安全的情况下，采用StringBuilder类更高效。相反如果需要线程安全则需要使用StringBuffer类。线程安全相关知识将在第12章多线程详细讲解。

# 多学一招

StringBuilder类

（2）对于euals()方法的使用我们已经有所了解，但是StringBuffer类与StringBuilder类中并没有重写Object类的equals()方法，也就是说，equals()方法对于StringBuffer类与StringBuilder类来言并不起作用，具体示例如下。

String s1 = new String("abc");
String s2 = new String("abc");
System.out.println(s1.equals(s2));      // 打印结果为true
StringBuffer sb1 = new StringBuffer("abc");
StringBuffer sb2 = new StringBuffer("abc");
System.out.println(sb1.equals(sb2));   // 打印结果为false
StringBuilder sbr1=new StringBuilder("abc");
StringBuilder sbr2=new StringBuilder("abc");
System.out.println(sbr1.equals(sbr2));	//打印结果为false

# 多学一招

StringBuilder类

（3）String类对象可以用操作符“+”进行连接，而StringBuffer类和StringBuild类的对象之间不能，具体示例如下。

String s1 = "a";
String s2 = "b";
String s3 = s1+s2;                             // 合法
System.out.println(s3);                       // 打印输出 ab
StringBuffer sb1 = new StringBuffer("a");
StringBuffer sb2 = new StringBuffer("b");
StringBuffer sb3 = sb1 + sb2;                // 编译出错
StringBuilder sb4 = new StringBuilder("c");
StringBuilder sb5 = new StringBuilder("d");
StringBuilder sb6 = sb4 + sb5;               // 编译出错

# System类与Runtime类

6.2

# 6.2.1 System类

先定一个小目标！

# 6.2.1 System类

System类对读者来说并不陌生，因为在之前所学知识中，需要打印结果时，使用的打印语句“System.out.println();”中就用到了System类。System类定义了一些与系统相关的属性和方法，它所提供的属性和方法都是静态的，因此，可以使用System类直接引用类中的属性和方法。System类的常用方法如下所示。

# 6.2.1 System类

System类的常用方法

| 方法名称 | 功能描述 |
|---|---|
| static void exit(int status) | 该方法用于终止当前正在运行的Java虚拟机，其中参数status表示状态码，若状态码非0 ，则表示异常终止 |
| static void gc() | 运行垃圾回收器，并对内存中的垃圾进行回收 |
| static void currentTimeMillis() | 返回以毫秒为单位的当前时间 |
| static void arraycopy(Object src,int srcPos,Object dest,int destPos,int length) | 从src引用的指定源数组的srcPos位置，复制length个元素，到dest引用的数组的destPos位置 |
| static Properties getProperties() | 获取当前系统全部属性 |
| static String getProperty(String key) | 获取指定键描述的系统属性 |

# 6.2.1 System类

1．arraycopy()方法

arraycopy()方法用于将源数组中的元素复制到目标数组，其声明格式如下。

static void arraycopy(Object src,int srcPos,Object dest,
		int destPos,int length)

# 6.2.1 System类

上述声明格式中参数含义如下。
 src：表示源数组。
 dest：表示目标数组。
 srcPos：表示源数组中复制元素的起始位置，即从哪个位置开始复制元素。
 destPos：表示复制到目标数组的起始位置，即复制到目标数组的哪个位置。
 length：表示复制元素的个数。
注意:在进行数组元素复制时，目标数组必须有足够的空间来存放复制的元素，否则会发生索引越界异常。

# 6.2.1 System类

public class Example09 {
 	public static void main(String[] args) {
 		int[] fromArray = { 10, 11, 12, 13, 14, 15 };    // 源数组
 		int[] toArray = { 20, 21, 22, 23, 24, 25, 26 }; // 目标数组
 		System.arraycopy(fromArray, 2, toArray, 3, 4);  // 复制数组元素
 		// 打印复制后数组的元素
          		System.out.println("复制后的数组元素为：");
 	    	for (int i = 0; i < toArray.length; i++) {
 		    System.out.print(toArray[i]+" ");
 		}
 	}
 }

案例演示

下面通过一个案例演示数组元素的复制。具体代码如下所示。

# 6.2.1 System类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 6.2.1 System类

2．currentTimeMillis()方法

currentTimeMillis()方法用于获取当前系统的时间，返回值类型是long，该值表示当前时间与1970年1月1日0点0分0秒之间的时间差，单位是毫秒，通常也将该值称作时间戳（系统当前时间）。

# 6.2.1 System类

public class Example10 {
      public static void main(String[] args) {
 	long startTime = System.currentTimeMillis();// 循环开始时的当前时间
 	int sum = 0;
 	for (int i = 0; i < 1000000000; i++) {
 		sum += i;
 	}
 	long endTime = System.currentTimeMillis();// 循环结束后的当前时间
 	System.out.println("程序运行的时间为："+(endTime - startTime)+"毫秒");
       }
 }

案例演示

下面通过一个案例演示currentTimeMillis()方法的使用，本案例要求计算程序在进行求和操作时所消耗的时间。具体代码如下所示。

# 6.2.1 System类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 6.2.1 System类

3．getProperties()和getProperty()方法

System类的getProperties()方法用于获取当前系统的全部属性，该方法会返回一个Properties对象，Properties对象封装了系统的所有属性，这些属性以键值对形式存在。getProperty()方法可以根据系统的属性名获取对应的属性值。

# 6.2.1 System类

public class Example11 {
	public static void main(String[] args) {
		// 获取当前系统属性
		Properties properties = System.getProperties();
		// 获取所有系统属性的key，返回Enumeration对象
		Enumeration propertyNames = properties.propertyNames();
		while (propertyNames.hasMoreElements()) {
			// 获取系统属性的键key
			String key = (String) propertyNames.nextElement();
			// 获取当前键key对应的值value
			String value = System.getProperty(key);
			System.out.println(key + "--->" + value);
		}
	}
}

案例演示

下面通过一个案例演示getProperties()和getProperty()方法的使用。具体代码如下所示。

# 6.2.1 System类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 6.2.1 System类

4．gc()方法

在Java中，一个对象如果不再被任何栈内存所引用，该对象就称为垃圾对象。垃圾对象会占用内存空间，时间一长，垃圾对象越来越多，就会导致内存空间不足。针对这种情况，Java引入了垃圾回收机制。除了等待Java虚拟机进行自动垃圾回收外，还可以通过调用System.gc()方法通知Java虚拟机立即进行垃圾回收。

# 步骤一：定义Person类，创建私有变量name和age，定义有参构造方法，重写toString()方法，定义finalize方法。代码如下所示：

class Person {
    private String name;
    private int age;
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    @Override
    public String toString() {
        return "姓名:"+this.name+"，年龄:"+this.age;
    }
    // 下面定义的finalize方法会在垃圾回收前被调用
    public void finalize() throws Throwable {
        System.out.println("对象被释放-->"+this);
    }
}

6.2.1 System类

# 步骤二：定义main()方法，创建对象p并赋值。然后将p对象的值设置为null断开引用，让对象p成为垃圾。调用gc()方法通知虚拟机进行垃圾回收。使用了一个空的for循环，延长程序运行的时间，从而能够更好地看到垃圾对象被回收的过程。代码如下所示：

public class Example12{
    public static void main(String[] args) {
        // 下面是创建Person对象
        Person p = new Person("张三",20);
        // 下面将变量置为null，让对象p成为垃圾
        p = null;
        // 调用方法进行垃圾回收
        System.gc();
        for (int i = 0; i < 1000000; i++) {
            // 为了延长程序运行的时间，执行空循环
        }
    }
}

6.2.1 System类

# 6.2.1 System类

运行结果

运行代码，控制台显示的运行结果如下图所示。

由图可知，Person类的finalize()方法被执行了，但是在案例中，并没有通过对象p调用finalize()方法，因此，可以表明对象p在回收之前调用了finalize()方法。

# 6.2.2 Runtime类

先定一个小目标！

# 6.2.2 Runtime类

Runtime类用于封装JVM虚拟机进程，通过Runtime类，可以获取虚拟机运行时状态。每一个JVM都对应着一个Runtime类的实例。在JDK文档中读者不会发现任何有关Runtime类构造方法的定义，这是因为Runtime类本身的构造方法是私有化的(单例设计模式)，若想在程序中获取一个Runtime类实例，只能通过调用getRuntime()方法获取，getRuntime()方法是Runtime类提供的一个静态方法，用于获取Runtime类实例。

# 6.2.2 Runtime类

由于Runtime类封装了虚拟机进程，因此，在程序中通常会通过Runtime类的实例对象获取当前虚拟机的相关信息。通过调用getRuntime()方法获取Runtime类实例的具体方式如下。

getRuntime()方法

Runtime run = Runtime.getRuntime();

# 6.2.2 Runtime类

Runtime类的常用方法

| 方法名称 | 功能描述 |
|---|---|
| getRuntime() | 用于获取Runtime类的实例 |
| exec(String command) | 用于根据指定的路径执行对应的可执行文件 |
| freeMemory() | 用于返回Java虚拟机中的空闲内存量，以字节为单位 |
| maxMemory() | 用于返回Java虚拟机的最大可用内存量 |
| availableProcessors() | 用于返回当前虚拟机的处理器个数 |
| totalMemory() | 用于返回Java虚拟机中的内存总量 |

# 6.2.2 Runtime类

1.获取当前虚拟机信息

Runtime类可以获取当前Java虚拟机的处理器的个数、空闲内存量、最大可用内存量和内存总量的信息等，通过这些信息可以清楚地知道JVM的内存使用情况。

# 6.2.2 Runtime类

public class Example13 {
       public static void main(String[] args) {
 	Runtime rt = Runtime.getRuntime(); // 创建Runtime对象
 	System.out.println("处理器的个数: " + rt.availableProcessors()+"个");
 	System.out.println("空闲内存数量: " + rt.freeMemory() / 1024 / 1024 + "M");
 	System.out.println("最大可用内存数量: " + rt.maxMemory() / 1024 / 1024 + "M");
                	System.out.println("虚拟机中内存总量: " + rt.totalMemory() / 1024 / 1024 + "M");
      }
 }

案例演示

下面通过一个案例演示Runtime类的常用方法的调用。具体代码如下所示。

# 6.2.2 Runtime类

运行结果

运行代码，控制台显示的运行结果如下图所示。

需要注意的是：因为每个人的电脑配置不同，打印结果可能不同，另外空闲内存量、可用最大内存量和内存总量都是以字节为单位计算的，本案例将字节换算成了兆（MB）。

# 6.2.2 Runtime类

2.操作系统进程

Runtime类中提供了一个exec()方法，该方法用于执行一个DOS命令，exec()方法的执行效果与DOS命令的效果相同。

# 6.2.2 Runtime类

import java.io.IOException;
 public class Example14{
 	public static void main(String[] args) throws IOException {
 	          Runtime rt = Runtime.getRuntime(); // 创建Runtime实例对象
 	          rt.exec("notepad.exe");              // 调用exec()方法
 	}
 }

案例演示

调用Runtime类的exec()方法，将notepad.exe作为参数传入exec()方法，打开Windows自带的记事本。具体代码如下所示。

# 6.2.2 Runtime类

运行结果

运行程序，系统会在桌面上打开一个记事本，如下图所示。

# 6.2.2 Runtime类

在案例运行后，Windows系统产生了一个新的进程notepad.exe，可以通过任务管理器查看该进程。

# 6.2.2 Runtime类

public class Example {
	     public static void main(String[] args) throws Exception {
	        Runtime rt = Runtime.getRuntime();  // 创建一个Runtime实例对象
	        Process process = rt.exec("notepad.exe");//得到表示进程的Process对象
	        Thread.sleep(3000); // 程序休眠3秒
	        process.destroy();  //关闭进程
	     }
     }

Runtime类的exec()方法的返回值为Process类型的对象，表示一个操作系统的进程类，通过Process类可以进行系统进程的控制，如关闭进程只需调用Process类的destroy()方法即可，具体代码如下所示。

# Math类与Random类

6.3

# 6.3.1 Math类

先定一个小目标！

# Math类是一个工具类，类中包含许多用于进行科学计算的方法，如计算一个数的平方根、绝对值或获取一个随机数等。因为Math类构造方法的访问权限是private，所以无法创建Math类的对象。Math类中所有方法都是静态方法，可以直接通过类名调用Math类中的方法。除静态方法外，Math类中还定义了两个静态常量PI和E，分别代表数学中的π和e。

6.3.1 Math类

# 6.3.1 Math类

Math类的常用方法

| 方法声明 | 功能描述 |
|---|---|
| abs(double a) | 用于计算a的绝对值 |
| sqrt(double a) | 用于计算a的方根 |
| ceil(double a) | 用于计算大于a的最小整数，并将该整数转化为double型数据。例如Math.ceil(15.2)的值是16.0 |
| floor(double a) | 用于计算小于a的最大整数，并将该整数转化为double型数据。例如Math.ceil(-15.2)的值是-16.0 |
| round(double a) | 用于计算小数a进行四舍五入后的值 |
| max(double a,double b) | 用于返回a和b的较大值 |

# 6.3.1 Math类

| 方法声明 | 功能描述 |
|---|---|
| min(double a,double b) | 用于返回a和b的较小值 |
| random() | 用于生成一个大于0.0小于1.0的随机值（包括0不包括1） |
| sin(double a) | 返回a的正弦值 |
| asin(double a) | 返回a的反正弦值 |
| pow(double a,double b) | 用于计算a的b次幂，即ab的值 |

# 6.3.1 Math类

public class Example15 {
      public static void main(String[] args) { 
           System.out.println("计算-10的绝对值: " + Math.abs(-10));
           System.out.println("求大于5.6的最小整数: " + Math.ceil(5.6));
           System.out.println("求小于-4.2的最大整数: " + Math.floor(-4.2));
           System.out.println("对-4.6进行四舍五入: " + Math.round(-4.6));
           System.out.println("求2.1和-2.1中的较大值: " + Math.max(2.1, -2.1));
           System.out.println("求2.1和-2.1中的较小值: " + Math.min(2.1, -2.1));
           System.out.println("生成一个大于等于0.0小于1.0随机值: " +Math.random());
           System.out.println("计算1.57的正弦结果: "+Math.sin(1.57));
           System.out.println("计算4的开平方的结果: "+Math.sqrt(4));
      }
}

案例演示

下面通过一个案例演示Math方法的应用。具体代码如下所示。

# 6.3.1 Math类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 6.3.2 Random类

先定一个小目标！

# 6.3.2 Random类

Random类可以产生指定取值范围的随机数字。Random类提供了两个构造方法，如下表所示。

Random的构造方法

| 方法声明 | 功能描述 |
|---|---|
| Random() | 使用当前机器时间创建一个Random对象 |
| Random(long seed) | 使用参数seed指定的种子创建一个Random对象 |

# 6.3.2 Random类

import java.util.Random;
 public class Example16 {
 	public static void main(String args[]) {
 		Random random = new Random(); // 不传入种子
 		// 随机产生10个[0,100)之间的整数
 		for (int x = 0; x < 10; x++) {
 			System.out.println(random.nextInt(100));
 		}
 	}
 }

案例演示

下面通过一个案例演示使用无参构造方法来产生随机数。具体代码如下所示。

# 6.3.2 Random类

运行结果

第一次运行代码，控制台显示的运行结果如下图所示。

# 6.3.2 Random类

运行结果

第二次运行代码，控制台显示的运行结果如下图所示。

# 6.3.2 Random类

两次运行结果分析

由上述两次运行的结果图可知，案例运行两次产生的随机数序列是不一样的。这是因为创建Random的对象时，没有指定种子，系统会以当前时间戳作为种子，产生随机数。由于每一时刻的时间戳都不一样，所以每一次运行时，产生的随机数也不一样。

# 6.3.2 Random类

import java.util.Random;
 public class Example17 {
 	public static void main(String args[]) {
 		Random r = new Random(13); // 创建对象时传入种子
 		// 随机产生10个[0,100)之间的整数
 		for (int x = 0; x < 10; x++) {
 			System.out.println(r.nextInt(100));
 		}
 	}
 }

案例演示

下面通过一个案例使用有参构造方法产生随机数。具体代码如下所示。

# 6.3.2 Random类

运行结果

第一次运行代码，控制台显示的运行结果如下图所示。

# 6.3.2 Random类

运行结果

第二次运行代码，控制台显示的运行结果如下图所示。

由两次运行结果可知，当创建Random类对象时，如果指定了相同的种子，则每个对象产生的随机数序列相同。

# 6.3.2 Random类

Random类提供了更多的方法来生成随机数，不仅可以生成整数类型的随机数，还可以生成浮点类型的随机数。Random类的常用方法，如下表所示。

Random类的常用方法

| 方法声明 | 功能描述 |
|---|---|
| boolean nextBoolean() | 随机生成boolean类型的随机数 |
| double nextDouble() | 随机生成double类型的随机数 |
| float nextFloat() | 随机生成float类型的随机数 |
| long nextLong() | 随机生成long类型的随机数 |
| int nextInt() | 随机生成int类型的随机数 |
| int nextInt(int n) | 随机生成[0~n)之间int类型的随机数 |

# 6.3.2 Random类

import java.util.Random;
 public class Example18 {
     public static void main(String[] args) {
         Random r = new Random(); // 创建Random实例对象
         System.out.println("生成boolean类型的随机数: " + r.nextBoolean());
         System.out.println("生成float类型的随机数: " + r.nextFloat());
         System.out.println("生成double类型的随机数:" + r.nextDouble());
         System.out.println("生成int类型的随机数:" + r.nextInt());
         System.out.println("生成0~100之间int类型的随机数:" +r.nextInt(100));
         System.out.println("生成long类型的随机数:" + r.nextLong());
     }
}

案例演示

下面通过一个案例学习Random类的常用方法。具体代码如下所示。

# 6.3.2 Random类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# BigInteger类与BigDecimal类

6.4

# 6.4.1 BigInteger类

先定一个小目标！

# 当程序需要处理一个非常大的整数时，如果这个数值超出了long类型的取值范围，则无法使用基本类型接收。早期程序开发者使用String类进行大整数的接收，使用String类接收大整数之后，再采用拆分的方式进行计算，操作过程非常麻烦。为了解决这个问题，Java提供了BigInteger类。BigInteger表示大整数类，定义在java.math包中，如果在开发时需要定义一个超出long类型的整型数据，可以使用BigInteger类的对象接收该数据。

6.4.1 BigInteger类

# BigInteger类封装了很多常用的基本运算方法，如下表所示。

BigInteger类中常用的基本运算方法

6.4.1 BigInteger类

| 方法声明 | 功能描述 |
|---|---|
| BigInteger(String val) | 将字符串val变为BigInteger类型的数据 |
| BigInteger add(BigInteger val) | 返回当前对象与val的和 |
| BigInteger subtract(BigInteger val) | 返回当前对象与val的差 |
| BigInteger multiply(BigInteger val) | 返回当前对象与val的积 |
| BigInteger divide(BigInteger val) | 返回当前对象与val的商 |

# BigInteger类中常用的基本运算方法

6.4.1 BigInteger类

| 方法声明 | 功能描述 |
|---|---|
| BigInteger max(BigInteger val) | 返回当前对象与val之中的较大值 |
| BigInteger min(BigInteger val) | 返回当前对象与val之中的较小值 |
| BigInteger[] divideAndRemainder(BigInteger val) | 除法操作，计算当前对象/val的结果，返回一个数组，数组的第1个元素为商，第2个元素为余数 |

# import java.math.BigInteger;
class Example19 {
    public static void main(String[] args) {
         BigInteger bi1 = new BigInteger("123456789");  // 创建BigInteger对象
         BigInteger bi2 = new BigInteger("987654321");  // 创建BigInteger对象
         System.out.println("bi2与bi1的和: " + bi2.add(bi1));
         System.out.println("bi2与bi1的差: " + bi2.subtract(bi1));
         System.out.println("bi2与bi1的积: " + bi2.multiply(bi1));
         System.out.println("bi2与bi1的商: " + bi2.divide(bi1));
         System.out.println("bi2与bi1之间的较大值: " + bi2.max(bi1));
         System.out.println("bi2与bi1之间的较小值: " + bi2.min(bi1));
         //创建BigInteger数组接收bi2除以bi1的商和余数
         BigInteger result[] = bi2.divideAndRemainder(bi1);  
         System.out.println("bi2除以bi1的商: " + result[0]+":bi2除以bi1的余数："+result[1]);
    }
}

案例演示

下面通过一个案例学习BigInteger类常用的方法。具体代码如下所示。

6.4.1 BigInteger类

# 运行结果

运行代码，控制台显示的运行结果如下图所示。

6.4.1 BigInteger类

# 先定一个小目标！

6.4.2 BigDecimal类

# 在进行浮点数运算的时候，float类型和double类型很容易丢失精度，为了能够精确的表示、计算浮点数，Java提供了BigDecimal类。BigDecimal类可以表示任意精度的小数，多用于数字精度要求高的场景，例如商业计算、货币值计算等。

6.4.2 BigDecimal类

# 6.4.2 BigDecimal类

BigDecimal类封装了很多常用的方法，如下表所示。

BigDecimal类中常用的方法

| 方法声明 | 功能描述 |
|---|---|
| BigDecimal BigDecimal(String val) | 将字符串val转为BigDecimal类型的数据 |
| static BigDecimal valueOf(double d) | 将double类型的数据转为BigDecimal类型的数据 |
| BigDecimal add(BigDecimal val) | 返回当前对象与val的和 |
| BigDecimal subtract(BigDecimal val) | 返回当前对象与val的差 |
| BigDecimal multiply(BigDecimal val) | 返回当前对象与val的积 |
| BigDecimal divide(BigDecimal val) | 返回当前对象与val的商 |
| BigDecimal max(BigDecimal val) | 返回当前对象与val之中的较大值 |
| BigDecimal min(BigDecimal val) | 返回当前对象与val之中的较小值 |

# 6.4.2 BigDecimal类

案例演示

下面通过一个案例学习BigDecimal类常用的方法。具体代码如下所示。

import java.math.BigDecimal;
public class Example20 {
    public static void main(String[] args) {
        BigDecimal bd1 = new BigDecimal("0.001");  // 创建BigDecimal对象
        BigDecimal bd2 = BigDecimal.valueOf(0.009);// 创建BigDecimal对象
        System.out.println("bd2与bd1的和: " + bd2.add(bd1));
        System.out.println("bd2与bd1的差: " + bd2.subtract(bd1));
        System.out.println("bd2与bd1的积: " + bd2.multiply(bd1));
        System.out.println("bd2与bd1的商: " + bd2.divide(bd1));
        System.out.println("bd2与bd1之间的较大值: " + bd2.max(bd1));
        System.out.println("bd2与bd1之间的较小值: " + bd2.min(bd1));
    }
}

# 6.4.2 BigDecimal类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 日期与时间类

6.5

# 6.5.1 Date类

先定一个小目标！

# JDK的java.util包提供了一个Date类用于表示日期和时间，Date类在JDK 1.0时就已经开始使用。随着JDK版本的不断升级和发展，Date类中大部分的构造方法和普通方法都已经不再推荐使用。在JDK 11中，Date类只有下面两个构造方法是实际开发中经常被应用到的。
 Date()：用于创建当前日期时间的Date对象。
 Date(long date)：用于创建指定时间的Date对象，其中date参数表示1970年1月1日0时0分0（称为历元）以来的毫秒数，即时间戳。

6.5.1 Date类

# 下面通过一个案例演示如何使用这两个构造函数创建Date对象。具体代码如下所示。

import java.util.*;
public class Example19 {
	public static void main(String[] args) {
	         // 创建表示当前时间的Date对象
	         Date date1 = new Date();
	         // 获取当前时间后1秒的时间
	         Date date2 = new Date(System.currentTimeMillis() + 1000);
	         System.out.println(date1);
	         System.out.println(date2);
	}
}

案例演示

6.5.1 Date类

# 运行结果

运行代码，控制台显示的运行结果如下图所示。

由图可知，程序已经输出了当前计算机的日期时间以及当前时间后一秒的日期时间。

6.5.1 Date类

# 6.5.2 Calendar类

先定一个小目标！

# 上一节学习了使用Date类获取计算机的当前日期和时间，但是Date类输出的日期格式不符合国内的日期标准格式。所以从 JDK 1.1 开始，Java提供了Calendar类，用Calendar类中的方法取代了Date类的相应功能。Calendar类也用于完成日期和时间字段的操作，它可以通过特定的方法设置和读取日期的特定部分，比如年、月、日、时、分、秒等。

6.5.2 Calendar类

# Calendar类是一个抽象类，不可以被实例化，如果想在程序中获取一个Calendar实例，则需要调用Calendar类的静态方法getInstance()。通过调用getInstance()方法获取Calendar实例的具体示例如下。

getInstance()方法

Calendar calendar = Calendar.getInstance();

6.5.2 Calendar类

# Calendar类的常用方法

6.5.2 Calendar类

| 方法声明 | 功能描述 |
|---|---|
| int get(int field) | 返回指定日历字段field的值 |
| void add(int field,int amount) | 根据日历规则，为指定的日历字段增加或减去指定的时间量 |
| void set(int field,int value) | 将指定日历字段field的值设置为value |
| void set(int year,int month,int date) | 设置Calendar对象的年、月、日三个字段的值 |
| void set(int year.int month,int date,int hourOfDay,int minute,int second) | 设置Calendar对象的年、月、日、时、分、秒六个字段的值 |

# 表中的大多数方法都用到了int类型的参数field，该参数需要接收Calendar类中定义的常量值，这些常量值分别表示不同的字段，Calendar类常用的常量值如下所示。
Calendar.YEAR：用于获取当前年份。
Calendar.MONTH：用于获取当前月份，需要注意的是，在使Calendar.MONTH
             字段时，月份的起始值是从0开始的，而不是从1开始，因此要获取当前的月
             需要在Calendar.MONTH的基础上加1。
Calendar.DATE：用于获取当前日。
Calendar.HOUR：用于获取时。
Calendar.MINUTE：用于获取分。
Calendar.SECOND：用于获取秒。

6.5.2 Calendar类

# 下面通过一个案例学习Calender类如何获取当前计算机的日期和时间。具体代码如下所示。

import java.util.*;
public class Example21 {
          public static void main(String[] args) {
          	// 获取表示当前时间的Calendar对象
 	Calendar calendar = Calendar.getInstance();
 	int year = calendar.get(Calendar.YEAR);        // 获取当前年份
 	int month = calendar.get(Calendar.MONTH) + 1; // 获取当前月份
 	int date = calendar.get(Calendar.DATE);        // 获取当前日
 	int hour = calendar.get(Calendar.HOUR);        // 获取时
 	int minute = calendar.get(Calendar.MINUTE);   // 获取分
 	int second = calendar.get(Calendar.SECOND);   // 获取秒
 	System.out.println("当前时间为:" + year + "年 " + month + "月 " 
 	          + date + "日 "+ hour + "时 " + minute + "分 " + second + "秒");
          }
}

案例演示

6.5.2 Calendar类

# 运行结果

运行代码，控制台显示的运行结果如下图所示。

由图可知，程序已经输出了当前计算机的日期时间以及当前时间后一秒的日期时间。

6.5.2 Calendar类

# 在程序中除了要获取当前计算机的时间外，还会经常设置或修改某个时间，比如一项工程的开始时间为2021年的1月1日，要求100天后竣工。此时要想知道竣工日期是哪天就需要先将日期设定在2021年的1月1日，然后对日期的天数进行增加。如果工程没有按照预期完成，可能还需要对日期时间进行修改。其中添加和修改日期时间的功能就可以通过Calendar类中的add()和set()方法来实现。

6.5.2 Calendar类

# Calendar类中的add()和set()方法可以实现添加和修改日期时间的功能。下面通过案例实现日期时间的添加和修改。具体代码如下所示。

import java.util.*;
public class Example22 {
          public static void main(String[] args) {
	Calendar calendar = Calendar.getInstance();// 获取表示当前时间的Calendar对象
	calendar.set(2021, 1, 1);// 设置指定日期
	calendar.add(Calendar.DATE, 100);// 为指定日期增加时间
	int year = calendar.get(Calendar.YEAR);// 返回指定日期的年
	int month = calendar.get(Calendar.MONTH) + 1;// 返回指定日期的月
	int date = calendar.get(Calendar.DATE);// 返回指定日期的日
	System.out.println("计划竣工日期为:" + year + "年" + month + "月" + date + "日");
         }
}

案例演示

6.5.2 Calendar类

# 运行结果

运行代码，控制台显示的运行结果如下图所示。

注意：Calendar.DATE表示的是天数，当天数累加到当月的最大值时，如果继续累加，Calendar.DATE的天数就会从1开始计数，同时月份值会自动加1，这和算术运算中的进位类似。

6.5.2 Calendar类

# 6.5.3 Instant类

先定一个小目标！

# 6.5.3 Instant类

Instant 类代表的是某个瞬间的时间。其内部由两个部分组成，第一部分保存的是标准Java计算时代（就是1970年1月1日开始）到现在的秒数，第二部分保存的是纳秒数。
Instant类提供了一系列用于操作时间常用的方法，Instant类常用的方法如下表所示。

Instant类的常用方法

| 方法声明 | 功能描述 |
|---|---|
| now() | 从系统时钟获取当前瞬间的时间。 |
| now(Clock clock) | 从指定时钟获取当前时刻。 |

# 6.5.3 Instant类

| 方法声明 | 功能描述 |
|---|---|
| ofEpochSecond(long epochSecond) | 使用从自标准Java计算时代开始的秒数获取一个Instant的实例。 |
| ofEpochMilli(long epochMilli) | 从1970-01-01T00:00:00Z的纪元中使用毫秒获取Instant的实例。 |
| getEpochSecond() | 从1970-01-01T00:00:00Z的Java时代获取秒数。 |
| getNano() | 用于从第二秒开始在此瞬间表示的时间轴中返回纳秒数。 |
| parse(CharSequence text) | 从一个时间文本字符串（如2007-12-03T10:15:30.00Z）获取一个Instant的实例。 |
| from(TemporalAccessor tenporal) | 从时间对象获取一个Instant的实例。 |

# 下面通过一个案例学习Instant类的常用方法的使用。具体代码如下所示。

import java.time.Instant;
public class Example23 {
    public static void main(String[] args) {
        //  Instant 类的时间戳类从1970-01-01 00:00:00 截止到当前时间的毫秒值
        Instant now = Instant.now();
        System.out.println("从系统获取的当前时刻为："+now); 
        Instant instant = Instant.ofEpochMilli(1000 * 60 * 60 * 24);
        System.out.println("计算机元年增加1000 * 60 * 60 * 24毫秒数后为："+instant);
         Instant instant1 = Instant.ofEpochSecond(60 * 60 * 24);
         System.out.println("计算机元年增加60 * 60 * 24秒数后为："+instant1); 
         System.out.println("获取的秒值为："+Instant.parse("2007-12-			03T10:15:30.44Z").getEpochSecond());
         System.out.println("获取的纳秒值为："+Instant.parse("2007-12-03T10:15:30.44Z").getNano());
         System.out.println("从时间对象获取的Instant实例为："+Instant.from(now));
     }
 }

案例演示

6.5.3 Instant类

# 运行结果

运行代码，控制台显示的运行结果如下图所示。

6.5.3 Instant类

# 6.5.4 LocalDate类

先定一个小目标！

# LocalDate类表示不带时区的日期，它所表示的日期包括年份和月份两部分。LocalDate类不能代表时间线上的即时信息，只是描述日期。LocalDate类提供了两个获取日期对象的方法now()和of(int year, int month, int dayOfMonth)，具体如下所示。

//按指定日期创建LocalDate对象
 LocalDate date = LocalDate.of(2020, 12, 12);
//从默认时区的系统时钟获取当前日期
LocalDate now1 = LocalDate.now();

6.5.4 LocalDate类

# LocalDate类还提供了日期格式化、增减年月日等一系列的常用方法。如下所示。

LocalDate类的常用方法

6.5.4 LocalDate类

| 方法声明 | 功能描述 |
|---|---|
| getYear() | 获取年份字段 |
| getMonth() | 使用Month枚举获取月份字段 |
| getMonthValue() | 获取当前日期的月份 |
| getDayOfMonth() | 获取当月第几天字段 |
| format(DateTimeFormatter formatter) | 使用指定的格式化程序格式化此日期 |
| isBefore(ChronoLocalDate other) | 检查此日期是否在指定日期之前 |

# 6.5.4 LocalDate类

| 方法声明 | 功能描述 |
|---|---|
| isAfter(ChronoLocalDate other) | 检查此日期是否在指定日期之后 |
| isEqual(ChronoLocalDate other) | 检查此日期是否等于指定的日期 |
| isLeapYear() | 根据ISO培训日历系统规则，检查年份是否是闰年 |
| parse(CharSequence text) | 从一个文本字获取一个 LocalDate的实例 |
| parse(CharSequence text, DateTimeFormatter formatter) | 使用特定格式格式化 LocalDate从文本字符串获取的 LocalDate实例 |
| plusYears(long yearsToAdd) | 增加指定年份 |
| plusMonths(long monthsToAdd) | 增加指定月份 |

# 6.5.4 LocalDate类

| 方法声明 | 功能描述 |
|---|---|
| plusDays(long daysToAdd) | 增加指定日数 |
| minusYears(long yearsToSubtract) | 减少指定年份 |
| minusMonths(long monthsToSubtract) | 减少指定月份 |
| minusDays(long daysToSubtract) | 减少指定日数 |
| withYear(int year) | 指定年 |
| withMonth(int month) | 指定月 |
| withDayOfYear(int dayOfYear) | 指定日 |

# public static void main(String[] args) {        
        LocalDate now = LocalDate.now();//获取日期时分秒
        LocalDate of = LocalDate.of(2015, 12, 12);
        System.out.println("1. LocalDate的获取及格式化的相关方法--------");
        System.out.println("从LocalDate实例获取的年份为："+now.getYear());
        System.out.println("从LocalDate实例获取的月份为："+now.getMonthValue());
        System.out.println("从LocalDate实例获取当天为本月的第几天："+now.getDayOfMonth());
        System.out.println("将获取到的Loacaldate实例格式化为："+
        	now.format(DateTimeFormatter.ofPattern("yyyy年MM月dd日")));
}

下面通过一个案例学习LocalDate类的一系列常用方法的使用。具体步骤如下所示。

案例演示

步骤一：定义main()方法，调用LocalDate的获取及格式化的相关方法。代码如下所示：

6.5.4 LocalDate类

# System.out.println("2. LocalDate判断的相关方法----------------");
        System.out.println("判断日期of是否在now之前："+of.isBefore(now));
        System.out.println("判断日期of是否在now之后："+of.isAfter(now));
        System.out.println("判断日期of和now是否相等："+now.equals(of));
        System.out.println("判断日期of是否是闰年："+ of.isLeapYear());
        System.out.println("3. LocalDate解析以及加减操作的相关方法---------");
        //给出一个符合默认格式要求的日期字符串
        String dateStr="2020-02-01";
        System.out.println("把日期字符串解析成日期对象后为"+
        LocalDate.parse(dateStr));
        System.out.println("将LocalDate实例年份加1为："+now.plusYears(1));
        System.out.println("将LocalDate实例天数减10为："+now.minusDays(10));
        System.out.println("将LocalDate实例指定年份为2014："+now.withYear(2014));

步骤二：在main()方法中，添加LocalDate判断的相关方法和LocalDate解析以及加减操作的相关方法。代码如下所示：

6.5.4 LocalDate类

# 运行结果

运行代码，控制台显示的运行结果如下图所示。

6.5.4 LocalDate类

# 6.5.5 LocalTime类与LocalDateTime类

先定一个小目标！

# LocalTime类用来表示时间，通常表示的是小时分钟秒。与LocalDate类一样，LocalTime类不能代表时间线上的即时信息，只是时间的描述。LocalTime类中提供了获取时间对象的方法，与LocalDate类用法类似。
此外，LocalTime类也提供了时间格式化、增减时分秒等常用方法，这些方法与LocalDate类的方法用法相同，这里不再详细列举。

1.  LocalTime类

6.5.5 LocalTime类与LocalDateTime类

# import java.time.LocalTime;
import java.time.format.DateTimeFormatter;
public class Example25 {
    public static void main(String[] args) {
        // 获取当前时间，包含毫秒数
        LocalTime time = LocalTime.now();
        LocalTime of = LocalTime.of(9,23,23);
        System.out.println("从LocalTime获取的小时为："+time.getHour());
        System.out.println("将获取到的LoacalTime实例格式化为："+
                time.format(DateTimeFormatter.ofPattern("HH:mm:ss")));
        System.out.println("判断时间of是否在now之前："+of.isBefore(time));
        System.out.println("将时间字符串解析为时间对象后为："+ LocalTime.parse("12:15:30"));
        System.out.println("从LocalTime获取当前时间，不包含毫秒数："+time.withNano(0));
    }
}

下面通过一个案例学习LocalTime类的方法。具体代码如下所示。

案例演示

6.5.5 LocalTime类与LocalDateTime类

# 注意：当我们调用parse()方法解析字符串的时候，该字符串要符合默认的时分秒格式。

运行结果

运行代码，控制台显示的运行结果如下图所示。

6.5.5 LocalTime类与LocalDateTime类

# LocalDateTime类是LocalDate类与LocalTime类的综合，它既包含日期也包含时间，查看Java API可以知道，LocalDateTime类包含了LocalDate类与LocalTime类的所有方法。LocalDateTime类还额外提供了日期时间的转换方法。

2. LocalDateTime类

6.5.5 LocalTime类与LocalDateTime类

# import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;
public class Example26 {
    public static void main(String[] args) {        
        LocalDateTime now = LocalDateTime.now();//获取系统当前年月日，时分秒
        System.out.println("获取的当前日期时间为："+now);
        System.out.println("将目标LocalDateTime转换为相应的LocalDate实例:"+ now.toLocalDate());
        System.out.println("将目标LocalDateTime转换为相应的LocalTime实例:"+ now.toLocalTime());
        //指定格式
        DateTimeFormatter ofPattern = DateTimeFormatter.ofPattern
       ("yyyy年MM月dd日 HH时mm分ss秒");
        System.out.println("格式化后的日期时间为："+now.format(ofPattern));
    }
}

下面通过一个案例学习LocalDateTime类的日期时间转换方法。具体代码如下所示。

案例演示

6.5.5 LocalTime类与LocalDateTime类

# 运行结果

运行代码，控制台显示的运行结果如下图所示。

6.5.5 LocalTime类与LocalDateTime类

# 6.5.6 Duration类与Period类

先定一个小目标！

# Duration类表示两个时间之间的间隔，间隔时间的单位可以是天、时、分、秒、毫秒和纳秒，例如今天的12:00:00与13:00:00之间，间隔1小时，或者60分钟，或者3600秒。Duration类的常用方法如下表所示。

1.  Duration类

6.5.6 Duration类与Period类

# Duration类的常用方法

6.5.6 Duration类与Period类

| 方法声明 | 功能描述 |
|---|---|
| between(Temporal startInclusive, Temporal endExclusive) | 获取一个Duration实例，表示两个时间对象之间的持续时间 |
| toDays() | 将间隔时间转换为以天为单位 |
| toHours() | 将间隔时间转换为以时为单位 |
| toMinutes() | 将间隔时间转换为以分钟为单位 |
| toMillis() | 将间隔时间转换为以毫秒为单位 |
| toNanos() | 将间隔时间转换为以纳秒为单位 |

# 下面通过一个案例讲解Duration类中常用方法的使用。具体代码如下所示。

import java.time.Duration;
import java.time.LocalTime;
public class Example27{
        public static void main(String[] args) {
             LocalTime start = LocalTime.now();
             LocalTime end = LocalTime.of(20,13,23);
             Duration duration = Duration.between(start, end);
             //间隔的时间
             System.out.println("时间间隔为："+duration.toNanos()+"纳秒");
             System.out.println("时间间隔为："+duration.toMillis()+"毫秒");
             System.out.println("时间间隔为："+duration.toHours()+"小时");
        }
}

案例演示

6.5.6 Duration类与Period类

# 运行结果

运行代码，控制台显示的运行结果如下图所示。

6.5.6 Duration类与Period类

# Period类主要用于计算两个日期的间隔，与Duration类相同，Period类也是通过between()方法计算日期间隔，并提供了获取年月日的三个常用方法，分别是 getYears()、getMonths()和getDays()。

2.  Period类

6.5.6 Duration类与Period类

# import java.time.LocalDate;
import java.time.Period;
public class Example28 {
    public static void main(String[] args) {
        LocalDate birthday = LocalDate.of(2018, 12, 12);
        LocalDate now = LocalDate.now();
        //计算两个日期的间隔
        Period between = Period.between(birthday, now);
        System.out.println("时间间隔为"+between.getYears()+"年");
        System.out.println("时间间隔为"+between.getMonths()+"月");
        System.out.println("时间间隔为"+between.getDays()+"天");
    }
}

下面通过一个案例学习getYears()、getMonths()和getDays()的使用。具体代码如下所示。

案例演示

6.5.6 Duration类与Period类

# 运行结果

运行代码，控制台显示的运行结果如下图所示。

6.5.6 Duration类与Period类

# 日期与时间格式化类

6.6

# 6.6.1 DateFormat类

先定一个小目标！

# 6.6.1 DateFormat类

尽管使用java.util.Date类能够获取日期和时间，但是因为其显示格式与日常使用的日期格式不同，因此，Java提供了DateFormat类，DateFormat类可以将日期时间进行格式化，使日期时间的格式符合人们的阅读习惯。DateFormat是一个抽象类，不能被直接实例化，但它提供了一系列用于获取DateFormat类实例的静态方法，并能调用其他相应的方法进行操作。

# 6.6.1 DateFormat类

DateFormat类的常用方法

| 方法声明 | 功能描述 |
|---|---|
| static DateFormat getDateInstance() | 用于创建默认语言环境和格式化风格的日期格式器 |
| static DateFormat getDateInstance(int style) | 用于创建默认语言环境和指定格式化风格的日期格式器 |
| static DateFormat getDateTimeInstance() | 用于创建默认语言环境和格式化风格的日期/时间格式器 |
| static DateFormat getDateTimeInstance(int dateStyle,int timeStyle) | 用于创建默认语言环境和指定格式化风格的日期/时间格式器 |
| String format(Date date) | 将一个 Date 格式化为日期/时间字符串 |
| Date parse(String source) | 将给定字符串解析成一个日期 |

# 6.6.1 DateFormat类

除了DateFormat类的6个常用方法外，DateFormat类还定义了许多常量，其中有4个常量值可以作为参数传递给DateFormat类的方法，表示不同格式的日期时间。这4个常量具体如下。

l FULL：用于表示完整格式的日期时间。
l LONG：用于表示长格式的日期时间。
l MEDIUM：用于表示普通格式的日期时间。
l SHORT：用于表示短格式的日期时间。

# 6.6.1 DateFormat类

public static void main(String[] args) { 	
        Date date = new Date();// 创建Date对象
        // Full格式的日期格式器对象
        DateFormat fullFormat = DateFormat.getDateInstance(DateFormat.FULL);
        // LONG格式的日期格式器对象
        DateFormat longFormat = DateFormat.getDateInstance(DateFormat.LONG);
        // MEDIUM格式的日期/时间 格式器对象
        DateFormat mediumFormat = DateFormat.getDateTimeInstance(
 		DateFormat.MEDIUM, DateFormat.MEDIUM);
        // SHORT格式的日期/时间格式器对象
        DateFormat shortFormat = DateFormat.getDateTimeInstance(
 			DateFormat.SHORT, DateFormat.SHORT);
        System.out.println("当前日期的完整格式为：" + fullFormat.format(date));
        System.out.println("当前日期的长格式为：" + longFormat.format(date));
        System.out.println("当前日期的普通格式为：" + mediumFormat.format(date));
        System.out.println("当前日期的短格式为：" + shortFormat.format(date));
}

案例演示

下面通过一个案例演示DateFormat类的使用。具体代码如下所示。

# 6.6.1 DateFormat类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 6.6.1 DateFormat类

import java.text.*;
public class Example30 {
       public static void main(String[] args) throws ParseException {
        	// 创建LONG格式的DateFormat对象
        	DateFormat dt = DateFormat.getDateInstance(DateFormat.LONG);
        	// 定义日期格式的字符串
        	String str = "2021年05月20日";
        	// 输出对应格式的字符串解析成Date对象后的结果
        	System.out.println(dt1.parse(str));
      }
}

案例演示

DateFormat类还提供了一个parse()方法，该方法能将一个字符串解析成Date对象，但是parse()方法要求字符串必须符合日期/时间的格式要求，否则会抛出异常。通过案例演示parse()方法的使用。具体代码如下所示。

# 6.6.1 DateFormat类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 6.6.2 SimpleDateFormat类

先定一个小目标！

# 6.6.2 SimpleDateFormat类

为了能够更好地格式化日期、解析字符串，Java提供了一个SimpleDateFormat类。
SimpleDateFormat类是DateFormat类的子类，它可以使用new关键字创建实例对象。在创建实例对象时，SimpleDateFormat类的构造方法需要接收一个表示日期格式模板的字符串参数，日期格式模板通过特定的日期标记可以将一个日期格式的日期数字提取出来。

# 6.6.2 SimpleDateFormat类

日期格式化模板标记

| 标记 | 功能描述 |
|---|---|
| y | 年，年份是4位数字，使用yyyy表示 |
| M | 月份，月份是两位数字，使用MM表示 |
| d | 天，天数是两位数字，使用dd表示 |
| H | 小时（24小时），小时是两位数字，使用HH表示 |
| m | 分钟，分钟是两位数字，使用mm表示 |
| s | 秒，秒是两位数字，使用ss表示 |
| S | 毫秒，毫秒是3位数字，使用SSS表示 |

# 6.6.2 SimpleDateFormat类

除了日期格式化模板标记，SimpleDateFormat类还提供了一系列的方法用于实现日期格式化，如下所示。

SimpleDateFormat类常用的方法

| 标记 | 功能描述 |
|---|---|
| SimpleDateFormat(String pattern) | 通过一个指定的模板构造对象 |
| Date parse(String source) throws ParseException | 将一个包含日期的字符串变为Date类型 |
| String format(Date date) | 将一个Date类型对象按照指定格式变为String类型 |

# 6.6.2 SimpleDateFormat类

下面通过一个案例演示如何使用SimpleDateFormat类将日期对象转为特定格式的字符串，具体代码如下所示。

import java.text.*;
 import java.util.*;
 public class Example31 {
      public static void main(String[] args) throws Exception {
 	// 创建一个SimpleDateFormat对象
 	SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日"); 
 	// 按SimpleDateFormat对象的日期模板格式化Date对象
 	System.out.println(sdf.format(new Date()));
      }
 }

案例演示

# 6.6.2 SimpleDateFormat类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 6.6.2 SimpleDateFormat类

import java.text.*;
 import java.util.*;
 public class Example32 {
     public static void main(String[] args) throws Exception {
         String strDate = "2021-03-02 17:26:11.234";    //定义日期时间的字符串
         String pat = "yyyy-MM-dd HH:mm:ss.SSS";         //定义日期时间的模板
         // 创建一个SimpleDateFormat对象
         SimpleDateFormat sdf = new SimpleDateFormat(pat);
         // 按SimpleDateFormat对象的日期模板将字符串格式化为Date对象
         Date d = sdf.parse(strDate);
         System.out.println(d);
     }
 }

下面通过一个案例演示如何使用SimpleDateFormat类将日期对象转为特定格式的字符串，具体代码如下所示。

案例演示

# 6.6.2 SimpleDateFormat类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 数字格式化类

6.7

# 6.7 数字格式化类

Java提供了NumberFormat类，定义在java.text包中。NumberFormat类可以格式化和解析任何区域设置的数字，使数字的格式符合人们的阅读习惯。NumberFormat类是一个抽象类，不能被直接实例化，但是它提供了一系列用于获取NumberFormat类实例的静态方法，并能调用其他相应的方法进行操作。

# NumberFormat类的常用方法

6.7 数字格式化类

| 方法声明 | 功能描述 |
|---|---|
| static NumberFormatgetCurrencyInstance() | 返回当前默认FORMAT语言环境的货币格式 |
| static NumberFormatgetCurrencyInstance(Locale i) | 返回指定语言环境的货币格式 |
| static NumberFormat getInstance() | 返回当前默认FORMAT语言环境的通用数字格式 |
| static NumberFormatgetInstance(Locale i) | 返回指定语言环境的通用数字格式 |
| String format(double number) | 将给定的double类型的数值格式化为数值字符串 |
| String format(long number) | 将给定的long类型的数值格式化为数值字符串 |
| Number parse(String source) | 将给定的字符串解析，生成对应的数值 |

# 包装类

6.8

# Java程序设计提倡一种思想，即万物皆对象。这样就出现一个矛盾，因为Java中的数据类型分为基本数据类型和引用数据类型，很多类的方法都需要接收引用类型的对象，此时就无法将一个基本数据类型的值传入。为了解决这样的问题，就需要将基本数据类型值进行包装，即将基本数据类型值包装为引用数据类型的对象。能够将基本数据类型值包装为引用数据类型对象的类，称为包装类。JDK提供了一系列包装类，通过这些包装类可以将基本数据类型的值包装为引用数据类型的对象。

6.8 包装类

# 6.8 包装类

Java中的基本数据类型对应的包装类

| 基本数据类型 | 对应的包装类 |
|---|---|
| byte | Byte |
| char | Character |
| int | Integer |
| short | Short |
| long | Long |
| float | Float |
| double | Double |
| boolean | Boolean |

# 6.8 包装类

除了Character和Boolean是Object的直接子类外，Integer、Byte、Float、Double、Short、Long都属于Number类的子类。Number类是一个抽象类，其本身提供了一系列的返回以上6种基本数据类型的方法，Number类的方法主要是将数字包装类中的内容变为基本数据类型。

# 6.8 包装类

将一个基本数据类型转变为包装类的过程，称为装箱操作，反之，将一个包装类转变为基本数据类型的过程称为拆箱操作。

Java中的基本数据类型对应的包装类

| 方法 | 方法描述 |
|---|---|
| byte byteValue() | 以byte形式返回指定的数值 |
| abstract double doubleValue() | 以double形式返回指定的数值 |
| abstract float floatValue() | 以float形式返回指定的数值 |
| abstract int intValue() | 以int形式返回指定的数值 |
| abstract long longValue() | 以long形式返回指定的数值 |
| short shortValue() | 以short形式返回指定的数值 |

# 6.8 包装类

下面以int类型的包装类Integer为例，通过一个案例演示装箱与拆箱的过程，具体代码如下所示。

public class Example33 {
     public static void main(String args[]) {
         int a = 20;                      //声明一个基本数据类型
         Integer in = new Integer(a);  //装箱：将基本数据类型变为包装类
         System.out.println(in);
         int temp = in.intValue();   //拆箱：将一个包装类变为基本数据类型
         System.out.println(temp);
     }
 }

案例演示

# 6.8 包装类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 6.8 包装类

其中的intValue()方法可以将Integer类型的值转为int类型，这个方法可以用来进行手动拆箱操作。parseInt(String s)方法可以将一个字符串形式的数值转成int类型，valueOf(int i)可以返回指定的int值为Integer实例。

Integer类特有的方法

| 方法 | 功能描述 |
|---|---|
| Integer valueOf(int i) | 返回一个表示指定的int值的 Integer 实例 |
| Integer valueOf(String s) | 返回保存指定的String的值的 Integer 对象 |
| int parseInt(String s) | 将字符串参数作为有符号的十进制整数进行解析 |
| int intValue() | 将 Integer 类型的值以int类型返回 |

# 6.8 包装类

public class Example34 {
     public static void main(String args[]) {
         Integer num = new Integer(20);     //手动装箱
         int sum = num.intValue() + 10;     //手动拆箱
         System.out.println("将Integer类值转化为int类型后与10求和为："+ sum);
         System.out.println("返回表示10的Integer实例为：" + Integer.valueOf(10));
         int w = Integer.parseInt("20")+32;
         System.out.println("将字符串转化为整数位：" + w);
     }
 }

下面通过一个案例演示Integer类的常用方法的使用，具体代码如下所示。

案例演示

# 6.8 包装类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 脚下留心

使用包装类时的注意事项

使用包装类时，需要注意以下几点。

（1）包装类都重写了Object类中的toString()方法，以字符串的形式返回被包装的基本数据类型的值。

# 脚下留心

使用包装类时的注意事项

（2）除了Character外，包装类都有valueOf(String s)方法，可以根据String类型的参数创建包装类对象，但参数字符串s不能为null，而且字符串必须是可以解析为相应基本类型的数据，否则虽然编译通过，但运行时会报错。具体示例如下。

Integer i = Integer.valueOf("123");  // 合法
Integer i = Integer.valueOf("12a");   // 不合法，12a不能被正确解析为基本类型数据

# 脚下留心

使用包装类时的注意事项

（3）除了Character外，包装类都有parseXxx(String s)的静态方法，该方法的作用是将字符串转换为对应的基本类型的数据。参数s不能为null，而且同样字符串必须可以解析为相应基本类型的数据，否则虽然编译通过，但运行时会报错。具体示例如下。

int i = Integer.parseInt("123");           // 合法    
Integer in = Integer.parseInt("itcast"); // 不合法

# 正则表达式

6.9

# 在实际开发中，经常需要对用户输入的信息进行格式校验。例如，判断输入的字符串是否符合Email格式。若手工编写代码实现校验逻辑，不仅耗时，而且健壮性也往往得不到保证。为此，Java提供了正则表达式，通过正则表达式可以快速校验信息格式。本节将针对正则表达式进行详细地讲解。

6.9 正则表达式

# 6.9.1 正则表达式语法

先定一个小目标！

# 6.9.1 正则表达式语法

正则表达式是由普通字符（如字符a~z）和特殊字符（元字符）组成的文本模式，例如，正则表达式“[a-z]*”描述了所有仅包含小写字母的字符串，其中a、z为普通字符，短横线、左右中括号及星号则为元字符。

正则表达式

# 6.9.1 正则表达式语法

点号可以匹配除“\n”之外的任何单个字符。

例如，正则表达式“t.n”可匹配“tan”“ten”“tcn”“t=n”“t n”（t和n之间有一个空格）等。

1. 点号

# 6.9.1 正则表达式语法

中括号可以匹配中括号内所有字符中的任意一个。可以在中括号内指定需要匹配的若干字符，表示仅使用这些字符参与匹配。

例如，正则表达式“t[abcd]n”只匹配“tan”“tbn”“tcn”“tdn”。中括号还有一些特殊写法，用于匹配某一范围内的字符，例如“[a-z]”匹配一个小写字母，“[a-zA-Z]”匹配一个字母、“[0-9]”匹配一个数字字符、“[a-z0-9]”匹配一个小写字母或一个数字字符等。

2. 中括号

# 6.9.1 正则表达式语法

“|”符号可以匹配其左侧或右侧的符号。

例如，正则表达式“t（a|e|i|io）n”，除了“tan”“ten”和“tin”外，还可以匹配“tion”。使用“|”符号时，必须使用圆括号将可以匹配的字符括起来，圆括号用来标记正则表达式中的组（Group）。

3.“|”符号

# 6.9.1 正则表达式语法

“^”符号可以匹配一行的开始。

例如，正则表达式“^Spring.*”匹配“Spring MVC”，而不匹配“a Spring MVC”。若“^”符号在中括号内，则表示不需要参与匹配的字符。例如，正则表达式“[a-z&&[^bc]]”表示，可以匹配除b和c之外的小写字母，等价于“[ad-z]”，正则表达式“[a-z&&[^h-n]]”表示除h到n之外的小写字母，等价于“[a-go-z]”，正则表达式“[^b][a-z]+”表示首个字符不能是b且后跟至少一个小写字母。

4.“^”符号

# 6.9.1 正则表达式语法

“$”符号可以匹配一行的结束。

例如，正则表达式“.*App$”中的“$”符号表示匹配以App结尾的字符串，可以匹配“Andriod App”，而不匹配“iOS Apps”和“App.”。

5.“%”符号

# 6.9.1 正则表达式语法

“\”符号表示其后的字符是普通字符而非元字符。

例如，正则表达式“\$”用来匹配“$”字符而非结束，“\.”用来匹配“.”字符而非任一字符。

6.“\”符号

# 6.9.1 正则表达式语法

匹配次数元字符用来确定其左侧符号的出现次数，常用的匹配次数元字符如下表所示。

7. 匹配次数元字符

| 元字符 | 含义 |
|---|---|
| X* | 匹配X出现零次或多次，如Y，YXXXY |
| X+ | 匹配X出现一次或多次，如YXY，YXX |
| X? | 匹配X出现零次或一次，如Y，YXY |
| X{n} | 匹配X出现恰好n次 |
| X{n,} | 匹配X出现至少出现n次 |
| X{n,m} | n<=m，匹配X出现至少n次，最多m次 |

# 6.9.1 正则表达式语法

除了上述7种元字符外，正则表达式还有一些其他常用元字符，具体如下表所示。

8. 其他常用符号

| 元字符 | 含义 |
|---|---|
| \d | 数字：[0-9] |
| \D | 非数字： [^0-9] |
| \s | 空白字符：[ \t\n\x0B\f\r] |
| \S | 非空白字符：[^\s] |
| \w | 单词字符：[a-zA-Z_0-9] |
| \b | 单词边界 |
| \B | 非单词边界 |
| \A | 输入的开头 |
| \G | 上一个匹配的结尾 |

# 6.9.2 Pattern类和Matcher类

先定一个小目标！

# 6.9.2 Pattern类和Matcher类

Pattern类用于创建一个正则表达式，也可以说创建一个匹配模式。Pattern类的构造方法是私有的，不可以直接创建正则表达式，为此，Pattern类提供了一个静态的complie()方法，通过调用complie()方法可以创建一个正则表达式，具体代码如下所示。

1. Pattern类

Pattern p = Pattern.compile("\\w+");

# 6.9.2 Pattern类和Matcher类

Pattern类常用方法

除了complie()方法，Pattern类还提供了其他的方法，其中常用方法如下表所示。

| 方法声明 | 功能描述 |
|---|---|
| static Pattern compile(String re) | 将正则表达式编译为模式 |
| Matcher matcher(CharSequence input) | 根据模式为字符串input创建匹配器。String类实现了CharSequence接口，CharSequence接口可视为String |
| Static boolean matches(String regex, 
                CharSequence input) | 判断字符串input是否匹配正则表达式regex。该方法适合于只进行一次匹配情况 |
| String pattern() | 返回模式使用的正则表达式 |
| String[] split(CharSequence input) | 根据模式将字符串input分割为字符串数组 |
| String[] split(CharSequence input,int limit) | 根据模式将字符串input分割为字符串数组，同时指定了子串的最大个数为limit |

# 6.9.2 Pattern类和Matcher类

import java.util.regex.Matcher;
import java.util.regex.Pattern;
public class Example35 {
    public static void main(String[] args) {
        Pattern p1 = Pattern.compile("a*b");   //根据参数指定的正则表达式创建模式
        Matcher m1 = p1.matcher("aaaaab");    //获取目标字符串的匹配器
        Matcher m2 = p1.matcher("aaabbb");    //获取目标字符串的匹配器
        System.out.println(m1.matches());     //执行匹配器
        System.out.println(m2.matches());     //执行匹配器
        Pattern p2 = Pattern.compile("[/]+");
        String[] str = p2.split("张三//李四/王五//赵六/钱七"); //按模式分割字符串
        for(String s : str){
            System.out.print(s+"\t");
        }
    }
}

案例演示

通过一个案例学习Pattern类常用方法的使用，具体代码如下所示。

# 6.9.2 Pattern类和Matcher类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 6.9.2 Pattern类和Matcher类

Matcher类用于验证Pattern定义的模式与字符串是否匹配，因此Matcher实例也称为匹配器。Matcher类的构造方法也是私有的，不能直接创建Macher实例，只能通过Pattern.matcher()方法获取该类的实例，多个Matcher对象可以使用同一Pattern对象。

2. Matcher类

# 6.9.2 Pattern类和Matcher类

Matcher类常用方法

Matcher类的常用方法如下表所示。

| 方法声明 | 功能描述 |
|---|---|
| Pattern pattern() | 返回匹配器的模式 |
| Matcher usePattern(Pattern p) | 返回匹配器的模式为p |
| Matcher reset() | 重设匹配器到初始状态 |
| Matcher reset(CharSequence input) | 重设匹配器到初始状态，并使用input为目标字符串 |
| Boolean find() | 在目标字符串中查找下一个匹配字符串，找到返回true |
| int start() | 正则表达式所匹配的字符串在整个字符串中第一次出现的索引 |

# 6.9.2 Pattern类和Matcher类

| 方法声明 | 功能描述 |
|---|---|
| int end() | 正则表达式所匹配的字符串在整个字符串中最后一次出现的索引 |
| String group() | 返回匹配到的子字符串 |
| String group(int i) | 返回上一次匹配的子串中与第i个组相匹配的那个子串。正则表达式中以一对圆括号括起来的部分称为组 |
| boolean matcher() | 对整个字符串进行匹配，只有整个字符串都匹配了才返回true |
| boolean lookingAt() | 从目标字符串的第一个字符开始匹配，有匹配成功的返回true，否则返回false |
| String replaceAll(String s) | 将目标字符串中与模式相匹配的全部子串替换为s并返回替换后的字符串 |
| String replaceFirst(String s) | 将目标字符串中与模式相匹配的首个子串替换为s并返回替换后的字符串 |

# 6.9.2 Pattern类和Matcher类

案例演示

下面通过一个案例学习Matcher类常用方法的使用，具体步骤如下所示。

public static void main(String[] args) {
         Pattern p=Pattern.compile("\\d+");
         Matcher m=p.matcher("22bb23");
         System.out.println("字符串是否匹配:"+ m.matches());  
         Matcher m2=p.matcher("2223");
         System.out.println("字符串2223与模式p是否匹配:"+ m2.matches());
         System.out.println("字符串22bb23与模式p的匹配结果:"+ m.lookingAt());
         Matcher m3=p.matcher("aa2223");
         System.out.println("字符串22bb23与模式p的匹配结果:"+m3.lookingAt());
         System.out.println("字符串22bb23与模式p是否存在下一个匹配结果:m.find());
         m3.find();//返回true
         System.out.println("字符串aa2223与模式p是否存在在下一个匹配结果m3.find());
}

步骤一：定义main()方法。代码如下所示：

# 6.9.2 Pattern类和Matcher类

Matcher m4=p.matcher("aabb");
System.out.println("字符串aabb与模式p是否存在下一个匹配结果："+ m4.find());
Matcher m1=p.matcher("aaa2223bb");
m1.find();//匹配2223
System.out.println("模式p与字符串aaa2223bb的匹配的起始索引:"+  m1.start());
System.out.println("模式p与字符串aaa2223bb的最后一个字符匹配后的偏移量"+  m1.end());
System.out.println("模式p与字符串aaa2223bb的匹配到的子字符串:"+  m1.group());
Pattern p2 = Pattern.compile("[/]+");
Matcher m5 = p2.matcher("张三/李四//王五///赵六");
System.out.println("将字符串张三/李四//王五///赵六中的/全部替换为|:"+ m5.replaceAll("|"));
System.out.println("将字符串张三/李四//王五///赵六中的首个/替换为|:"+ m5.replaceFirst("|"));

步骤二：在main()方法中添加Matcher类的其他常用方法。代码如下所示：

# 6.9.2 Pattern类和Matcher类

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 6.9.3 String类对正则表达式的支持

先定一个小目标！

# 6.9.3 String类对正则表达式的支持

String类提供了3个支持正则表达式操作的方法，如下表所示。

| 方法声明 | 功能描述 |
|---|---|
| boolean matches(String regex) | 匹配字符串regex |
| String replaceAll(String regex, String replacement) | 使用字符串replacement替换regex |
| String[] split(String regex) | 拆分字符串 |

# 6.9.3 String类对正则表达式的支持

public class Example37{
     public static void main(String[] args) {
         String str = "A1B22DDS34DSJ9D".replaceAll("\\d+","_");
         System.out.println("字符串替换后为："+str);
         boolean te = "321123as1".matches("\\d+");
         System.out.println("字符串是否匹配："+te);
         String[] s="SDS45d4DD4dDS88D".split("\\d+");
         System.out.print("字符串拆分后为：");
         for(int i=0;i<s.length;i++){
             System.out.print(s[i]+"  ");
         }
     }
 }

案例演示

下面通过一个案例演示String类支持正则表达式操作的方法的使用，具体代码如下所示。

# 6.9.3 String类对正则表达式的支持

运行结果

运行代码，控制台显示的运行结果如下图所示。

注意：String类matches(String regex)方法的调用同Pattern类和Matcher类中该方法调用一样，必须匹配所有的字符串才返回true，否则返回false。

# 本章小结

本章详细介绍了Java API的基础知识。首先从String类、StringBuffer类的使用上介绍了字符串类，然后介绍了String类、StringBuffer类和StringBuilder类的区别；其次介绍了System类和Runtime类的使用；接下来介绍了Math类、Random类和BigInteger类的使用；然后详细介绍了日期时间类，包括Date类、Calendar类、Instant类、LocalDate类、LocalTime类、Period类和Duration类以及日期格式化类DateFormat类和SimpleDateformat类；紧接着介绍了基本类型所对应的包装类；最后介绍了正则表达式，从正则表达式语法、Pattern类、Matcher类和String类对正则表达式的支持等方面对正则表达式的使用进行了详解介绍。熟练掌握Java中的常用 API，对以后的实际开发大有裨益。

本

章

小

结
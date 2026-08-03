# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# 子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。

模块一  任务描述

子任务1： 获取字符串长度及访问字符串中的第一个字符。
子任务2： 字符串转换为大写。
子任务3： 字符串“HelloWorld”中的“World”替换为“Java”。
子任务4： 判断字符串是否以“Str”开头。
子任务5： 将字符串“本科-硕士-博士”先截取出“硕士”，后分割           					字符串。
子任务6： 使用StringBuffer实现字符串的添加、删除、修改和截取。

# ..

模块二 知识链接

String类

StringBuffer类

# String类

模块二 
知识链接

Java定义了两种初始化String对象的方式。
第一种方式：使用字符串常量直接初始化一个String对象，语法格式：  									String 变量名=字符串；
示例代码如下：
String str1=null;          //将字符串str1设置为空
String str2=“”;         //将字符串str2设置为空字符串
String str3=“hello”;     //将字符串str3设置为“hello”

# String类

模块二 
知识链接

第二种方式：调用String类构造方法初始化字符串对象，其语法格式：
 String 变量名=new String(字符串)；  							
String类的常见构造方法如下：

| 方法声明 | 功能描述 |
|---|---|
| String() | 创建一个内容为空的字符串 |
| String(String value) | String(String value) |
| String(char[] value) | 根据指定的字符数组value创建对象 |
| String(byte[] bytes) | 根据指定的字节数组bytes创建对象 |

# String类

模块二 
知识链接

| 方法声明 | 功能描述 |
|---|---|
| int length() | 返回当前字符串的长度，即字符串中字符的个数。 |
| int indexOf(int ch) | 返回指定字符ch在字符串中第一次出现位置的索引。 |
| int lastIndexOf(int ch) | 返回指定字符ch在字符串中最后一次出现位置的索引。 |
| int indexOf(String str) | 返回指定子字符串str在字符串第一次出现位置的索引。 |
| int lastIndexOf(String str) | 返回指定子字符串str在此字符串中最后一次出现位置的索引。 |
| char charAt(int index) | 返回字符串中index位置上的字符，其中index的取值范围是0~(字符串长度-1)。 |
| boolean endsWith(String suffix) | 判断此字符串是否以指定的字符串结尾。 |

# String类

模块二 
知识链接

| 方法声明 | 功能描述 |
|---|---|
| boolean equals(Object obj) | 比较obj与当前字符串对象的内容是否相同。 |
| boolean equalsIgnoreCase(String str) | 以忽略大小写的方式比较str与当前字符串对象的内容是否相同。 |
| int compareTo(String str) | 按对应字符的Unicode编码比较str与当前字符串对象的大小。若当前字符串对象比str大，返回正整数；若比str小，返回负整数；若相等则返回0。 |
| int compareToIgnoreCase(String str) | 按对应字符的Unicode编码以忽略大小写的方式比较str与当前字符串对象的大小。若当前字符串对象比str大，返回正整数；若比str小，返回负整数；若相等则返回0。 |
| boolean isEmpty() | 判断字符串长度是否为0，如果为0则返回true，反之则返回flase。 |
| boolean startsWith(String prefix) | 判断此字符串是否以指定的字符串prefix开始。 |

# String类

模块二 
知识链接

| 方法声明 | 功能描述 |
|---|---|
| boolean contains(CharSequence cs) | 判断此字符串中是否包含指定的字符序列cs。 |
| String toLowerCase() | 使用默认语言环境的规则将String中的所有字符都转换为小写。 |
| String toUpperCase() | 使用默认语言环境的规则将String中的所有字符都转换为大写。 |
| static String valueOf(int i) | 将int变量i转换成字符串。 |
| char[] toCharArray() | 将此字符串转换为一个字符数组。 |
| String replace(CharSequence oldstr, CharSequence newstr) | 使用newstr替换原字符串中的oldstr，返回一个新的字符串。 |
| String concat(String str) | 将str连接到当前字符串对象之后。 |

# String类

模块二 
知识链接

| 方法声明 | 功能描述 |
|---|---|
| String[] split(String regex) | 根据参数regex将原来的字符串分割为若干个子字符串。 |
| String substring(int beginIndex) | 返回一个新字符串，它包含从指定的beginIndex处开始，直到此字符串末尾的所有字符。 |
| String substring(int beginIndex, int endIndex) | 返回一个新字符串，它包含从指定的beginIndex处开始，直到索引endIndex-1处的所有字符。 |
| String trim() | 去除了原字符串首尾的空格。 |

# StringBuffer类

模块二 
知识链接

StringBuffer类和String类最大的区别在于它的内容和长度都是可以改变的。StringBuffer类就像一个字符容器，当在其中添加或者删除字符时，操作的都是这个字符容器，因此并不会产生新的StringBuffer对象。

# StringBuffer类

模块二 
知识链接

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

# StringBuffer类

模块二 
知识链接

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

# ，

过渡页

模块三  任务实现

模块三 
任务实现

子任务1： 获取字符串长度及访问字符串中的第一个字符。
子任务2： 字符串转换为大写。
子任务3： 字符串“HelloWorld”中的“World”替换为“Java”。
子任务4： 判断字符串是否以“Str”开头。
子任务5： 将字符串“本科-硕士-博士”先截取出“硕士”，后分割           					字符串。
子任务6： 使用StringBuffer实现字符串的添加、删除、修改和截取。

# 子任务1-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

public class Example01 {
    public static void main(String[] args) {
        String s = "ababcdedcba"; // 定义字符串s
        // 获取字符串长度，即字符个数
        System.out.println("字符串的长度为：" + s.length());
        System.out.println("字符串中第一个字符:" + s.charAt(0));
}
}

# 子任务1-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 子任务2-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

public class Example02 {
    public static void main(String[] args) {
        String str = "abcd";
 		System.out.println("将字符串转换成大写之后的结果:" +
                str.toUpperCase());
}
}

# 子任务2-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 子任务3-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

public class Example03 {
    public static void main(String[] args) {
        String s = "HelloWorld";
        // 字符串替换操作
        System.out.println("将World替换成Java的结果:" + s.replace("World",
                "Java"));
		}
}

# 子任务3-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 子任务4-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

public class Example04 {
    public static void main(String[] args) {
        String s1 = "String"; // 定义一个字符串
        String s2 = "string";
        System.out.println("判断s1字符串对象是否以Str开头:" +s1.startsWith("Str"));
        System.out.println("判断s2字符串对象是否以Str开头:" +s2.startsWith("Str"));
	}
}

# 子任务4-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 子任务5-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

public class Example05 {
    public static void main(String[] args) {
        String str = "本科-硕士-博士";
        // 下面是字符串截取操作
        System.out.println("从第4个字符截取到第5个字符的结果：" +
                str.substring(3, 5));
        // 下面是字符串分割操作
        System.out.print("分割后的字符串数组中的元素依次为:");

# 子任务5-代码实现

模块三 
任务实现

String[] strArray = str.split("-"); // 将字符串转换为字符串数组
        for (int i = 0; i < strArray.length; i++) {
            if (i != strArray.length - 1) {
                // 如果不是数组的最后一个元素,在元素后面加逗号
                System.out.print(strArray[i] + ",");
            } else {
                // 数组的最后一个元素后面不加逗号
                System.out.println(strArray[i]);
            }  }  }  }

# 子任务5-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 子任务6-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

public static void main(String[] args) {
        System.out.println("1.添加------------------------");
        add();
        System.out.println("2.删除------------------------");
        remove();
        System.out.println("3.修改------------------------");
        alter();
        System.out.println("4.截取------------------------");
        sub(); }

# 子任务6-代码实现

模块三 
任务实现

public static void add() {
        StringBuffer sb = new StringBuffer();           // 定义一个字符串缓冲区
        sb.append("abcdefg"); 				            // 在末尾添加字符串
        sb.append("hij").append("klmn"); 	            // 连续调用append()方法添加字符串
        System.out.println("append添加结果：" + sb);
        sb.insert(2, "123"); 				// 在指定位置插入字符串
        System.out.println("insert添加结果：" + sb);
    }

# 子任务6-代码实现

模块三 
任务实现

public static void remove() {
        StringBuffer sb = new StringBuffer("abcdefg");
        sb.delete(1, 5);    		 			// 指定范围删除
        System.out.println("删除指定位置结果：" + sb);
        sb.deleteCharAt(2); 				    // 指定位置删除
        System.out.println("删除指定位置结果：" + sb);
        sb.delete(0, sb.length()); 			    // 清空字符串缓冲区
        System.out.println("清空缓冲区结果：" + sb);
    }

# 子任务6-代码实现

模块三 
任务实现

public static void alter() {
        StringBuffer sb = new StringBuffer("abcdef");
        sb.setCharAt(1, 'p');    			    // 修改指定位置字符
        System.out.println("修改指定位置字符结果：" + sb);
        sb.replace(1, 3, "qq"); 			// 替换指定位置字符串或字符
        System.out.println("替换指定位置字符（串）结果：" + sb);
        System.out.println("字符串翻转结果：" + sb.reverse());
    }

# 子任务6-代码实现

模块三 
任务实现

public static void sub() {
        StringBuffer sb = new StringBuffer();   // 定义一个字符串缓冲区
        System.out.println("获取sb的初始容量：" + sb.capacity());
        sb.append("hello123"); 			    // 在末尾添加字符串
        System.out.println("append添加结果：" + sb);
        System.out.println("截取第6~8个字符：" + sb.substring(5,8));
    }
}

# 子任务6-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 感谢关注
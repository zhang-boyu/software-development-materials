
## 第1页幻灯片
无锡职业技术学院内部资料
JAVA程序设计项目教程

## 第2页幻灯片
*
任务描述
知识链接
任务实现
目录

## 第3页幻灯片
子任务2：在子任务1的基础上，定义子类Cat的属性color以及设置和获取方法；定义测试类输出Cat实例相关属性信息。
*
模块一  任务描述
子任务1： 获取字符串长度及访问字符串中的第一个字符。
子任务2： 字符串转换为大写。
子任务3： 字符串“HelloWorld”中的“World”替换为“Java”。
子任务4： 判断字符串是否以“Str”开头。
子任务5： 将字符串“本科-硕士-博士”先截取出“硕士”，后分割           					字符串。
子任务6： 使用StringBuffer实现字符串的添加、删除、修改和截取。

## 第4页幻灯片
..
*
模块二 知识链接
String类
StringBuffer类

## 第5页幻灯片
String类
模块二 
知识链接
Java定义了两种初始化String对象的方式。
第一种方式：使用字符串常量直接初始化一个String对象，语法格式：  									String 变量名=字符串；
示例代码如下：
String str1=null;          //将字符串str1设置为空
String str2=“”;         //将字符串str2设置为空字符串
String str3=“hello”;     //将字符串str3设置为“hello”

## 第6页幻灯片
String类
模块二 
知识链接
第二种方式：调用String类构造方法初始化字符串对象，其语法格式：
 String 变量名=new String(字符串)；  							
String类的常见构造方法如下：

## 第7页幻灯片
String类
模块二 
知识链接

## 第8页幻灯片
String类
模块二 
知识链接

## 第9页幻灯片
String类
模块二 
知识链接

## 第10页幻灯片
String类
模块二 
知识链接

## 第11页幻灯片
StringBuffer类
模块二 
知识链接
StringBuffer类和String类最大的区别在于它的内容和长度都是可以改变的。StringBuffer类就像一个字符容器，当在其中添加或者删除字符时，操作的都是这个字符容器，因此并不会产生新的StringBuffer对象。

## 第12页幻灯片
StringBuffer类
模块二 
知识链接

## 第13页幻灯片
StringBuffer类
模块二 
知识链接

## 第14页幻灯片
，
*
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

## 第15页幻灯片
子任务1-代码实现
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

## 第16页幻灯片
子任务1-运行结果
代码运行结果如图所示:
模块三 
任务实现

## 第17页幻灯片
子任务2-代码实现
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

## 第18页幻灯片
子任务2-运行结果
代码运行结果如图所示:
模块三 
任务实现

## 第19页幻灯片
子任务3-代码实现
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

## 第20页幻灯片
子任务3-运行结果
代码运行结果如图所示:
模块三 
任务实现

## 第21页幻灯片
子任务4-代码实现
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

## 第22页幻灯片
子任务4-运行结果
代码运行结果如图所示:
模块三 
任务实现

## 第23页幻灯片
子任务5-代码实现
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

## 第24页幻灯片
子任务5-代码实现
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

## 第25页幻灯片
子任务5-运行结果
代码运行结果如图所示:
模块三 
任务实现

## 第26页幻灯片
子任务6-代码实现
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

## 第27页幻灯片
子任务6-代码实现
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

## 第28页幻灯片
子任务6-代码实现
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

## 第29页幻灯片
子任务6-代码实现
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

## 第30页幻灯片
子任务6-代码实现
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

## 第31页幻灯片
子任务6-运行结果
代码运行结果如图所示:
模块三 
任务实现

## 第32页幻灯片
感谢关注
# 无锡职业技术学院内部资料

JAVA程序设计项目教程

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

子任务1 使用正则表达式计算与“a*b”匹配的字符串是“aaaaab”   	还是“aaabbb”。
子任务2 使用Matcher类中的lookingAt()方法判断字符串  	“22bb23”与“aa2223”是否与模式“\\d+”匹配。

# ..

模块二 知识链接

Pattern类

Matcher类

正则表达式

# 正则表达式

模块二 
知识链接

正则表达式是由普通字符（如字符a~z）和特殊字符（元字符）组成的文本模式，例如，正则表达式“[a-z]*”描述了所有仅包含小写字母的字符串，其中a、z为普通字符，短横线、左右中括号及星号则为元字符。

# 正则表达式

模块二 
知识链接

点号可以匹配除“\n”之外的任何单个字符。

例如，正则表达式“t.n”可匹配“tan”“ten”“tcn”“t=n”“t n”（t和n之间有一个空格）等。

# 正则表达式

模块二 
知识链接

中括号可以匹配中括号内所有字符中的任意一个。可以在中括号内指定需要匹配的若干字符，表示仅使用这些字符参与匹配。

例如，正则表达式“t[abcd]n”只匹配“tan”“tbn”“tcn”“tdn”。中括号还有一些特殊写法，用于匹配某一范围内的字符，例如“[a-z]”匹配一个小写字母，“[a-zA-Z]”匹配一个字母、“[0-9]”匹配一个数字字符、“[a-z0-9]”匹配一个小写字母或一个数字字符等。

# 正则表达式

模块二 
知识链接

“|”符号可以匹配其左侧或右侧的符号。

例如，正则表达式“t（a|e|i|io）n”，除了“tan”“ten”和“tin”外，还可以匹配“tion”。使用“|”符号时，必须使用圆括号将可以匹配的字符括起来，圆括号用来标记正则表达式中的组（Group）。

# 正则表达式

模块二 
知识链接

“^”符号可以匹配一行的开始。

例如，正则表达式“^Spring.*”匹配“Spring MVC”，而不匹配“a Spring MVC”。若“^”符号在中括号内，则表示不需要参与匹配的字符。例如，正则表达式“[a-z&&[^bc]]”表示，可以匹配除b和c之外的小写字母，等价于“[ad-z]”，正则表达式“[a-z&&[^h-n]]”表示除h到n之外的小写字母，等价于“[a-go-z]”，正则表达式“[^b][a-z]+”表示首个字符不能是b且后跟至少一个小写字母。

# 正则表达式

模块二 
知识链接

“$”符号可以匹配一行的结束。

例如，正则表达式“.*App$”中的“$”符号表示匹配以App结尾的字符串，可以匹配“Andriod App”，而不匹配“iOS Apps”和“App.”。

# 正则表达式

模块二 
知识链接

“\”符号表示其后的字符是普通字符而非元字符。

例如，正则表达式“\$”用来匹配“$”字符而非结束，“\.”用来匹配“.”字符而非任一字符。

# 正则表达式

模块二 
知识链接

匹配次数元字符用来确定其左侧符号的出现次数，常用的匹配次数元字符如下表所示。

| 元字符 | 含义 |
|---|---|
| X* | 匹配X出现零次或多次，如Y，YXXXY |
| X+ | 匹配X出现一次或多次，如YXY，YXX |
| X? | 匹配X出现零次或一次，如Y，YXY |
| X{n} | 匹配X出现恰好n次 |
| X{n,} | 匹配X出现至少出现n次 |
| X{n,m} | n<=m，匹配X出现至少n次，最多m次 |

# 正则表达式

模块二 
知识链接

除了上述7种元字符外，正则表达式还有一些其他常用元字符，如下表所示。

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

# Pattern类

模块二 
知识链接

Pattern类用于创建一个正则表达式，也可以说创建一个匹配模式。Pattern类的构造方法是私有的，不可以直接创建正则表达式，为此，Pattern类提供了一个静态的complie()方法，通过调用complie()方法可以创建一个正则表达式，具体代码如下所示。

Pattern p = Pattern.compile("\\w+");

# Pattern类

模块二 
知识链接

Pattern类还提供了其他的方法

| 方法声明 | 功能描述 |
|---|---|
| static Pattern compile(String re) | 将正则表达式编译为模式 |
| Matcher matcher(CharSequence input) | 根据模式为字符串input创建匹配器。String类实现了CharSequence接口，CharSequence接口可视为String |
| Static boolean matches(String regex, 
                CharSequence input) | 判断字符串input是否匹配正则表达式regex。该方法适合于只进行一次匹配情况 |
| String pattern() | 返回模式使用的正则表达式 |
| String[] split(CharSequence input) | 根据模式将字符串input分割为字符串数组 |
| String[] split(CharSequence input,int limit) | 根据模式将字符串input分割为字符串数组，同时指定了子串的最大个数为limit |

# Matcher类

模块二 
知识链接

Matcher类用于验证Pattern定义的模式与字符串是否匹配，因此Matcher实例也称为匹配器。Matcher类的构造方法也是私有的，不能直接创建Macher实例，只能通过Pattern.matcher()方法获取该类的实例，多个Matcher对象可以使用同一Pattern对象。

# Matcher类

模块二 
知识链接

Matcher类的常用方法

| 方法声明 | 功能描述 |
|---|---|
| Pattern pattern() | 返回匹配器的模式 |
| Matcher usePattern(Pattern p) | 返回匹配器的模式为p |
| Matcher reset() | 重设匹配器到初始状态 |
| Matcher reset(CharSequence input) | 重设匹配器到初始状态，并使用input为目标字符串 |
| Boolean find() | 在目标字符串中查找下一个匹配字符串，找到返回true |
| int start() | 正则表达式所匹配的字符串在整个字符串中第一次出现的索引 |

# Matcher类

模块二 
知识链接

| 方法声明 | 功能描述 |
|---|---|
| int end() | 正则表达式所匹配的字符串在整个字符串中最后一次出现的索引 |
| String group() | 返回匹配到的子字符串 |
| String group(int i) | 返回上一次匹配的子串中与第i个组相匹配的那个子串。正则表达式中以一对圆括号括起来的部分称为组 |
| boolean matcher() | 对整个字符串进行匹配，只有整个字符串都匹配了才返回true |
| boolean lookingAt() | 从目标字符串的第一个字符开始匹配，有匹配成功的返回true，否则返回false |
| String replaceAll(String s) | 将目标字符串中与模式相匹配的全部子串替换为s并返回替换后的字符串 |
| String replaceFirst(String s) | 将目标字符串中与模式相匹配的首个子串替换为s并返回替换后的字符串 |

# ，

模块三  任务实现

子任务1 使用正则表达式计算与“a*b”匹配的字符串是“aaaaab”   	还是“aaabbb”。
子任务2 使用Matcher类中的lookingAt()方法判断字符串  	“22bb23”与“aa2223”是否与模式“\\d+”匹配。

# 子任务1-代码实现

结合任务描述和知识链接中相关知识点可以得到如下代码。

模块三 
任务实现

import java.util.regex.Matcher;
import java.util.regex.Pattern;
public class Example25 {
    public static void main(String[] args) {
        Pattern p1 = Pattern.compile("a*b");    //根据参数指定的正则表达式创建模式
        Matcher m1 = p1.matcher("aaaaab");    //获取目标字符串的匹配器
        Matcher m2 = p1.matcher("aaabbb");    //获取目标字符串的匹配器
        System.out.println(m1.matches());           //执行匹配器
        System.out.println(m2.matches());           //执行匹配器
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

import java.util.regex.Matcher;
import java.util.regex.Pattern;
public class Example26 {
    public static void main(String[] args) {
        Pattern p=Pattern.compile("\\d+");
        Matcher m1=p.matcher("22bb23");
        System.out.println("字符串22bb23与模式p的匹配结果:"+ m1.lookingAt());
        Matcher m2=p.matcher("aa2223");
        System.out.println("字符串aa2223与模式p的匹配结果:"+m2.lookingAt());
    }
}

# 子任务2-运行结果

代码运行结果如图所示:

模块三 
任务实现

# 感谢关注
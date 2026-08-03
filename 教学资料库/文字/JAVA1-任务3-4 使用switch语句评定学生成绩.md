# 无锡职业技术学院内部资料

JAVA程序设计

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

使用switch语句评定从键盘输入的学生成绩。

# ..

模块二 知识链接

switch条件语句功能

switch条件语句语法格式

# switch条件语句

语句功能

模块二 
知识链接

如果在多个备选方案中处理多项选择时，用if…else结构就显得很繁琐。这时可以使用switch语句来实现同样的功能。switch语句基于一个表达式条件来执行多个分支语句中的一个，它是一个不需要布尔求值的流程控制语句。switch语句也称多分支的开关语句。

# switch条件语句

switch(表达式){
case  常量值1：语句1；
break；
case  常量值2：语句2；  
break；
……
case  常量值n：语句n；
break；
[default：上面情况都不符合情况下执行的语句；]
}

模块二 
知识链接

表达式的值应为一个byte、short、int、char类型的数值

“常量表达式”的值必须各不相同否则会出现相互矛盾的现象。常量表达式仅起语句标号作用，并不进行条件判断。

有一个default语句作为其它情况都不匹配时的出口,各case及default子句的先后次序，不影响程序执行结果。

每一分支语句中都用break语句作为结束。如果忽略掉break语句，程序将继续测试并有可能执行下一分支，直到遇到break语句或当前switch语句体结束。

语法格式

# ，

过渡页

模块三  任务实现

使用switch语句评定从键盘输入的学生成绩。

模块三 
任务实现

# *

过渡页

从键盘输入成绩

匹配等级

模块三  任务实现

输出结果

# 任务源码

结合任务3-4中的描述和知识链接中switch条件语句知识点可以得到文件3-4所示的代码：

模块三 
任务实现

文件3-4 Example04.Java

1 import Java.util.Scanner;
2 public class Example04 {
3	public static void main(String[] args) {
4		Scanner input=new Scanner(System.in);
5	    System.out.println("请输入数学成绩：");
6	    int math_score=input.nextInt();
7	    switch((int)math_score/10) {
8	    case 10:
9	    case  9:
10	    	System.out.println("优秀");
11    	break;
12    case 8:
13    	System.out.println("良好");
14    	break;
15    case 7:
16    	System.out.println("中等");
17    	break;	
18    case 6:
19    	System.out.println("及格");
20    	break;	
21    default:
22    	System.out.println("不及格");
23    	break;		
24    }
25   }
25  }

# 输出结果

模块三 
任务实现

运行结果如图3-7所示：

图3-7文件3-4的运行结果

# 感谢关注
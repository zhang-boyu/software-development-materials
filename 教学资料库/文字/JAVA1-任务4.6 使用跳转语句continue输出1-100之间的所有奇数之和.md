# 无锡职业技术学院内部资料

JAVA程序设计

# *

任务描述

知识链接

任务实现

目录

# *

输出 1～100 的所有奇数之和。

模块一  任务描述

# *

continue语句

return语句

模块二  知识链接

# continue语句

模块二 
知识链接

continue 语句只能用于循环结构语句中，其作用是结束本次循环，然后进行下一次循环的执行。它的语法格式如下：
continue; 
其中，continue 是关键字。
（1）continue 语句也称为循环的短路语句，用在循环结构语句中，使程序执行到
continue 语句时，回到循环的入口，执行下一次循环，此时循环体内写在 continue 语句后的语句不会被执行。

# continue语句

模块二 
知识链接

（2）continue 语句与 break 语句不同的是，它结束的是本次循环，而不是整个循环，所以相对于 break 语句的终止循环功能，continue 语句的功能应该是中断循环，这种中断是暂时的，下一次循环还是要执行的。例如，以下代码中 while 语句实际上只输出 3 次循环变量 i 的值。
int i=1; 
while(i++<=4 ){ 
if (i==2){ 
continue; 
} 
System.out.print(" i=" + i ); 
}

# return语句

模块二 
知识链接

return 语句，称为返回语句，其语法格式也很简单，具体如下：
return; 
return 语句并不是专门用于结束循环的，return 语句的功能是结束一个方法的执行。一
旦在循环体内执行到一条 return 语句，return 语句将会结束其所在方法的执行，而循环自然也随之结束。
return 语句与 continue 和 break 语句不同的是，return 语句直接结束整个方法的执行，
不管这个 return 语句处于多少层循环之内。

# return语句

模块二 
知识链接

例如以下代码，遇到 return 语句时直接结束 main( )方法的执行。
public static void main(String[] args){ 
for (int i=0;i<2;i++){ 
for (int j=0; j<2;j++){ 
if (j==1){ 
return; 
} 
System.out.println("j 的值是" + j) ; 
} 
} 
}

# *

输出 1～100 的所有奇数之和。

模块三  任务实现

# 模块三 
任务实现

运行结果显示

使用continue输出1-100之间的所有奇数之和

| public class Example06 {
    public static void main(String[] args) {
        int sum = 0; // sum变量用来存放奇数的累加和
        for (int i = 1; i <= 100; i++) { // 循环变量i从1遍历到100
            if (i % 2 == 0) { // 如果i是偶数
                continue; // 跳过本次循环，继续下一个i的值
            }
            sum += i; // 如果i是奇数，将i的值累加到sum中
        }
        // 输出1到100之间的奇数和
        System.out.println("1-100奇数之和是：" + sum);
    }
} |

# 感谢关注
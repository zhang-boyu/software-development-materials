# 无锡职业技术学院内部资料

JAVA程序设计

# *

任务描述

知识链接

任务实现

目录

# *

模块一  任务描述

定义整数类型变量x,y,z的值为0，表达式a = x > 0 & y++ > 1，输出a和y的值。和表达式b = x > 0 && z++ > 1，输出b和z的值。

# *

模块二 知识链接

逻辑运算符

# 模块二 
知识链接

逻辑运算符及用法

逻辑运算符用于对布尔型的数据进行操作，其结果仍是一个布尔值。Java中的逻辑运算符及用法具体如下表所示。

| 运算符 | 运算 | 范例 | 结果 |
|---|---|---|---|
| & | 与 | true & true | true |
|  |  | true & false | false |
|  |  | false & false | false |
|  |  | false &true | false |
| | | 或 | true | true | true |
|  |  | true | false | true |
|  |  | false| false | false |
|  |  | false| true | true |
| ^ | 异或 | true ^ true | false |
|  |  | true ^ false | true |
|  |  | false ^ false | false |
|  |  | false ^ true | true |

# 模块二 
知识链接

逻辑运算符及用法

| 运算符 | 运算 | 范例 | 结果 |
|---|---|---|---|
| ! | 非 | !true | false |
|  |  | !false | true |
| && | 短路与 | true && true | true |
|  |  | true && false | false |
|  |  | false && false | false |
|  |  | false && true | false |
| || | 短路或 | true || true | true |
|  |  | true || false | true |
|  |  | false|| false | false |
|  |  | false|| true | true |

# 模块二 
知识链接

（1）逻辑运算符可以针对结果为布尔值的表达式进行运算。
例如，x > 3 && y != 0。
（2）运算符“&”和“&&”都表示与操作，当且仅当运算符两边的操作数都为true时，其结果才为true，否则结果为false。虽然运算符“&”和“&&”都表示与操作，但两者在使用上还有一定的区别。在使用“&”进行运算时，不论左边为true或者false，右边的表达式都会进行运算。在使用“&&”进行运算，当左边为false时，右边的表达式就不再进行运算，因此“&&”被称作短路与。

使用逻辑运算符的注意事项

# 模块二 
知识链接

（3）运算符“|”和“||”都表示或操作，当运算符两边的任一表达式值为true时，其结果为true。只有两边表达式的值都为false时，其结果才为false。同逻辑与操作类似，“||”运算符为短路或，当运算符“||”的左边为true时，右边的表达式不再进行运算，具体示例如下。

使用逻辑运算符的注意事项

int x = 0;
int y = 0;
boolean b = x==0 || y++>0

# 模块二 
知识链接

（4）运算符“^”表示异或操作，当运算符两边的布尔值相同时（都为true或都为false），其结果为false。当两边表达式的布尔值不相同时，其结果为true。

使用逻辑运算符的注意事项

# *

过渡页

模块三  任务实现

定义整数类型变量x,y,z的值为0，表达式a = x > 0 & y++ > 1，输出a和y的值。和表达式b = x > 0 && z++ > 1，输出b和z的值。

# 代码实现

1  public class Example13 {
2	public static void main(String[] args) {
3		int x = 0; 		// 定义变量x，初始值为0
4		int y = 0; 		// 定义变量y，初始值为0
5		int z = 0; 		// 定义变量z，初始值为0
6		boolean a, b;   	// 定义boolean变量a和b
7		a = x > 0 & y++ > 1; 	// 逻辑运算符&对表达式进行运算
8		System.out.println("a="+a);
9		System.out.println("y = " + y);
10		b = x > 0 && z++ > 1; // 逻辑运算符&&对表达式进行运算
11		System.out.println("b="+b);
12		System.out.println("z = " + z);
13 	 }
14  }

模块三 
任务实现

# 运行结果

模块三 
任务实现

# 感谢关注
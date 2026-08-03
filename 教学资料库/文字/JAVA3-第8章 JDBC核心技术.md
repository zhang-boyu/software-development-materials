# <<JSP与Servlet开发技术与典型应用教程>>

JSP and  servlet  development  technology  and  typical application  course

第八章    JDBC核心技术

大连理工大学出版社

# 01

02

03

掌握JDBC编程基本操作、JDBC事务操作、预处理操作

理解DAO模式、结果集处理方式

了解JDBC原理

能力目标

# 01

02

03

培养严谨的逻辑思维能力

提高编码、调试、排错能力；培养整体架构的能力

培养主动学习、主动思考、主动改进的能力

素质目标

# 8.1  JDBC基础

# 第八章    Java数据库连接

8.1  JDBC基础 
8.1.1  JDBC简介  
8.1.2  ODBC数据源的配置 
8.1.3  MYSQL数据库安装与驱动下载

# 第八章   JDBC核心技术

本课任务：

JDBC基础
什么是JDBC
JDBC核心接口介绍
Mysql数据库安装与驱动下载

# 8.1  JDBC基础

8.1.1  什么是JDBC

百度百科是这样解释JDBC：Java数据库连接，（Java Database Connectivity，简称JDBC）是Java语言中用来规范客户端程序如何来访问数据库的应用程序接口，提供了诸如查询和更新数据库中数据的方法。我们通常说的JDBC是面向关系型数据库的

# 8.1  JDBC基础

8.1.1什么是JDBC 
JDBC-ODBC桥：使用JDBC-ODBC桥接方式到ODBC驱动程序进行数据库操作。ODBC出现的比较早，支持数据源广泛，简单便利，是一种使用普遍的驱动程序。
本地API驱动：直接使用各个数据库生产商提供的JDBC驱动程序，因为只能应用在特定的数据库上，会丧失程序的可移植性，不过性能很高。
网络协议驱动：这种类型的驱动给客户端提供了一个网络API，客户端上的JDBC驱动程序使用套接字（Socket）来调用服务器上的中间件程序，后者在将其请求转化为所需的具体API调用。
本地协议驱动：这种类型的驱动使用Socket，直接在客户端和数据库间通信。设计上采用紧密耦合的方式，可发挥数据库的特定功能，提供较高的运行效率，此类驱动也一般被认定为是较好的一种驱动程序。

# 8.1  JDBC基础

8.1.2 JDBC核心接口介绍

JDBC规范提供了若干接口，而掌握这些接口的使用方法是掌握JDBC技术的关键。JDBC中的核心接口是：Driver、DriverManager、Connection、Statement、PreparedStatement和ResultSet。
（1）Driver
驱动程序，会将自身加载到DriverManager中去，并处理相应的请求并返回相应的数据库连接（Connection）
（2）DriverManger
负责加载各种不同驱动程序（Driver），并根据不同的请求，向调用者返回相应的数据库连接。
（3）Connection
数据库连接，负责与进行数据库间通讯，SQL执行以及事务处理都是在某个特定Connection环境中进行的。可以产生用以执行SQL的Statement。

# 8.1  JDBC基础

8.1.2 JDBC核心接口介绍

JDBC规范提供了若干接口，而掌握这些接口的使用方法是掌握JDBC技术的关键。JDBC中的核心接口是：Driver、DriverManager、Connection、Statement、PreparedStatement和ResultSet。
（4）Statement
用来向数据库发送SQL语句，这样数据库就会执行发送过来的SQL语句（针对静态SQL语句和单次执行）。
（5）PreparedStatement
用来执行包含动态参数的SQL查询和更新（在服务器端编译，允许重复执行以提高效率）。
（6）ResultSet
用来表示执行查询操作后产生的查询结果集，结果集是一个有行有列的二维的表格。操作结果集要移动ResultSet内部的游标，以及获取当前行上的每一列上的数据。

# 8.1  JDBC基础

8.1.3  Mysql数据库安装与驱动下载

下载MySQL安装文件。登录网址http://www.mysql.com/downloads/mysql/，会出现下载列表如图 8-2 MySQL下载列表所示，根据个人操作系统选择相应的下载项，这里下载的是Windows（x86,64-bit）,MSI Installer，注意首先需要登录Oracle账户。
运行安装程序出现图 8-3 安装类型选择界面，选择Custom（自定义）安装，方便将MySQL安装到非系统盘。

# 8.2  JDBC编程基本操作

# JDBC编程基本操作 
注册数据库驱动程序 
建立数据库连接
使用Statement接口实现添删改查操作
使用PreparedStatement接口实现添删改查操作
可滚动结果集和可更新结果集
实现Connection工厂类

第八章    JDBC核心技术

# 8.2  JDBC编程基本操作

8.2.1 注册数据库驱动程序

JDBC编程的准备工作是需要下载驱动包，解压后得到 jar 库文件，然后在对应的项目中导入该库文件。
JDBC编程的第一步是注册 JDBC 驱动程序，示例代码如下所示：
try {
			Class.forName("com.mysql.jdbc.Driver");
		} catch (ClassNotFoundException e) {
			e.printStackTrace();
		}
	}

# 8.2  JDBC编程基本操作

8.2.2 建立数据库连接
	
	JDBC编程的第二步是建立数据库连接，前一节在JVM环境下注册了JDBC运行所需要的类库后，JVM和数据库之间并没有直接联系，只有通过本节操作后才能获得一个数据库连接对象Connection建立程序和数据库的联系。
	
	建立连接过程涉及两个主要API：java.sql.DriverManager类和java.sql.Connection接口。DriverManager是JDBC用于管理驱动程序的类，通过调用它的static方法getConnection( )可以返回一个数据库连接对象Connection。

# 8.2  JDBC编程基本操作

Connection对象的常用方法

| 方法 | 描述 |
|---|---|
| Statement  createStatement( ) | 创建一个 Statement 对象来将 SQL 语句发送到数据库 |
| DatabaseMetaData  getMetaData( ) | 获取一个 DatabaseMetaData 对象，该对象包含关于此 Connection 对象所连接的数据库的元数据 |
| PreparedStatement  	preparedStatement(String sql) | 创建一个 PreparedStatement 对象来将参数化的 SQL 语句发送到数据库 |
| void  setAutoCommit(boolean autocommit) | 将此连接的自动提交模式设置为给定状态 |
| void  commit( ) | 使所有上一次提交/回滚后进行的更改成为持久更改，并释放此Connection对象当前持有的所有数据库锁 |
| void  rollback( ) | 取消在当前事务中进行的所有更改，并释放此 Connection 对象当前持有的所有数据库锁 |

# 8.2  JDBC编程基本操作

获取数据库连接的方法就是调用DriverManager 对象的静态方法 getConnection( )。
conn = DriverManager.getConnection
("jdbc:mysql://127.0.0.1:3306/usertable", "root", "123456");
      之前Mysql注册方式是基于 jar 包：mysql-connector-java-5.1.39-bin.jar，现在如果所使用的MySQL 8.0 以上版本的数据库连接则有所不同：
	com.mysql.jdbc.Driver 更换为 com.mysql.cj.jdbc.Driver。
	MySQL 8.0 以上版本不需要建立 SSL 连接的，需要显示关闭。
	allowPublicKeyRetrieval=true 允许客户端从服务器获取公钥。
	需要设置 CST。

# 8.2  JDBC编程基本操作

8.2.3使用Statement接口实现添删改查操作
	
       JDBC编程的第三步，通过数据库操作代理对象（Statement）进行添加、删除、修改和查询操作可以分为两种情况：一种不会对数据库记录产生影响的操作（查询）和另一种可能会对数据库记录产生影响的操作（添加、删除、修改）。
	JDBC对数据库进行查询操作时，首先需要获得数据库代理接口java.sql.Statement的一个实现对象。Statement的实现类对象通过第二步中创建的Connection对象调用createStatement( )方法获得。

# 8.2  JDBC编程基本操作

Statement对象的常用方法

8.2.3使用Statement接口实现添删改查操作

| 方法 | 描述 |
|---|---|
| ResultSet  executeQuery(String sql) | 执行给定的SQL查询 语句，该语句返回单个 ResultSet 对象 |
| int  executeUpdate(String sql) | 执行给定SQL语句，该语句可能为INSERT、UPDATE 或 DELETE 语句，或者不返回任何内容的 SQL 语句（如 SQL DDL 语句） |
| void  close( ) | 立即释放此Statement 对象的数据库和 JDBC 资源 |

# 8.2  JDBC编程基本操作

在获得了Statement类型的对象后，通过调用它的executeQuery( )方法可以进行数据库查询，JDBC会将返回的数据库查询结果封装成为java.sql.ResultSet接口类型的对象。

8.2.3使用Statement接口实现添删改查操作

# 8.2  JDBC编程基本操作

8.2.3使用Statement接口实现添删改查操作
	
       对数据库中的表进行添加、删除、修改操作时同样需要通过Statement对象进行，与前面的查询操作不同的地方在于，添删改操作不会返回一个查询结果集ResultSet，但是添删改操作会返回一个整数表示当前操作所影响的记录行数，所以添删改操作不能调用executeQuery( )方法，而需要调用executeUpdate( )方法（不要被方法名迷惑以为该方法只能执行update操作，实际上所有对数据库产生影响的操作都可以调用executeUpdate，包括添加、删除、修改、DDL命令）。

# 8.2  JDBC编程基本操作

8.2.3使用Statement接口实现添删改查操作
	JDBC编程需要在Java程序和底层数据库中间建立连接，这些连接需要消耗系统资源，如果在使用完数据库后不关闭连接，随着操作次数增加系统资源会很快耗尽，因此需要在进行完相关操作后关闭连接，回收资源。

# 8.2  JDBC编程基本操作

8.2.4 使用PreparedStatement接口实现添删改查操作
	使用Statement进行数据库操作时，每次操作都会建立新的操作语句。JDBC提供预备语句（Prepared  Statement）建立一个带有参数的SQL语句，每次操作时只需要为变量赋值就可以反复使用这条语句，这种特性可以提高性能，同时可以简化开发。PreparedStatement对象可以通过Connection对象调用preparedStatement( )方法获得。

# 8.2  JDBC编程基本操作

PreparedStatement对象的常用方法

8.2.4 使用PreparedStatement接口实现添删改查操作

| 方法 | 描述 |
|---|---|
| boolean  execute( ) | 在此 PreparedStatement 对象中执行 SQL 语句，该语句可以是任何种类的 SQL 语句 |
| ResultSet  executeQuery( ) | 在此 PreparedStatement 对象中执行 SQL 查询，并返回该查询生成的 ResultSet 对象 |
| int  executeUpdate( ) | 在此 PreparedStatement 对象中执行 SQL 语句，该语句必须是一个 SQL 数据操作语言语句，比如 INSERT、UPDATE 或 DELETE 语句；或者是无返回内容的 SQL 语句，比如 DDL 语句 |
| void  setString(int  x,String value) | 将字符串value赋给第x个占位符，x从1开始 |
| void  setInt(int  x,int value) | 将整形value赋给第x个占位符，x从1开始 |

# 8.2  JDBC编程基本操作

8.2.5 可滚动结果集和可更新结果集
       
       ResultSet默认只能按顺序遍历结果集中的所有行，并且结果集中的数据更改不会影响到数据库中的记录。如果希望在结果集上前后移动，并且能够通过结果集的变化更新数据库中的记录，则需要通过下面的方法得到Statement对象:
       Statement  stat = con.createStatement(type,concurrency);
	或者通过下面的方法得到一个PreparedStateme对象：
       PreparedStateme  ps=con.preparedStatement(cmd,type,concurrency);
	ResultSet类提供了一些静态常量来表示type和concurrency。

# 8.2  JDBC编程基本操作

ResultSet类的type值

ResultSet类的concurrency值

| TYPE_FORWARD_ONLY | 结果集不能滚动 |
|---|---|
| TYPE_SCROLL_INSENSITIVE | 结果集可以滚动，对数据库变化不敏感 |
| TYPE_SCROLL_SENSITIVE | 结果集可以滚动，对数据可变化敏感 |
| CONCUR_READ_ONLY | 结果集只读 |
|---|---|
| CONCUR_UPDATABLE | 结果集可以更新数据库 |

# 8.2  JDBC编程基本操作

ResultSet对象的常用方法

| 方法 | 描述 |
|---|---|
| boolean  absolute( int   row) | 将游标移动到此 ResultSet 对象的给定行编号 |
| int   getRow( ) | 获取当前行编号，编号从1开始 |
| boolean  absolutely( int n ) | 将游标移动到第n行 |
| void  afterLast( ) | 将游标移动到此 ResultSet 对象的末尾，正好位于最后一行之后 |
| void  beforeFirst( ) | 将游标移动到此 ResultSet 对象的开头，正好位于第一行之前 |
| boolean  isFirst( ) | 游标是否在第一行 |
| boolean  isLast( ) | 游标是否在最后一行 |
| boolean  isBeforeFirst( ) | 游标是否在第一行之前 |
| boolean  isAfterLast( ) | 游标是否在最后一行之后 |
| boolean  first( ) | 将游标移动到此 ResultSet 对象的第一行 |
| boolean   last( ) | 将游标移动到此 ResultSet 对象的最后一行 |
| boolean   next( ) | 将游标从当前位置向后移一行 |
| boolean   previous( ) | 将游标从当前位置向前移一行 |
| void  insertRow( ) | 将插入行上的内容更新到数据库 |
| void  deleteRow( ) | 删除数据库和结果集中的当前行 |
| void updateInt(int column,int data) | 更新结果集中当前行的某个字段值，其他数据类型格式相同 |
| void  updateRow( ) | 将当前行上的更新发送到数据库中 |
| void  cancelRowUpdates( ) | 撤销对当前行的更新 |

# 8.2  JDBC编程基本操作

8.2.6 实现Connection工厂类
       
       在实际数据库编程中，因为每次获得Connection都要重新创建一个Connection对象，所以代码中出现了大量重复，可以通过创建一个Connection工厂类封装创建Connection对象来解决这个问题

# 8.3 事务处理

# 第八章    JDBC核心技术

事务处理
在JDBC中处理数据库事务
 事务并发问题

# 8.3  事务处理

8.3.1 在JDBC中处理数据库事务
	 事务是SQL提供的一种机制，用于强制数据库的完整性和维护数据的一致性。
        事务的思想是保证多步操作中的任何一步失败的话，则整个事务回滚，如果所有步骤都成功则这个事务可以提交，从而把所有的改变保存到数据库中。

# 8.3 事务处理

JDBC提供对事务的支持，默认情况下事务是自动提交的，即每次执行executeUpdate( )语句，相关操作都是即时保存到数据库中的。如果不想让这些SQL命令自动提交，可以在获得连接后使用下面的语句关闭自动提交：
		con.setAutoCommit(false);
	然后执行JDBC操作命令，假设所有操作都能正确执行，在操作语句后面加上下面的语句就能提交事务，所做的改动将保存到数据库中：
		con.commit( );
	如果在操作中出现异常，调用下面的语句可以使事务回滚，所做的改动不会保存到数据库中：
		con.rollback( );

# 8.3  事务处理

8.3.2 事务并发问题
脏读是指在一个事务处理过程中读取了另一个未提交事务中的数据。
可重复读是指对于数据库中的某个数据，一个事务范围内多次查询返回了相同的数据值。
不可重复读是指对于数据库中的某个数据，一个事务范围内多次查询返回了不同的数据值，这是由于在查询间隔被另一个事务修改并提交了。在某些情况下，不可重复读并不是问题，比如，多次查询某个数据记录，以最后一次查询结果为准。
幻读是指是指当事务不是独立执行时发生的一种现象。

# 8.3  事务处理

8.3.2 事务并发问题

数据库的四种隔离级别

# 8.4 基于MVC模式的数据库访问

# 第八章    JDBC核心技术

基于MVC模式的数据库访问
使用DTO、ENTITY和DAO
一个基于MVC模式的数据库访问应用程序体验

# 8.4  基于MVC模式的数据库访问

8.4.1 使用DTO、ENTITY和DAO
	在项目开发中，根据代码所起的作用可以分为界面显示代码、业务处理代码、逻辑控制代码、数据访问代码、数据传输代码等。
      DTO（数据传输对象）主要的作用是在不同类中进行数据的交换，将大量数据放入一个DTO中便于整体传输。
      ENTITY（实体类）与DTO在结构和作用方面非常相似，但又有着本质上的不同，ENTITY一般是和数据表做映射，ENTITY中的属性对应表中的列，ENTITY的名称与表名一致。
      DAO（数据访问对象）主要的作用是封装对数据库操作的JDBC代码，把增删改查相关的JDBC代码放入DAO层中，对外提供操作数据库的添删改查方法，封装的优点是便于后期代码的维护与排错。

# 8.4  基于MVC模式的数据库访问

8.4.2 一个基于MVC模式的数据库访问应用程序体验
	DAO是Data Access Object数据访问对象。数据访问是与数据库打交道，对数据库中的数据进行添删改查的操作，在项目开发中数据访问对象夹在业务逻辑与数据库资源中间。通过数据库访问对象可以将数据库的相关操作代码，如加载驱动、建立数据库连接、数据库添删改查、关闭连接等操作封装起来。上层代码需要对数据库访问时直接调用数据库访问对象中的相关方法，对于上层代码来说，数据库的操作是不可见的。

基于MVC模式的数据库访问 ---一个基于MVC模式的数据库访问应用程序体验

# 8.4 基于MVC模式的数据库访问

基于MVC的数据库访问程序清单如下表所示，其中UserDAO.java、User.java共同组成了用户模型层（M），UserServlet.java充当了其中的控制层（C），index.jsp负责显示，充当了视图层。

8.4.2 一个基于MVC模式的数据库访问应用程序体验

| 文件名 | 功能描述 |
|---|---|
| UserDAO.java | 数据访问组件，定义了对用户表的访问方法。 |
| User.java | JavaBean组件，定义了用户表的相关信息。 |
| UserServlet.java | 在整个程序中充当控制器的角色，用于程序转向。 |
| index.jsp | 页面，为用户提供了输入添加用户的界面和查询、删除界面。 |
| web.xml | 配置servlet相关信息。 |

# 本章小结

Java Web应用通过JDBC对数据库中的数据进行查询和更新。JDBC由基于Java语言的通用JDBC API和数据库专用JDBC驱动程序组成。对于JDBC数据库编程来说，其基本的编程过程包含四个基本步骤：注册数据库驱动程序，建立数据库连接，通过数据库操作代理对象（Statement）进行添加、删除、修改、查询操作，关闭数据库连接资源。
通过DAO对象可以将数据库的相关操作代码，如加载驱动、建立数据库连接、数据库添删改查、关闭连接等操作封装起来。这样的设计模式可以提高系统的可维护性并且增加代码的可重用性。
事务是SQL提供的一种机制，用于强制数据库的完整性和维护数据的一致性。在JDBC中提供了对事务的支持，可以根据需要对事务进行自动提交、手动提交和回滚处理。
Mysql的事务四种隔离级别读未提交（read-uncommitted）、不可重复读（read-committed）、可重复读（repeatable-read）、可串行化（serializable）。
在本章学习过程中，需要对书上的代码善用“拿来主义”，并知其然知其所以然，细细研究分析JDBC代码，不断重构完善自己的代码，是对所学知识达到融会贯通最简洁的途径。理无专在，而学无止境也，然则问可少耶。

# 实战演练

[实战 8-1] 完善例程8-2，完成代码中查询显示指定id记录详细值的功能。
[实战 8-2] 完善例程8-3，完成代码中查询指定id记录值的功能。
[实战 8-3] 完善例程8-9，使用Connection工厂类修改一个基于MVC模式的数据库访问应用程序体验，实现分层操作。

# <<JSP与Servlet开发技术与典型应用教程>>

感谢观看 THANK YOU!

大连理工大学出版社

第八章    JDBC核心技术
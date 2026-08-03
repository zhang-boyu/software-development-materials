# 第11章  JDBC

Java基础入门（第3版）

# 学习目标/Target

# 章节概述/ Summary

在软件开发过程中，经常要使用数据库存储和管理数据。为了在Java中提供对数据库访问的支持，SUN公司于1996年提供了一套访问数据库的标准Java类库，即JDBC。本章将主要围绕什么是JDBC、JDBC的常用API、JDBC入门程序等知识进行详细地讲解。

# 目录/Contents

# 什么是JDBC

11.1

# 11.1.1  JDBC概述

先定一个小目标！

# 11.1.1  JDBC概述

JDBC的全称是Java数据库连接（Java Database Connectivity），它是一套用于执行SQL语句的Java API。应用程序可通过这套Java API连接到关系数据库，并使用SQL语句完成对数据库中数据的查询、新增、更新和删除等操作。使用JDBC连接数据库驱动，用户就不必用户不必编写Java程序与数据库交互的底层代码，使得代码的通用性更强。

JDBC介绍

# 11.1.1  JDBC概述

应用程序使用JDBC访问数据库的方式

由左图可知，不同的数据库需要使用不同的JDBC驱动进行连接，例如，访问MySQL数据库需要使用MySQL驱动，访问Oracle数据库需要使用Oracle驱动。而JDBC在应用程序与数据库之间起到了一个桥梁作用。应用程序与数据库连接成功后即可对数据库进行相应的操作。

# 11.1.2  JDBC驱动程序

先定一个小目标！

# 11.1.2  JDBC驱动程序

JDBC驱动程序分类

JDBC本身提供的是一套数据库操作标准，而JDBC中提供的这些标准又需要各个数据库厂商实现，针对每一个数据库而言，每一个数据库厂商都会为其数据库产品提供一个JDBC的驱动程序，目前比较常见的JDBC驱动程序可以分为以下4类。

# 11.1.2  JDBC驱动程序

1. JDBC-ODBC桥驱动程序

JDBC-ODBC桥驱动程序由SUN公司开发，是JDK提供的数据库操作标准API，这种类型的驱动实际是把所有 JDBC的调用传递给ODBC（Open Database Connectivity，开发数据库连接），再由ODBC调用本地数据库驱动代码，操作数据库中的数据。通过JDBC-ODBC桥驱动操作数据库的方式如下所示：

由于JDBC-ODBC桥驱动程序经过几次中间调用，所以执行效率比较低。

# 11.1.2  JDBC驱动程序

2. 本地API驱动程序

本地API驱动直接将JDBC API 映射成数据库特定的客户端API。这种驱动包含特定数据库的本地API，通过它可以访问数据库的客户端。通过本地API驱动操作数据库的方式如下所示：

通过本地 API驱动程序访问数据库减少了ODBC的调用环节，提高了数据库访问的效率。

# 11.1.2  JDBC驱动程序

3. 网络协议驱动程序

网络协议驱动是用纯Java语言编写的，JDBC把对数据库的访问请求传递给网络上的中间件服务器，中间件服务器先把请求转换为数据库通信协议请求，然后再通过中间件服务器与数据库进行交互。使用这种类型驱动程序的Java应用程序可以与服务器端完全分离，具有很大的灵活性。通过网络协议驱动操作数据库的方式：

# 11.1.2  JDBC驱动程序

4. 本地协议驱动

本地协议驱动是用使用纯Java语言编写的。本地协议驱动通常由数据库厂商直接提供驱动的JAR包，本地协议驱动程序直接将JDBC调用转换为数据库特定的网络通信协 议,然后与数据库进行交互。通过本地协议驱动操作数据库的方式：

# 11.1.2  JDBC驱动程序

上述4种类型中，JDBC-ODBC桥驱动程序由于执行效率不高，更适合开发应用时的一种过渡方案； 如果是在内联网（Intranet）的应用，可以考虑本地API 驱动程序；如果是基于互联网（Internet）并且需要同时连接多个不同种类的数据库, 并发连接要求高的应用，可以考虑JDBC-Net Driver。如果是基于互联网（Internet）但连接单一数据库的应用，可以考虑Native Protocol Driver。本章将基于Native Protocol Driver类型对JDBC进行讲解

# JDBC的常用API

11.2

# 11.2  JDBC的常用API

先定一个小目标！

# 11.2  JDBC的常用API

JDBC的API

JDBC的核心就是为开发人员提供操作数据库的Java API类库，Java程序开发人员可以利用这些类库开发数据库应用程序，如创建数据库连接、执行SQL语句、检索结果集、访问数据库元数据等。JDBC的 API主要位于java.sql包中，该包定义了一系列访问数据库的接口和类。本节将针对java.sql包内常用的接口和类进行详细讲解。

# 11.2  JDBC的常用API

1. Driver接口

Driver接口是所有JDBC驱动程序必须实现的接口，该接口专门提供给数据库厂商使用。需要注意的是，在编写JDBC程序时，必须要把所使用的数据库驱动程序（这里指MySQL驱动JAR包）或类库加载到项目的classpath中。

# 11.2  JDBC的常用API

2. DriverManager类

使用JDBC连接数据库，需要用到DriverManager类，DriverManager类用于加载JDBC驱动并且创建JDBC程序与数据库的连接。在DriverManager类中，定义了两个比较重要的静态方法，如下所示。

| 方法声明 | 功能描述 |
|---|---|
| registerDriver(Driver driver) | 该方法用于向DriverManager中注册给定的JDBC驱动程序 |
| getConnection
(String url,String user,String password) | 该方法用于建立和数据库的连接，并返回表示连接的Connection对象 |

# 11.2  JDBC的常用API

3. Connection接口

DriverManager类的getConnection()方法返回了一个Connection对象，Connection对象是表示数据库连接的对象，只有获得该连接对象，才能访问并操作数据库。一个应用程序可与单个数据库建立一个或多个连接，也可以与多个数据库建立连接。Connection接口的常用方法如下所示。

# 11.2  JDBC的常用API

Connection接口的常用方法：

| 方法声明 | 功能描述 |
|---|---|
| createStatement() | 用于创建一个Statement对象，Statement对象可以将SQL语句发送到数据库 |
| prepareStatement(String sql) | 用于创建一个PreparedStatement对象，该对象可以将参数化的动态SQL语句发送到数据库 |
| prepareCall(String sql) | 用于创建一个CallableStatement对象来调用数据库的存储过程 |
| isReadOnly() | 用于查看当前Connection对象的读取模式是否为只读模式 |
| setReadOnly() | 用于设置当前Connection对象的读写模式，默认是非只读模式 |

# 11.2  JDBC的常用API

| 方法声明 | 功能描述 |
|---|---|
| commit() | 使所有上一次提交/回滚后进行的更改成为持久更改，并释放此Connection对象当前持有的所有数据库锁 |
| setAutoCommit(boolean autoCommit) | 设置是否关闭自动提交模式 |
| roolback() | 用于取消在当前事务中进行的所有更改，并释放此Connection对象当前持有的所有数据库锁 |
| close() | 用于立即释放Connection对象的数据库和JDBC资源，而不是等它们被自动释放 |
| isClose() | 用于判断Connection对象是否已被自动关闭 |

# 11.2  JDBC的常用API

4. Statement接口

Statement接口用于执行静态的SQL语句，并返回一个结果对象。Statement接口对象可以通过Connection实例的createStatement()方法获得，该对象会把静态的SQL语句发送到数据库中编译执行，然后返回数据库的处理结果。Statement接口提供了3个常用的执行SQL语句的方法，如下所示。

# 11.2  JDBC的常用API

Statement接口常用的执行SQL语句的方法：

| 方法声明 | 功能描述 |
|---|---|
| execute(String sql) | 用于执行各种SQL语句。该方法返回一个boolean类型的值，如果返回值为true，表示所执行的SQL语句有查询结果，可以通过Statement的getResultSet()方法获得查询结果。 |
| executeUpdate(String sql) | 用于执行SQL中的insert、update和delete语句。该方法返回一个int类型的值，表示数据库中受该SQL语句影响的条数。 |
| executeQuery(String sql) | 用于执行SQL中的select语句。该方法返回一个表示查询结果的ResultSet对象。 |

# 11.2  JDBC的常用API

5. PreparedStatement 接口

PreparedStatement是Statement的子接口，用于执行预编译的SQL语句。PreparedStatement接口扩展了带有参数SQL语句的执行操作，该接口中的SQL语句可以使用占位符?代替参数，然后通过setter方法为SQL语句的参数赋值。PreparedStatement接口提供的常用方法，如下所示。

# 11.2  JDBC的常用API

PreparedStatement接口常用的方法：

| 方法声明 | 功能描述 |
|---|---|
| executeUpdate() | 在PreparedStatement对象中执行 SQL 语句，SQL语句必须是一个DML语句或者是无返回内容的SQL语句，如DDL语句。 |
| executeQuery() | 在PreparedStatement对象中执行SQL查询，该方法返回的是ResultSet对象。 |
| setInt(int parameterIndex, int x) | 将指定参数设置成给定的int值。 |
| setFloat(int index,float f) | 将指定位置的参数设置为float值。 |

# 11.2  JDBC的常用API

在上表中，DML（数据操纵语言）语句指的是操作数据库、表、列等的语句，使用的关键字为CREATE、 ALTER、 DROP。DDL（数据定义语言）语句指的是对表中的数据进行增、删、改操作的语句，使用的关键字为INSERT 、UPDATE、 DELETE。

| 方法声明 | 功能描述 |
|---|---|
| setLong(int index,long l) | 将指定位置的参数设置为long值。 |
| setDouble(int index,double d) | 将指定位置的参数设置为double值。 |
| setBoolean(int index,boolean b) | 将指定位置的参数设置为boolean值。 |
| void setString(int parameterIndex,String x) | 将指定参数设置成给定的String值。 |

# 11.2  JDBC的常用API

6. ResultSet接口

ResultSet接口用于保存JDBC执行查询时返回的结果集，该结果集封装在一个逻辑表格中。在ResultSet接口内部有一个指向表格数据行的游标（或指针），ResultSet对象初始化时，游标在表格的第一行之前，调用next()方法可以将游标移动到下一行。如果下一行没有数据，则next()方法返回false。在应用程序中经常使用next()方法作为while循环的条件来迭代ResultSet结果集。ResultSet接口的常用方法，如下所示。

# 11.2  JDBC的常用API

ResultSet接口常用的方法：

| 方法声明 | 功能描述 |
|---|---|
| getString(int columnIndex) | 用于获取指定字段的String类型的值，参数columnIndex代表字段的索引 |
| getString(String columnName) | 用于获取指定字段的String类型的值，参数columnName代表字段的名称 |
| getInt(int columnIndex) | 用于获取指定字段的int类型的值，参数columnIndex代表字段的索引 |
| getInt(String columnName) | 用于获取指定字段的int类型的值，参数columnName代表字段的名称 |
| absolute(int row) | 将游标移动到结果集的第row条记录 |
| relative(int row) | 按相对行数（正或负）移动游标 |

# 11.2  JDBC的常用API

| 方法声明 | 功能描述 |
|---|---|
| previous() | 将游标从结果集的当前位置移动到上一行 |
| next() | 将游标从结果集的当前位置移动到下一行 |
| beforeFirst() | 将游标移动到结果集的开头（第一行之前） |
| isBeforeFirst() | 判断游标是否位于结果集的开头（第一行之前） |
| afterLast() | 将游标指针移动到结果集的末尾（最后一行之后） |
| isAfterLast() | 判断游标是否位于结果集的末尾（最后一行之后） |
| first() | 将游标移动到结果集的第一行 |
| isFirst() | 判断游标是否位于结果集的第一行 |

# 11.2  JDBC的常用API

从表中可以看出，ResultSet接口中定义了一些getter方法，而采用哪种getter方法获取数据取决于字段的数据类型。程序既可以通过字段的名称来获取指定数据，也可以通过字段的索引来获取指定的数据，字段的索引是从1开始编号的。

| 方法声明 | 功能描述 |
|---|---|
| last() | 将游标移动到结果集的最后一条记录 |
| getRow() | 返回当前记录的行号 |
| getStatement() | 返回生成结果集的Statement对象 |
| close() | 释放当前结果集的数据库和JDBC资源 |

# JDBC编程

11.3

# 11.3.1  JDBC编程步骤

先定一个小目标！

# 11.3.1  JDBC编程步骤

JDBC编程步骤简述

通常情况下,使用JDBC API实现JDBC 程序时,首先需要加载并注册数据库驱动程 序,其次使用 DriverManager类调用getConnection()方法获取表示数据连接的 Connection 对象,最后通过 Connection对象调用相应方法获取Statement对象,通过Statement对象执 行SQL语句。执行SQL语句之后,如果数据库有返回结果,则将结果封装为 ResultSet对象返回。

# 11.3.1  JDBC编程步骤

JDBC编程流程图

使用JDBC的常用API实现JDBC程序的步骤如下所示。

接下来根据流程图，分步骤讲解JDBC程序的编写。

# 11.3.1  JDBC编程步骤

1. 加载并注册数据库驱动程序

在连接数据库之前，要加载数据库的驱动到JVM（Java虚拟机）。加载数据库驱动操作可以通过java.lang.Class类的静态方法forName(String className)或DriverManager类的静态方法registerDriver(Driver driver)实现，具体示例如下所示：

DriverManager.registerDriver(Driver driver);
或
Class.forName("DriverName");

# 11.3.1  JDBC编程步骤

registDriver()和forName()方法分析：

调用registDriver()方法时，其实会创建了两个Driver对象，对于只需加载驱动类来讲有些浪费资源；使用forName()方法的话，驱动程序类的名称是以字符串的形式填写，使用时可以把该驱动类名称放到配置文件中，如果需要切换驱动类会非常方便。所以在实际开发中，常调用forName()方法注册数据库驱动。

# 11.3.1  JDBC编程步骤

forName()方法的参数DriverName：表示数据库的驱动类。

以MySQL数据库为例，MySQL驱动类在MySQL 6.0.2版本之前是com.mysql.jdbc.Driver，加载示例代码如下所示：

forName("com.mysql.jdbc.Driver");

而在MySQL 6.0.2版本之后，MySQL驱动类是com.mysql.cj.jdbc.Driver，加载示例代码如下所示：

forName("com.mysql.cj.jdbc.Driver");

# 11.3.1  JDBC编程步骤

2. 通过DriverManager获取数据库连接

DriverManager类的getConnection()方法用于获取JDBC驱动程序到数据库的连接，通过DriverManager类获取数据库连接的具体方式如下：

Connection conn = DriverManager.getConnection(String url, String user, String pwd);

从上述代码可以看出，getConnection()方法有3个参数，分别表示连接数据库的URL、登录数据库的用户名和登录数据库的密码。

# 11.3.1  JDBC编程步骤

getConnection()方法的参数 数据库连接地址URL书写格式：

以MySQL数据库为例，MySQL数据库地址的书写格式如下所示：

jdbc:mysql://hostname:port/databasename

在上面代码中，jdbc:mysql:是固定的写法，后面的hostname指的是主机的名称，port指的是连接数据库的端口号（MySQL端口号默认为3306），databasename指的是MySQL中相应数据库的名称。

# 11.3.1  JDBC编程步骤

3. 通过Connection对象获取Statement对象

获取Connetction对象之后，还必须要创建一个Statement对象，将各种SQL语句发送到所连接的数据库中执行。如果把Connection对象看作一条连接程序和数据库的索道，那么Statement对象就可以看作是索道上的一辆缆车，它为数据库传输SQL语句，并返回执行结果。

# 11.3.1  JDBC编程步骤

（1）createStatement()：创建基本的Statement对象。
（2）prepareStatement()：根据传递的SQL语句创建PreparedStatement对象。
（3）prepareCall()：根据传入的SQL语句创建CallableStatement对象。

以创建基本的Statement对象为例，创建方式如下：

Statement stmt = conn.createStatement();

Connection创建Statement对象的方法：

# 11.3.1  JDBC编程步骤

4. 使用Statement执行SQL语句

创建了Statement对象后，就可以通过该对象执行SQL语句。如果SQL语句运行后产生了结果集，Statement对象会将结果集封装成ResultSet对象并返回。Statement有以下3个执行SQL语句的方法。
execute()：可以执行任何SQL语句。
executeQuery()：通常执行查询语句，执行后返回代表结果集的ResultSet对象。
executeUpdate()：主要用于执行DML语句和DDL语句。执行DML语句，如INSERT、UPDATE或DELETE时，返回受SQL语句影响的行数；执行DDL语句返回0。

# 11.3.1  JDBC编程步骤

5. 操作结果集

如果执行的SQL语句是查询语句，执行结果将返回一个ResultSet对象，该对象保存了SQL语句查询的结果。程序可以通过操作该ResultSet对象取出查询结果。

# 11.3.1  JDBC编程步骤

6. 关闭连接，释放资源

每次操作数据库结束后都要关闭数据库连接并释放资源，以防止系统资源浪费。资源的关闭顺序和声明顺序相反，关闭顺序依次为关闭结果集对象ResultSet、关闭Statement对象、关闭Connection对象。为了保证在异常情况下也能关闭资源，通常在try...catch语句的finally代码块中统一关闭资源。

# 11.3.2  实现第一个JDBC程序

先定一个小目标！

# 11.3.2  实现第一个JDBC程序

讲解了JDBC程序的大致实现步骤后，下面编写一个JDBC程序，该程序要求从users表中读取数据，并将结果输出到控制台。因为Java中的JDBC是用来连接数据库从而执行相关数据相关操作的，因此在使用JDBC时，一定要确保安装有数据库。常用的关系型数据库有MySQL和Oracle，下面以连接MySQL数据库为例，使用JDBC执行相关操作。程序的具体实现步骤如下所示。

# 11.3.2  实现第一个JDBC程序

（1）搭建数据库环境

在MySQL中创建一个名称为jdbc的数据库，然后在jdbc数据库中创建一个users表，创建数据库和表的SQL语句如下所示：

CREATE DATABASE jdbc;
USE jdbc;
CREATE TABLE users(
		id INT PRIMARY KEY AUTO_INCREMENT,
		name VARCHAR(40),
		password VARCHAR(40),
		email VARCHAR(60),
		birthday DATE 
);

# 11.3.2  实现第一个JDBC程序

jdbc数据库和users表创建成功后，再向users表中插入3条数据，插入的SQL语句如下所示：

INSERT INTO users(NAME,PASSWORD,email,birthday) 
	VALUES('zhangs','123456','zs@sina.com','1980-12-04'),
	('lisi','123456','lisi@sina.com','1981-12-04'),
	('wangwu','123456','wangwu@sina.com','1979-12-04');

# 11.3.2  实现第一个JDBC程序

（2）创建项目环境，导入数据库驱动

在IDEA中新建一个名称为chapter11的Java项目，右击项目名称，在弹出的快捷菜单中选 择 New→Directory命令,在弹出的对话框中将该目录命名为lib,项目根目录中就会出现一 个名称为lib的目录。

# 11.3.2  实现第一个JDBC程序

添加MySQL 的JAR包：

将下载好的Jar包复制到项目的lib目录中，并把Jar包添加到项目里。在IDEA菜单栏单击File，选择“Project Structure”→
“Modules”→“Dependencies”，单击最右侧加号后选择第一项：JARs or directories…，在弹出框中选择下载好的Jar包确认。最后可以看到mysql-connector-java-8.0.15.jar包添加到IDEA的依赖项中。

# 11.3.2  实现第一个JDBC程序

加入数据库驱动后的项目结构：

在上图中，mysql-connector-java-8.0.15.jar包添加到依赖项之后，单击“Apply”按钮后再单击“OK”按钮，可以看到在External libraries下已经存在刚刚添加的jar包。至此，Jar包添加成功。可以从右边的图中查看加入数据库驱动后的项目结构。

# 11.3.2  实现第一个JDBC程序

案例演示：（3）编写JDBC程序

在项目chapter11的src目录下，新建一个名称为com.itheima.jdbc.example的包，在该包中创建类Example01，Example01类用于读取数据库中的users表，并将结果输出到控制台。具体实现步骤如下所示。

# 11.3.2  实现第一个JDBC程序

步骤一：注册数据库驱动，通过DriverManager获取数据库连接，通过Connection对象获取Statement对象。代码如下所示：

Statement stmt = null;
ResultSet rs = null;
Connection conn = null; 
// 1. 注册数据库的驱动
 Class.forName("com.mysql.cj.jdbc.Driver");
 // 2.通过DriverManager获取数据库连接
 String url = "jdbc:mysql://localhost:3306/jdbc"+
 		"?serverTimezone=GMT%2B8&useSSL=false";
 String username = "root";    //数据库用户名
 String password = "root";    //数据库密码
 conn = DriverManager.getConnection(url, username, password);
 // 3.通过Connection对象获取Statement对象
 stmt = conn.createStatement();

# 11.3.2  实现第一个JDBC程序

步骤二：使用Statement执行SQL语句，操作ResultSet结果集。代码如下所示：

// 4.使用Statement执行SQL语句
 String sql = "select * from users";
 rs = stmt.executeQuery(sql);
 // 5. 操作ResultSet结果集
 System.out.println("id	|  name  |  password  |  email  |  birthday");
 while (rs.next()) {
 int id = rs.getInt("id"); // 通过列名获取指定字段的值
 String name = rs.getString("name");
 String psw = rs.getString("password"); 
 String email = rs.getString("email");
 Date birthday = rs.getDate("birthday");
 System.out.println(id + "  |  " + name + "  |	" + psw +
 	"  |  " + email + "  |  " + birthday);
 }

# 11.3.2  实现第一个JDBC程序

步骤三：回收数据库资源。代码如下所示：

// 6.回收数据库资源
 if (rs != null) {
 try {
 	rs.close();
 } catch (SQLException e) {e.printStackTrace();}
 rs = null;
 }
 if (stmt != null) {
 try {
 	stmt.close();
 } catch (SQLException e) {e.printStackTrace();}
 stmt = null;
 }
 if (conn != null) {
 try {
 	conn.close();
 } catch (SQLException e) {e.printStackTrace();}
 conn = null;
 }

# 11.3.2  实现第一个JDBC程序

步骤四：定义main()方法，定义try...catch...finally代码块，把步骤一和步骤二的代码写在try{}块中，把步骤三的代码写在finally块中。

# 11.3.2  实现第一个JDBC程序

运行代码，控制台显示的运行结果如下图所示。

从图中可以看到，users表中的数据已被输出到了控制台。至此，第一个JDBC程序实现成功。

# 11.3.2  实现第一个JDBC程序

实现JDBC入门程序时的注意事项：

1. 注册驱动程序
虽然使用DriverManager.registerDriver(new com.mysql.cj.jdbc.Driver())方法也可以完成注册，但这种方式会使数据库驱动被注册两次。因为在Driver类的源码中，已经在静态代码块中完成了数据库驱动的注册。为了避免数据库驱动被重复注册，在程序中使用Class.forName()方法加载驱动类即可。

# 11.3.2  实现第一个JDBC程序

2. 释放资源
由于数据库资源非常宝贵，数据库允许的并发访问连接数量有限，因此，当数据库资源使用完毕后，一定要释放资源。为了保证资源的释放，在Java程序中应该将释放资源的操作放在finally代码块中。

# 11.3.2  实现第一个JDBC程序

3. 获取数据库连接
在 MySQL8.0及以上版本中获取数据库连接时需要设置时区为北京时间(serverTimezone=GMT%2B8)，因为安装数据库时默认为美国时间。如果不设置时区为北京时间，系统会报MySQL设置时区与当前电脑系统时区不符的错误，报错信息如下图所示。

# 11.3.2  实现第一个JDBC程序

MySQL高版本需要指明是否进行SSL连接，否则会出现警告信息。警告信息具体如下所示。

Fri Mar 20 18:55:47 CST 2020 WARN: Establishing SSL connection without server's identity verification is not recommended. According to MySQL 5.5.45+, 5.6.26+ and 5.7.6+ requirements SSL connection must be established by default if explicit option isn't set. For compliance with existing applications not using SSL the verifyServerCertificate property is set to 'false'. You need either to explicitly disable SSL by setting useSSL=false, or set useSSL=true and provide truststore for server certificate verification.

url=jdbc:mysql://127.0.0.1:3306/jdbc?characterEncoding=utf8&useSSL=true

遇到上述出现警告信息的情况，只需要在MySQL连接字符串url中加useSSL=true
或者useSSL=false即可，具体示例如下所示：

# 脚下留心

MySQL数据库编码问题

数据库和表创建成功后，如果使用的是命令行窗口向tb_user表中插入带有中文的数据，命令行窗口可能会报错，同时从MySQL数据库查询带有中文数据还可能会显示乱码，这是因为MySQL数据库默认使用的是UTF-8编码格式，而命令行窗口默认使用的是GBK编码格式，所以执行带有中文数据的插入语句会出现解析错误。为了在命令行窗口也能正常向MySQL数据库插入中文数据，以及查询中文数据，可以在执行插入语句和查询语句前，先在命令行窗口执行以下两条命令：

set character_set_client=gbk;
set character_set_results=gbk;

执行完上述两条命令后，再次在命令行窗口执行插入和查询操作就不再出现乱码问题了。

# 本章小结

本章主要讲解了JDBC的基本知识，包括什么是JDBC、JDBC的主要类和接口、JDBC的入门程序。通过本章的学习，读者可以了解到什么是JDBC，熟悉JDBC的主要类和接口，掌握如何使用JDBC操作数据库中的数据。

本

章

小

结
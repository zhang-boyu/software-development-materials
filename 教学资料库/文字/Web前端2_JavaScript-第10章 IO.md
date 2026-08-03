# 第10章  I/O

Java基础入门（第3版）

# 学习目标/Target

# 学习目标/Target

# 章节概述/ Summary

IO操作主要是指使用Java程序完成输入（Input）、输出（Output）操作。所谓输入是指将文件内容以数据流的形式读取到内存中，输出是指通过Java程序将内存中的数据写入到文件中，输入、输出操作在实际开发中应用较为广泛。本章将针对IO的相关操作进行讲解。

# 目录/Contents

# File类

10.1

# 10.1.1  创建File对象

先定一个小目标！

# 10.1.1  创建File对象

File类的构造方法

File类提供了多个构造方法用于创建File对象，具体如下表所示。

| 方法声明 | 功能描述 |
|---|---|
| File(String pathname) | 通过指定的一个字符串类型的文件路径来创建一个新的File对象 |
| File(String parent,String child) | 根据指定的一个字符串类型的父路径和一个字符串类型的子路径（包括文件名称）创建一个File对象 |
| File(File parent,String child) | 根据指定的File类的父路径和字符串类型的子路径（包括文件名称）创建一个File对象 |

# 10.1.1  创建File对象

案例演示

下面通过一个案例演示如何使用File类的构造方法创建File对象。具体代码如下所示。

import java.io.File;
 public class Example01 {
     public static void main(String[] args) {
         File f = new File("D:\\file\\a.txt");     //使用绝对路径创建File对象
         File f1 = new File("src\\Hello.java"); //使用相对路径创建File对象
        System.out.println(f);
        System.out.println(f1);
    }
}

# 10.1.1  创建File对象

注意：
       案例在创建File对象时传入的路径使用了\\，这是因为Windows中的目录符号为反斜线\，但反斜线\在Java中是特殊字符，具有转义作用，所以使用反斜线\时，前面应该再添加一个反斜线，即为\\。此外，目录符号还可以用正斜线/表示，如“D:/file/a.txt”。

# 10.1.1  创建File对象

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 10.1.2  File类的常用方法

先定一个小目标！

# 10.1.2  File类的常用方法

File类的常用方法

File类提供了一系列方法，用于操作File类对象内部封装的路径指向的文件或者目录。具体如下表所示。

| 方法声明 | 功能描述 |
|---|---|
| boolean exists() | 判断File对象对应的文件或目录是否存在，若存在则返回true，否则返回false |
| boolean delete() | 删除File对象对应的文件或目录，若删除成功则返回true，否则返回false |
| boolean createNewFile() | 当File对象对应的文件不存在时，该方法将新建一个文件，若创建成功则返回true，否则返回false |
| String getName() | 返回File对象表示的文件或文件夹的名称 |
| String getPath() | 返回File对象对应的路径 |

# 10.1.2  File类的常用方法

| 方法声明 | 功能描述 |
|---|---|
| String getAbsolutePath() | 返回File对象对应的绝对路径(在Unix/Linux等系统上，如果路径是以正斜线/开始，则这个路径是绝对路径；在Windows等系统上，如果路径是从盘符开始，则这个路径是绝对路径) |
| String getParentFile() | 返回File对象对应目录的父目录(即返回的目录不包含最后一级子目录) |
| boolean canRead() | 判断File对象对应的文件或目录是否可读，若可读则返回true，反之返回false |
| boolean canWrite() | 判断File对象对应的文件或目录是否可写，若可写则返回true，反之返回false |
| boolean isFile() | 判断File对象对应的是否是文件(不是目录)，若是文件则返回true，反之返回false |

# 10.1.2  File类的常用方法

| 方法声明 | 功能描述 |
|---|---|
| boolean isDirectory() | 判断File对象对应的是否是目录(不是文件)，若是目录则返回true，反之返回false |
| boolean isAbsolute() | 判断File对象对应的文件或目录是否是绝对路径 |
| long lastModified() | 返回1970年1月1日0时0分0秒到文件最后修改时间的毫秒值 |
| long length() | 返回文件内容的长度（单位是字节） |
| String[] list() | 递归列出指定目录的全部内容（包括子目录与文件），只是列出名称 |
| File[] listFiles() | 返回一个包含了File对象所有子文件和子目录的File数组 |

# 10.1.2  File类的常用方法

案例演示

下面通过一个案例演示如何使用File类的常用方法。具体代码如下所示。

import java.io.File;
 public class Example02 {
     public static void main(String[] args) {
         File file = new File("src/test.txt");
         System.out.println("文件是否存在："+file.exists());
         System.out.println("文件名："+file.getName());
         System.out.println("文件大小："+file.length()+"bytes");
         System.out.println("文件相对路径："+file.getPath());
         System.out.println("文件绝对路径："+file.getAbsolutePath());
         System.out.println("文件的父级对象是否为文件："+file.isFile());
         System.out.println("文件删除是否成功："+file.delete());
     }
 }

# 10.1.2  File类的常用方法

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 多学一招

createTempFile()方法和deleteOnExit()方法

在一些特定情况下，程序需要读写一些临时文件，为此，File类提供了createTempFile()方法和deleteOnExit()方法，用于操作临时文件。createTempFile()方法用于创建一个临时文件， deleteOnExit()方法在JVM退出时自动删除临时文件。

# 多学一招

createTempFile()方法和deleteOnExit()方法

案例演示

下面通过一个案例演示如何使用File类的常用方法。具体代码如下所示。

import java.io.File;
 import java.io.IOException;
 public class Example03 {
     public static void main(String[] args) throws IOException {
         // 提供临时文件的前缀和后缀
         File f = File.createTempFile("itcast-", ".txt");
         f.deleteOnExit(); // JVM退出时自动删除文件f
         System.out.println("f是否为文件："+f.isFile());
         System.out.println("f的相对路径："+f.getPath());
     }
 }

# 多学一招

createTempFile()方法和deleteOnExit()方法

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 10.1.3  遍历目录下的文件

先定一个小目标！

# 10.1.3  遍历目录下的文件

目录下文件的遍历方式

通过调用File类中的list()方法，可以遍历目录下的文件。按照调用方法的不同，目录下的文件遍历可分为以下3种方式。
(1)遍历指定目录下的所有文件。 
(2)遍历指定目录下指定扩展名的文件。
(3)遍历包括子目录中的文件在内的所有文件。

# 10.1.3  遍历目录下的文件

1. 遍历指定目录下的所有文件

File类的list()方法可以遍历指定目录下的所有文件，下面通过一个案例演示如何使用list()方法遍历目录下的所有文件。具体实现代码如下所示。

import java.io.File;
public class Example04 {
    public static void main(String[] args) throws Exception {
        // 创建File对象
        File file = new File("E:\\Java学科资料汇总（保密）\\Java学科\\18_《Java"
                              +"基础入门》第三版教材\\3.案例文件\\chapter10\\src");
        if (file.isDirectory()) {           // 判断File对象对应的目录是否存在
            String[] names = file.list (); // 获得目录下的所有文件的文件名
            for (String name : names) {
                System.out.println(name);	   // 输出文件名
            }
        }
    }
}

# 10.1.3  遍历目录下的文件

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 10.1.3  遍历目录下的文件

2. 遍历指定目录下指定拓展名的文件

有时程序需要获取指定类型的文件，如获取指定目录下所有的“.java”文件。针对这种需求，File类提供了一个重载的list()方法，该方法接收一个FilenameFilter类型的参数。FilenameFilter是一个接口，被称作文件过滤器，其中定义了一个抽象方法accept()用于依次对指定File的所有子目录或文件进行迭代。在调用list()方法时，需要实现文件过滤器FilenameFilter，并在accept()方法中进行筛选，从而获得指定类型的文件。

# 10.1.3  遍历目录下的文件

案例演示：遍历目录下的文件

下面通过一个案例演示如何遍历指定目录下所有扩展名为“.java”的文件。具体步骤如下。

# 10.1.3  遍历目录下的文件

步骤一：创建Example05类，定义main()方法，在main()方法中创建File对象，然后创建过滤器对象，实现accept()方法。代码如下所示：

// 创建File对象
         File file = new File("E:\\Java学科资料汇总（保密）\\Java学科\\18_《Java"
                             +"基础入门》第三版教材\\3.案例文件\\chapter10\\src");
         // 创建过滤器对象
         FilenameFilter filter = new FilenameFilter() {
             // 实现accept()方法
             public boolean accept(File dir, String name) {
                 File currFile = new File(dir, name);
                 // 如果文件名以.java结尾返回true，否则返回false
                 if (currFile.isFile() && name.endsWith(".java")) {
                     return true;
                 } else {
                     return false;
                 }
             }
         };

# 10.1.3  遍历目录下的文件

步骤二：在main()方法中添加，判断File对象对应的目录是否存在，获得过滤后的所有文件名数组，然后遍历数组，输出文件名。代码如下所示：

if (file.exists()) { // 判断File对象对应的目录是否存在
             String[] lists = file.list(filter); // 获得过滤后的所有文件名数组
             for (String name : lists) {
                 System.out.println(name);
             }
         }

# 10.1.3  遍历目录下的文件

案例运行结果：运行代码，控制台显示的运行结果如下图所示。

# 10.1.3  遍历目录下的文件

3. 遍历包括子目录文件的所有文件

有时候在一个目录下，除了文件还有子目录，如果想获取所有子目录下的文件，list()方法显然不能满足要求，这时可以使用File类提供的另一个方法listFiles()。listFiles()方法返回一个File对象数组，当对数组中的元素进行遍历时，如果元素中还有子目录需要遍历，则可以使用递归再次遍历子目录。

# 10.1.3  遍历目录下的文件

案例演示：下面通过一个案例演示包括子目录文件的所有文件的遍历。具体代码如下所示。

public class Example06 {
     public static void main(String[] args) {
         // 创建一个代表目录的File对象
         File file = new File("E:\\Java学科资料汇总（保密）\\Java学科\\18_《Java"
                                +"基础入门》第三版教材\\3.案例文件\\chapter10");
         fileDir(file);	// 调用FileDir方法
     }
     public static void fileDir(File dir) {
         File[] files = dir.listFiles();   // 获得表示目录下所有文件的数组
         for (File file : files) {		 // 遍历所有的子目录和文件
             if (file.isDirectory()) {
                 fileDir(file);	 	// 如果是目录，递归调用fileDir()
             }
             System.out.println(file.getAbsolutePath()); // 输出文件的绝对路径
         }
     }
 }

# 10.1.3  遍历目录下的文件

案例运行结果：运行代码，控制台显示的运行结果如下图所示。

# 10.1.4  删除文件及目录

先定一个小目标！

# 10.1.4  删除文件及目录

删除文件及目录

在操作文件时，可能会遇到需要删除一个目录下的某个文件或者删除整个目录的情况，这时可以调用File类的delete()方法。

# 10.1.4  删除文件及目录

案例一演示：下面通过一个案例演示调用delete()方法删除文件或文件夹。具体代码如下所示。

import java.io.*;
 public class Example07 {
 	public static void main(String[] args) {
 		File file = new File("D:\\hello");
 		if (file.exists()) {
 			System.out.println(file.delete());
 		}
 	}
 }

# 10.1.4  删除文件及目录

案例一运行结果：运行代码，控制台显示的运行结果如下图所示。

# 10.1.4  删除文件及目录

案例一运行结果分析：

上图的运行结果中为false，这说明文件删除失败了。原因是File类的delete()方法只能删除一个指定的文件，假如File对象代表目录，并且目录下包含子目录或文件，则File类的delete()方法不允许直接删除这个目录。在这种情况下，需要通过递归的方式将整个目录以及目录中的文件全部删除。

# 10.1.4  删除文件及目录

案例二演示：递归删除包含子文件的目录

下面修改案例一，递归删除包含子文件的目录。具体步骤如下。

# 10.1.4  删除文件及目录

步骤一：创建递归删除的方法deleteDir()，遍历所有的子目录和文件，进行递归删除。具体代码如下所示。

public static void deleteDir(File dir) {
           if (dir.exists()) {                       // 判断传入的File对象是否存在
	File[] files = dir.listFiles();    // 得到File数组
	for (File file : files) { // 遍历所有的子目录和文件
 		if (file.isDirectory()) {
 		          deleteDir(file); // 如果是目录，递归调用deleteDir()
 		 } else {
 		           // 如果是文件，直接删除
 		           file.delete();
 		 }
 	 }
 	 // 删除完一个目录里的所有文件后，就删除这个目录
 	 dir.delete();
           }
}

# 10.1.4  删除文件及目录

步骤二：创建Example08类，定义main()方法，创建File对象，调用步骤一中的deleteDir删除方法。具体代码如下所示。

public class Example08 {
         public static void main(String[] args) {
	File file = new File("D:\\hello");
	deleteDir(file);         // 调用deleteDir删除方法
         	System.out.println("删除成功!");
         }
}

# 10.1.4  删除文件及目录

案例二运行结果：运行代码，控制台显示的运行结果如下图所示。

注意：删除目录是从JVM直接删除而不放入回收站，文件一旦删除就无法恢复，因此在进行文件删除操作的时候需要格外小心。

# 字节流

10.2

# 10.2.1  字节流的概念

先定一个小目标！

# 10.2.1  字节流的概念

字节流的概念介绍

在程序的开发中，经常需要处理设备之间的数据传输，而计算机中，无论是文本、图片、音频还是视频，所有文件都是以二进制（字节）形式存在的。对于字节的输入输出，I/O流提供了一系列的流，统称为字节流，字节流是程序中最常用的流，根据数据的传输方向可将其分为字节输入流和字节输出流。

# 10.2.1  字节流的概念

抽象类InputStream和OutputStream

JDK提供了两个抽象类InputStream和OutputStream，它们是字节流的顶级父类，所有的字节输入流都继承自InputStream，所有的字节输出流都继承自OutputStream。为了方便理解，可以把InputStream和OutputStream比作两根“水管”，具体如下：

# 10.2.1  字节流的概念

抽象类InputStream和OutputStream

在左图中，InputStream被看成一个输入管道，OutputStream被看成一个输出管道，数据通过InputStream从源设备输入到程序，通过OutputStream从程序输出到目标设备，从而实现数据的传输。由此可见，I/O流中的输入输出都是相对于程序而言的。

# 10.2.1  字节流的概念

InputStream类的常用方法

InputStream类提供了一系列与读数据相关的方法。具体如下表所示。

| 方法声明 | 功能描述 |
|---|---|
| int read() | 从输入流读取一个8位的字节，把它转换为0~255之间的整数，并返回这一整数 |
| int read(byte[] b) | 从输入流读取若干字节，把它们保存到参数b指定的字节数组中，返回的整数表示读取字节的数目 |
| int read(byte[] b,int off,int len) | 从输入流读取若干字节，把它们保存到参数b指定的字节数组中，off指定字节数组开始保存数据的起始索引，len表示读取的字节数目 |
| void close() | 关闭此输入流并释放与该流关联的所有系统资源 |

# 10.2.1  字节流的概念

InputStream体系结构

InputStream类虽然提供了一系列和读数据有关的方法，但是InputStream类是抽象类，不能被实例化，因此针对不同的功能，InputStream类提供了不同的子类，这些子类形成了一个体系结构。如下图所示。

# 10.2.1  字节流的概念

OutputStream类的常用方法

OutputStream类提供了一系列与写数据相关的方法。具体如下表所示。

| 方法声明 | 功能描述 |
|---|---|
| void write(int b) | 向输出流写入一个字节 |
| void write(byte[] b) | 把参数b指定的字节数组的所有字节写到输出流 |
| void write(byte[] b,int off,int len) | 将指定byte数组中从偏移量off开始的len个字节写入输出流 |
| void flush() | 刷新此输出流并强制写出所有缓冲的输出字节 |
| void close() | 关闭此输出流并释放与此流相关的所有系统资源 |

# 10.2.1  字节流的概念

OutputStream体系结构

OutputStream类虽然提供了一系列和写数据有关的方法，但是OutputStream类是抽象类，不能被实例化，因此针对不同的功能，OutputStream类提供了不同的子类，这些子类形成了一个体系结构。如下图所示。

# 10.2.2  字节流读文件

先定一个小目标！

# 10.2.2  字节流读文件

字节流FileInputStream

InputStream就是JDK提供的基本输入流，它是所有输入流的父类，FileInputStream是InputStream的子类，它是操作文件的字节输入流，专门用于读取文件中的数据。

# 10.2.2  字节流读文件

案例准备

在实现案例之前，首先在Java项目的根目录下创建一个文本文件test.txt，在文件中输入内容“itcast”并保存；然后使用字节输入流对象来读取test.txt文本文件。

# 10.2.2  字节流读文件

案例代码

public class Example09 {
 	public static void main(String[] args) throws Exception {
 		// 创建一个文件字节输入流，并指定源文件名称
 		FileInputStream in = new FileInputStream("test.txt");
 		int b = 0;  // 定义一个int类型的变量b，记住每次读取的一个字节
 		while (true) {
 			b = in.read(); // 变量b记住读取的一个字节
 			if (b == -1) { // 如果读取的字节为-1，跳出while循环
 				break;
 			}
 			System.out.println(b); // 否则将b写出
 		}
 		in.close();
 	}
 }

下面通过一个案例实现字节流对文件数据的读取。具体代码如下所示。

# 10.2.2  字节流读文件

代码运行结果

运行代码，控制台显示的运行结果如下图所示。

# 10.2.2  字节流读文件

代码运行结果分析

由上图可知，控制台打印的结果分别为105、116、99、97、115和116。在本章的开头我们讲过，计算机中的数据都是以字节的形式存在的。在test.txt文件中，字符‘i’‘t’‘c’‘a’‘s’‘t’各占一个字节，所以最终结果显示的就是文件test.txt中的六个字节所对应的十进制数。

# 10.2.2  字节流读文件

文件读取发生错误处理方法

有时，在文件读取的过程中可能会发生错误。例如，文件不存在导致无法读取，或者用户没有读取权限等，这些错误都由JVM自动封装成IOException异常并抛出。如果文件读取过程中发生了IO错误，InputStream就无法正常关闭，资源也无法及时释放，这样会造成资源浪费。对此，可以使用try…finally保证InputStream在任何情况下都能够正确关闭。

# 10.2.2  字节流读文件

public static void main(String[] args) throws Exception {
        InputStream input =null;
        try {
        	// 创建一个文件字节输入流
        	FileInputStream in = new FileInputStream("test.txt");
        	int b = 0;           // 定义一个int类型的变量b，记住每次读取的一个字节
        	while (true) {
            		b = in.read(); // 变量b记住读取的一个字节
            		if (b == -1) { // 如果读取的字节为-1，跳出while循环
                		break;
            	}
            	System.out.println(b); // 否则将b写出
        }
        } finally {
            	if (input != null) {
                		input.close();
            	}
        }
    }

修改案例，将读取文件的代码放入try语句块中，将关闭输入流的代码放入finally语句块中，具体代码如下所示。

# 10.2.3  字节流写文件

先定一个小目标！

# 10.2.3  字节流写文件

字节流FileOutputStream

OutputStream是JDK提供的最基本的输出流，与InputStream类似，OutputStream也是抽象类，它是所有输出流的父类。OutputStream是一个抽象类，如果使用此类，则必须先通过子类实例化对象。OutputStream类有多个子类，其中FileOutputStream子类是操作文件的字节输出流，专门用于把数据写入文件。

# 10.2.3  字节流写文件

案例代码

import java.io.*;
public class Example10{
 	public static void main(String[] args) throws Exception {
 		// 创建一个文件字节输出流，并指定输出文件名称
 		OutputStream out = new FileOutputStream("example.txt");
 		String str = "传智教育";
 		byte[] b = str.getBytes();
 		for (int i = 0; i < b.length; i++) {
 			out.write(b[i]);
 		}
 		out.close();
 	}
}

下面通过一个案例演示如何使用FileOutputStream将数据写入文件。具体代码如下所示。

# 10.2.3  字节流写文件

代码运行结果

运行代码，运行结果如下图所示。

由图可知，使用FileOutputStream写数据时，程序自动创建了文件example.txt，并将数据写入example.txt文件。注意：如果通过FileOutputStream向一个已经存在的文件中写入数据，那么该文件中的数据会被覆盖。

# 10.2.3  字节流写文件

在已存在的文件中追加内容

若希望在已存在的文件内容之后追加新内容，则可使用FileOutputStream的构造函数
FileOutputStream(String fileName, boolean append)创建文件输出流对象，并把append 参数的值设置为true。

# 10.2.3  字节流写文件

案例代码

public class Example11{
	public static void main(String[] args) throws Exception {
          		//创建文件输出流对象，并指定输出文件名称和开启文件内容追加功能
		OutputStream out = new FileOutputStream("example.txt ", true);
		String str = "欢迎你!";
        		 //将字符串存入byte类型的数组中
		byte[] b = str.getBytes();
		for (int i = 0; i < b.length; i++) {
			out.write(b[i]);
		}
		out.close();
	}
}

下面通过一个案例演示文件内容的追加。具体代码如下所示。

# 10.2.3  字节流写文件

代码运行结果

运行代码，运行结果如下图所示。

由图可知，程序通过字节输出流对象out向文件example.txt写入“欢迎你!”后，并没有将文件之前的数据清空，而是将新写入的数据追加到了文件的末尾。

# 10.2.3  字节流写文件

注意：
       I/O流在进行数据读写操作时会出现异常，为了代码的简洁，在InputStream读文件和OutputStream写文件的程序中都使用了throws关键字将异常抛出。然而一旦遇到IO异常，I/O流的close()方法将无法得到执行，流对象所占用的系统资源将得不到释放，因此，为了保证I/O流的close()方法必须执行，通常将关闭流的操作写在finally代码块中，具体代码请参考10.2.2小节。

# 10.2.4  文件的复制

先定一个小目标！

# 10.2.4  文件的复制

文件复制

在应用程序中，I/O流通常都是成对出现的，即输入流和输出流一起使用。例如，文件的复制就需要通过输入流读取文件中的数据，再通过输出流将数据写入文件。

# 10.2.4  文件的复制

案例准备

首先在chapter10项目的根目录下创建source文件夹和target文件夹，然后在source文件夹中存放一个a.png文件，最后将source文件夹下的a.png复制到target文件夹下并重新命名为b.png。

# 10.2.4  文件的复制

案例代码

// 创建一个字节输入流，用于读取当前目录下source文件夹中的a.png文件
InputStream in = new FileInputStream("source/a.png");
// 创建一个文件字节输出流，用于将读取的数据写入target目录下的文件中
OutputStream out = new FileOutputStream("target/b.png");
int len; // 定义一个int类型的变量len，记住每次读取的一个字节
// 获取复制文件前的系统时间
long begintime = System.currentTimeMillis();
while ((len = in.read()) != -1) { // 读取一个字节并判断是否读到文件末尾
 	out.write(len); // 将读到的字节写入文件
}
// 获取文件复制结束时的系统时间
long endtime = System.currentTimeMillis();
System.out.println("复制文件所消耗的时间是：" + (endtime - begintime) + "毫秒");
in.close();
out.close();

创建Example12类，定义main()方法，文件复制代码如下。

# 10.2.4  文件的复制

代码运行结果

运行代码，控制台显示的运行结果如下图所示。

# 10.2.4  文件的复制

文件复制结果

运行结束后，打开target文件夹，发现source文件夹中的a.png文件被成功复制到了target文件夹，如下图所示。

# 10.2.4  文件的复制

案例实现的文件复制是一个字节一个字节的读写，需要频繁的操作文件，效率非常低。这就好比从北京运送烤鸭到上海，如果有一万只烤鸭，每次运送一只，就必须运输一万次，这样的效率显然非常低。为了减少运输次数，可以先把一批烤鸭装在车厢中，这样就可以成批的运送烤鸭，这时的车厢就相当于一个临时缓冲区。在通过流的方式复制文件时，为了提高效率也可以定义一个字节数组作为缓冲区。在复制文件时，可以一次性读取多个字节的数据，并保存在字节数组中，然后将字节数组中的数据一次性写入文件。程序中的缓冲区就是一块内存，该内存主要用于存放暂时输入输出的数据，由于使用缓冲区减少了对文件的操作次数，所以可以提高数据的读写效率。

# 10.2.4  文件的复制

案例代码

// 创建一个字节输入流，用于读取当前目录下source文件夹中的文件a.png
InputStream in = new FileInputStream("source/a.png");
// 创建一个文件字节输出流，用于将读取的数据写入当前目录的target文件中
OutputStream out = new FileOutputStream("target/a.png");
// 以下是用缓冲区读写文件
byte[] buff = new byte[1024];	// 定义一个字节数组，作为缓冲区
// 定义一个int类型的变量len记住读取读入缓冲区的字节数
int len;
long begintime = System.currentTimeMillis();
while ((len = in.read(buff)) != -1) { // 判断是否读到文件末尾
	out.write(buff, 0, len);  // 从第一个字节开始，向文件写入len个字节
}
long endtime = System.currentTimeMillis();
System.out.println("复制文件所消耗的时间是：" + (endtime - begintime) + "毫秒");
in.close();
out.close();

创建Example13类，定义main()方法，利用缓冲区文件复制代码如下。

# 10.2.4  文件的复制

代码运行结果

运行代码，控制台显示的运行结果如下图所示。

通过比较，可以看出使用缓冲区复制文件所消耗的时间明显减少了，这说明使用缓冲区读写文件可以有效的提高程序的读写效率。

# 字符流

10.3

# 10.3.1  字符流定义及基本用法

先定一个小目标！

# 10.3.1  字符流定义及基本用法

字符流的介绍

前面讲解内容都是通过字节流直接对文件进行读写，如果读写的文件内容是字符，考虑到使用字节流读写字符可能存在传输效率以及数据编码问题，此时建议使用字符流。同字节流一样，字符流也有两个抽象的顶级父类，分别是Reader类和Writer类。其中Reader类是字符输入流，用于从某个源设备读取字符。Writer类是字符输出流，用于向某个目标设备写入字符。

# 10.3.1  字符流定义及基本用法

Reader类的常用方法

Reader类提供了一系列与读数据相关的方法。具体如下表所示。

| 方法声明 | 功能描述 |
|---|---|
| int read() | 以字符为单位读数据 |
| int read(char cbuf[]) | 将数据读入char类型数组，并返回数据长度 |
| int read(char cbuf[],int off,int len) | 将数据读入char类型数组的指定区间，并返回数据长度 |
| void close() | 关闭数据流 |
| long transferTo(Writer out) | 将数据直接读入字符输出流 |

# 10.3.1  字符流定义及基本用法

Reader体系结构

Reader类作为字符流的顶级父类，也有许多子类，下面通过一张继承关系图列举Reader类的常用子类。如下图所示。

# 10.3.1  字符流定义及基本用法

Writer类的常用方法

Writer类提供了一系列与写数据相关的方法。具体如下表所示。

| 方法声明 | 功能描述 |
|---|---|
| void write(int c) | 以字符为单位写数据 |
| void write(char cbuf[]) | 将char类型数组中的数据写出 |
| void write(char cbuf[],int off,int len) | 将char类型数组中指定区间的数据写出 |
| void write(String str) | 将String类型的数据写出 |
| void wirte(String str,int off,int len) | 将String类型指定区间的数据写出 |
| void flush() | 可以强制将缓冲区的数据同步到输出流中 |
| void close() | 关闭数据流 |

# 10.3.1  字符流定义及基本用法

Writer体系结构

Writer类作为字符流的顶级父类，也有许多子类，下面通过一张继承关系图列举Writer类的常用子类。如下图所示。

# 10.3.2  字符流读文件

先定一个小目标！

# 10.3.2  字符流读文件

字符流FileReader

在程序开发中，经常需要对文本文件的内容进行读取，如果想从文件中直接读取字符便可以使用字符输入流FileReader，通过此流可以从关联的文件中读取一个或一组字符。

# 10.3.2  字符流读文件

下面通过一个案例学习如何使用FileReader读取文件中的字符。

首先在chapter10项目的根目录下新建文本文件src.txt并在文件中输入“hello itcast”；
其次在src文件夹中创建一个名称为Example16的类。在Example16类中创建字节输入流FileInputStream对象读取src.txt文件中的内容，并将字节输入流转换成字符输入流；
然后创建一个字节输出流对象，并指定目标文件为des.txt，最后将字节输出流转换成字符输出流将字符输出到文件中。

# 10.3.2  字符流读文件

代码运行结果

运行代码，控制台显示的运行结果如下图所示。

# 10.3.3  字符流写文件

先定一个小目标！

# 10.3.3  字符流写文件

字符流FileWriter

在程序开发中，有时需要向文本文件写入内容，通过字符流向文本文件写入内容需要使用FileWriter类，FileWriter类可以一次向文件中写入一个或一组字符。

# 10.3.3  字符流写文件

案例代码

import java.io.*;
public class Example15 {
	public static void main(String[] args) throws Exception {
		// 创建一个FileWriter对象用于向文件中写入数据
		FileWriter writer = new FileWriter("writer.txt");
		String str = "你好，传智教育";
		writer.write(str);  // 将字符数据写入到文本文件中
		writer.write("\r\n");  // 将输出语句换行
		writer.close(); // 关闭写入流，释放资源
	}
}

下面通过一个案例学习如何使用FileWriter字符流将字符写入文件。具体代码如下所示。

# 10.3.3  字符流写文件

代码运行结果

运行代码，运行结果如下图所示。

# 10.3.3  字符流写文件

在已存在的文件中追加内容

FileWriter同FileOutputStream一样，如果指定的文件不存在，就会先创建文件，再写入数据，如果文件存在，则原文件内容会被覆盖。如果想在文件末尾追加数据，同样需要调用重载的构造方法。将案例中的第5行代码进行如下修改。再次运行程序，即可实现在文件中追加内容的效果。

FileWriter writer = new FileWriter("writer.txt",true);

# 转换流

10.4

# 10.4  转换流

先定一个小目标！

# 10.4  转换流

转换流的介绍

I/O流分为字节流和字符流，字节流和字符流之间可以进行转换。JDK提供了两个类用于将字节流转换为字符流，它们分别是InputStreamReader和OutputStreamWriter，也称为转换流，其作用如下所示。
（1）InputStreamReader是Reader的子类，它可以将一个字节输入流转换成字符输入流，
        方便直接读取字符。
（2）OutputStreamWriter是Writer的子类，它可以将一个字节输出流转换成字符输出流， 
        方便直接写入字符。

# 10.4  转换流

案例代码

public static void main(String[] args) throws Exception {
        // 创建一个字节输入流in，并指定源文件为src.txt
        FileInputStream in = new FileInputStream("src.txt");
        // 将字节输入流in转换成字符输入流isr
        InputStreamReader isr = new InputStreamReader(in);
        // 创建一个字节输出流对象out，并指定目标文件为des.txt
        FileOutputStream out = new FileOutputStream("des.txt");
      // 将字节输出流out转换成字符输出流osw
      OutputStreamWriter osw = new OutputStreamWriter(out);
      int ch; // 定义一个变量用于记录读取的字符
      while ((ch = isr.read()) != -1) { 	// 循环判断是否读取到文件的末尾
            osw.write(ch);  // 将字符数据写入des.txt文件中
      }
      isr.close(); // 关闭字符输入流，释放资源
      osw.close(); // 关闭字符输出流，释放资源
    }
}

下面通过一个案例学习如何将字节流转为字符流。具体代码如下所示。

# 10.4  转换流

代码运行结果

运行代码，src.txt文件和des.txt文件内容分别如下图所示。

src.txt文件

# 10.4  转换流

des.txt文件

由两图对比可知，案例实现了字节流和字符流之间的转换，并通过转换后的字符流完成了src.txt文件到des.txt文件的数据读写。

# 序列化和反序列化

10.5

# 10.5  序列化和反序列化

先定一个小目标！

# 10.5  序列化和反序列化

序列化和反序列化

程序在运行过程中，数据都保存在Java中的对象中（内存），但很多情况下我们都需要将一些数据永久保存到磁盘上。为此，Java提供了对象序列化，对象序列化可以将对象中的数据保存到磁盘。
对象序列化（Serializable）是指将一个Java对象转换成一个I/O流的字节序列的过程。
反序列化（Deserialize）是指将I/O流中的字节序列恢复为Java对象的过程。

# 10.5  序列化和反序列化

Serializable接口和Externalizable接口实现序列化机制的主要区别

对象实现支持序列化机制，这个对象所属的类必须是可序列化的。在Java中可序列化的类必须实现Serializable或Externalizable两个接口之一。

| Serializable接口 | Externalizable接口 |
|---|---|
| 系统自动存储必要的信息 | 由程序员决定所存储的信息 |
| Java内部支持，易于实现，只需实现该接口即可，不需要其他代码支持 | 接口中只提供了两个抽象方法，实现该接口必须要实现这两个抽象方法 |
| 性能较差 | 性能较好 |

# 10.5  序列化和反序列化

实现序列化方法

与实现Serializable接口相比，虽然实现Externalizable接口可以带来一定性能上的提升，但由于实现Externalizable接口，需要实现两个抽象方法，所以实现Externalizable接口也将导致编程的复杂度增加。在实际开发时，大部分都采用实现Serializable接口的方式来实现对象序列化。使用Serializable接口实现对象序列化非常简单，只需要让目标类实现Serializable接口即可，无需实现任何方法。

# 10.5  序列化和反序列化

示例代码

public class Person implements Serializable{
	//为该类指定一个serialVersionUID变量值
	private static final long serialVersionUID = 1L;
	//声明变量
	private int id;
	private String name;
	private int age;
	// 此处省略各属性的getter和setter方法
    ...
}

实现序列化。具体代码如下所示。

# 10.5  序列化和反序列化

小提示：serialVersionUID

serialVersionUID适用于Java的对象序列化机制。简单来说，Java的对象序列化机制是通过判断类的serialVersionUID来验证版本一致性。在进行反序列化时，JVM会把字节流中的serialVersionUID与本地相应实体类的serialVersionUID进行比较，如果相同就认为是一致的，可以进行反序列化，否则就会抛出序列化版本不一致的异常。因此，为了在反序列化时确保序列化版本的兼容性，最好在每一个要序列化的类中加入private static final long serialVersionUID的变量值，具体数值可自定义，默认是1L。

# 本章小结

本章主要介绍了I/O流的相关知识。首先讲解了File类，包括创建File对象、File类的常用方法、遍历目录下的文件和删除文件及目录；接着讲解了字节流，包括字节流的概念、字节流读文件、字节流写文件和文件的复制；然后讲解了字符流，包括了字符流定义及基本用法、字符流读文件和字符流写文件；接着又讲解了转换流的使用；最后讲解了序列化和反序列化。通过本章的学习，读者可以认识I/O流，并能够熟练掌握I/O流的相关知识。

本

章

小

结
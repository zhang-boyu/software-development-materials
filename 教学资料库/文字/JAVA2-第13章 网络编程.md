# 第13章  网络编程

Java基础入门（第3版）

# 学习目标/Target

# 学习目标/Target

# 章节概述/ Summary

如今，计算机网络已经成为人们日常生活的必需品，无论是工作时发送邮件，还是在休闲时和朋友网上聊天都离不开计算机网络。所谓的计算机网络是指将地理位置不同的具有独立功能的多台计算机及其外部设备，通过通信线路连接起来，在网络操作系统、网络管理软件及网络通信协议的管理和协调下，实现资源共享和信息传递的计算机系统。位于同一个网络中的计算机若想实现彼此间的通信，可以通过编写网络程序来实现，即在不同的计算机上编写一些实现了网络连接的程序，通过这些程序可以实现不同计算机之间数据的交互。本章将重点介绍网络通信的相关知识以及网络程序的编写。

# 目录/Contents

# 网络基础

13.1

# 13.1.1  网络通信协议

先定一个小目标！

# 13.1.1  网络通信协议

为了提供通信支持，位于同一个网络中的计算机在进行连接和通信时必须要遵守一定的规则，这些规则被称为网络通信协议，它对数据的传输格式、传输速率、传输步骤等做了统一规定，通信双方必须同时遵守才能完成数据交互。网络通信协议有很多种，本章所学的网络编程知识，主要就是基于TCP/IP协议中的内容。

网络通信协议

# 13.1.1  网络通信协议

TCP/IP协议

TCP/IP（又称TCP/IP协议簇）是一组用于实现网络互连的通信协议，其名称来源于该协议簇中两个重要的协议（TCP协议和IP协议）。基于TCP/IP的网络参考模型将协议分成四个层次，如图所示。

# 13.1.1  网络通信协议

TCP/IP协议中的四个层次

TCP/IP协议中的四个层次从最下层到最上层依次是链路层、网络层、传输层和应用层，每层分别负责不同的通信功能。
链路层：链路层也称为数据链路层或网络接口层，通常包括操作系统中的设备驱动程序和计算机中对应的网络接口卡。它们一起处理与电缆或其他传输媒介有关的物理接口细节。
网络层：也称网络互联层，是整个TCP/IP协议的核心，它主要用于将传输的数据进行分组，将分组数据发送到目标计算机或者网络。网络层对TCP/IP网络中的硬件资源进行标识。

# 13.1.1  网络通信协议

传输层：在TCP/IP网络中，不同的机器之间进行通信，数据的传输是由传输层控制的，这包括数据要发往的目的主机及应用程序、数据的质量控制等。TCP/IP网络中最常用的传输协议TCP和UDP就应用于这一层。传输层通常以TCP或UDP来控制端点到端点的通信。用于通信的端点由Socket定义，而Socket由IP地址和端口号组成。
应用层：主要负责应用程序的协议。大多数基于Internet的应用程序都被看作TCP/IP的应用层协议，如HTTP协议、FTP协议、SMTP协议、Telnet协议等。

# 13.1.2  UDP与TCP协议

先定一个小目标！

# 13.1.2  UDP与TCP协议

UDP是无连接通信协议，即在数据传输时，数据的发送端和接收端不建立逻辑连接。简单来说，当一台计算机向另外一台计算机发送数据时，发送端不会确认接收端是否存在就会发出数据。同样接收端在收到数据时，也不会向发送端反馈是否收到数据。

1.  UDP协议

# 13.1.2  UDP与TCP协议

UDP连接的交互过程

由于UDP协议消耗资源小，通信效率高，所以UDP协议通常都会用于音频、视频和普通数据的传输，但是在使用UDP协议传送数据时，因为UDP具有面向无连接性，不能保证数据的完整性，所以在传输重要数据时不建议使用UDP协议。

# 13.1.2  UDP与TCP协议

TCP协议是面向连接的通信协议，即在传输数据前先在发送端和接收端建立逻辑连接，然后再传输数据，它提供了两台计算机之间可靠无差错的数据传输。在TCP连接中必须要明确客户端与服务器端，由客户端向服务器端发出连接请求，每次连接的创建都需要经过“三次握手”。因为TCP协议拥有面向连接特性，所以它可以保证传输数据的安全性，是一个被广泛采用的协议。例如文件传输。

2.  TCP协议

# 13.1.2  UDP与TCP协议

TCP连接的交互过程

第一次握手，客户端向服务器端发出连接请求，等待服务器确认；
第二次握手，服务器端向客户端回送一个响应，通知客户端收到了连接请求；第三次握手，客户端再次向服务器端发送确认信息，确认连接。

# 13.1.3  IP地址和端口号

先定一个小目标！

# 13.1.3  IP地址和端口号

互联网上的每一台终端设备都有一个唯一标识，网络中的请求可以根据这个标识找到具体的计算机，这个唯一标识就是IP地址。目前，IP地址广泛使用的版本是IPv4，它用4个字节大小的二进制数表示，如00001010000000000000000000000001。因为二进制形式不便于记忆，所以通常会将IP地址写成十进制形式，每个字节用一个十进制数字（0~255）表示，数字间用点符号（.）分开，如127.0.0.1。

1.  IP地址（Intenet Protocol）

# 13.1.3  IP地址和端口号

查看本机的IP地址

在Windows操作系统中，用户可以在命令行通过ipconfig命令查看本机的IP地址，具体如图所示。

# 13.1.3  IP地址和端口号

IP地址的组成

IP地址={<网络地址>，<主机地址>}，其中网络部分表示IP地址属于互联网的哪一个网络，是网络的地址编码，主机部分表示其属于该网络中的哪一台主机，是网络中一个主机的地址编码，二者是主从关系。

# 13.1.3  IP地址和端口号

IP地址分类及其范围

IP地址根据网络地址和主机地址的范围，分为5类，各地址可使用的IP数量不同，IP地址分类及其范围如表所示。

在表中可以发现没有127.X.X.X的地址，因为其是保留地址，用作循环测试，在开发中经常使用127.0.0.1表示本机的IP地址。

| 方法声明 | 功能描述 |
|---|---|
| A类地址 | 1.0.0.1~126.255.255.254 |
| B类地址 | 128.0.0.1~191.255.255.254 |
| C类地址 | 192.0.0.1~223.255.255.254 |
| D类地址 | 224.0.0.0~239.255.255.255 |
| E类地址 | 240.0.0.0~255.255.255.255 |

# 13.1.3  IP地址和端口号

在计算机中，端口号就是一个服务所占用的端口的唯一标识。如果把计算机看做一座大楼，IP地址相当于大楼的地址，端口号是不同房间的门牌号。IP地址需要和端口号结合起来使用，网络中的请求需要通过IP地址找到主机，一台主机上可能同时运行很多个服务，不同的服务会占用不同的端口，主机根据端口号把不同的请求分配给不同的服务。端口号是用16位的二进制数来表示的，将其转换为十进制数的取值范围是0~65535，其中，0~1023之间的端口号由操作系统的网络服务占用。

2.  端口号（port）

# 13.1.3  IP地址和端口号

IP地址和端口号的作用

从图中可以清楚地看到，位于网络中的一台计算机可以通过IP地址去访问另一台计算机，并通过端口号访问目标计算机中的某个应用程序。

# 13.1.4  InetAddress类

先定一个小目标！

# 13.1.4  InetAddress类

InetAddress类的常用方法

Java提供了一个与IP地址相关的InetAddress类，用于封装一个IP地址，并提供了一系列与IP地址相关的方法，如表所示。

| 方法声明 | 功能描述 |
|---|---|
| InetAddress getByName(String host) | 通过给定的主机名host，获取InetAddress对象的IP地址 |
| InetAddress getByAddress(byte[] addr) | 通过存放在字节数组中的IP地址，返回一个InetAddress对象 |
| InetAddress getLocalHost() | 获取本地主机的IP地址 |
| byte[] getAddress() | 获取本对象的IP地址，并存放在字节数组中 |
| String getHostAddress() | 获取字符串格式的原始IP地址 |
| String getHostName() | 获取IP地址的主机名，如果是本机则是计算机名，不是本机则是主机名，如果没有域名则是IP地址 |
| Boolean isReachable(int timeout) | 判断地址是否可以到达，同时指定超时时间 |

# 13.1.4  InetAddress类

案例演示

下面通过一个案例演示InetAddress类常用方法的使用。具体代码如下所示。

import java.net.InetAddress;
 public class Example01 {
   public static void main(String[] args) throws Exception {
    InetAddress localAddress = InetAddress.getLocalHost();
    InetAddress remoteAddress = InetAddress.getByName("www.itcast.cn");
    System.out.println("本机的IP地址：" + localAddress.getHostAddress());
    System.out.println("www.itcast.cn的IP地址：" + 
 			remoteAddress.getHostAddress());
    System.out.println("3秒是否可达主机名为www.itcast.cn的IP地址：" + 
 			remoteAddress.isReachable(3000));
 	}
 }

# 13.1.4  InetAddress类

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# 13.1.5  URL编程

先定一个小目标！

# 13.1.5  URL编程

URL（Uniform Resource Locator）是统一资源定位器，它表示互联网上某一资源的地址。互联网上的资源包括HTML文件、图像文件、音频文件、视频文件等，只要按照URL规则定义某个资源，网络上的程序就可以通过URL访问它。也就是说，通过URL访问Internet时，浏览器或其他程序通过解析给定的URL就可以在网络上查找到相应的文件或资源。实际上，用户上网时在浏览器地址栏中输入的网址就是一个URL。

URL（Uniform Resource Locator）

# 13.1.5  URL编程

URL的基本结构

URL的基本结构由5部分组成，具体格式如下。

传输协议：//主机名：端口号/文件名#引用

URL基本格式中每个部分的含义如下所示。
（1）传输协议：指所使用的协议名，如HTTP、FTP等。
（2）主机名：指资源所在的计算机名称。主机名可以是IP地址，也可以是计算机的名称或域名。
（3）端口号：指定服务占用的端口号。

# 13.1.5  URL编程

http://java.sun.com
http://java.sun.com/index.html

（4）文件名：指访问的文件名称，包括该文件的完整路径。在HTTP中，有一个默认的文件名index.html，因此下列两个地址是等价的。

（5）引用：指资源内部的某个参考点，如http://java.sun.com/index.html#page1。

  注意：对于一个URL，并不要求必须包含所有的5个部分。

# 13.1.5  URL编程

URL类的常用方法

Java中定义了一个URL类，用于访问网络上的资源，URL类中定义了一些常用方法，利用这些方法可以得到URL位置本身的数据，或是将URL对象转换成表示URL位置的字符串如表所示。

| 方法声明 | 功能描述 |
|---|---|
| public URL(String spec)throws MalformedURLException | 根据指定的地址实例化URL对象 |
| public URL(String protocol,String host,int port,String file)throws MalformedURLException | 实例化URL对象，并指定协议、主机、端口名称、资源对象 |
| public URLConnection openConnection()throws IOException | 取得一个URLConnection对象 |
| public final InputStream openStream()throws IOException | 取得输入流 |

# 13.1.5  URL编程

案例演示

下面通过一个案例学习URL类中常用方法的使用。具体代码如下所示。

import java.io.InputStream;
 import java.net.URL;
 import java.util.Scanner;
 public class Example02 {
     public static void main(String[] args) throws Exception {
        URL url = new URL("http","www.itcast.cn",80,"/subject/uidszly/index.html");
         InputStream input = url.openStream();
         Scanner scan = new Scanner(input);
         scan.useDelimiter("\n");
         while(scan.hasNext()){
             System.out.println(scan.next());
         }
     }
 }

# 13.1.5  URL编程

案例运行结果

运行代码，控制台显示的运行结果如下图所示。

# TCP通信

13.2

# 13.2.1  ServerSocket类

先定一个小目标！

# 13.2.1  ServerSocket类

在Socket编程中，编写服务器端程序需要使用ServerSocket类。ServerSocket类在java.net包中，java.net. ServerSocket继承自java.lang.Object类。ServerSocket类的主要作用是接收客户端的连接请求。

ServerSocket类

# 13.2.1  ServerSocket类

ServerSocket类的构造方法

通过查阅API文档可知，ServerSocket类提供了多种构造方法，如表所示。

| 构造方法 | 功能描述 |
|---|---|
| ServerSocket() | 通过该方法创建的ServerSocket对象不与任何端口绑定，这样的ServerSocket对象创建的服务器端没有监听任何端口，不能直接使用，还需要继续调用bind(SocketAddress endpoint)方法将其绑定到指定的端口号上，才可以正常使用。 |
| ServerSocket(int port) | 该方法的作用是以端口port创建ServerSocket对象，并等待客户端的连接请求。最常用的构造方法。 |
| ServerSocket(int port, int backlog) | 该构造方法在第二个构造方法的基础上，增加了一个backlog参数。该参数用于指定最大连接数，即可以同时连接的客户端数量。 |
| ServerSocket(int port, int backlog, InetAddress bindAddr) | 该构造方法在第三个构造方法的基础上，增加了一个bindAddr参数，该参数用于指定相关的IP地址。 |

# 13.2.1  ServerSocket类

ServerSocket类的常用方法

了解了ServerSocket类的构造方法后，下面学习一下ServerSocket类的常用方法，如表所示。

| 方法名称 | 功能描述 |
|---|---|
| Socket accept() | 该方法用于等待客户端的连接，在客户端连接之前会一直处于阻塞状态，如果有客户端连接，就会返回一个与之对应的Socket对象。 |
| InetAddress getInetAddress() | 该方法用于返回一个InetAddress对象，该对象中封装了ServerSocket绑定的IP地址。 |
| boolean isClosed() | 该方法用于判断ServerSocket对象是否为关闭状态，如果是关闭状态则返回true，反之则返回false。 |
| void bind(SocketAddress endpoint) | 该方法用于将ServerSocket对象绑定到指定的IP地址和端口号，其中参数endpoint 封装了IP 地址和端口号。 |

# 13.2.2  Socket类

先定一个小目标！

# 13.2.2  Socket类

Socket类在java.net包中定义，java.net.Socket继承自java.lang.Object类。Socket类用于编写客户端程序，用户通过创建一个Socket对象建立与服务器的连接。

Socket类

# 13.2.2  Socket类

Socket类的构造方法

通过查阅API文档可知，Socket类的构造方法，如表所示。

| 构造方法 | 功能描述 |
|---|---|
| Socket() | 使用该构造方法在创建Socket对象时，并没有指定IP地址和端口号，也就意味着只创建了客户端对象，并没有去连接任何服务器。最常用的构造方法。 |
| Socket(String host, int port) | 该构造方法用于在客户端以指定的服务器地址host和端口号port创建一个Socket对象，并向服务器端发出连接请求。 |
| Socket(InetAddress address, int port) | 创建一个流套接字，并将其连接到指定IP地址的指定端口 |
| Socket(InetAddress address, int port,boolean stream) | 该构造方法在使用上与第二个构造方法类似，但IP地址由host指定。 |

# 13.2.2  Socket类

Socket类的常用方法

了解了Socket类的构造方法后，下面学习一下Socket类的常用方法，如表所示。

| 方法名称 | 功能描述 |
|---|---|
| int getPort() | 该方法用于获取Socket对象与服务器端连接的端口号。 |
| InetAddress getLocalAddress() | 该方法用于获取Socket对象绑定的本地IP地址，并将IP地址封装成InetAddress类型的对象返回。 |
| InetAddress getInetAddress() | 该方法用于获取创建Socket对象时指定的服务器的IP地址。 |
| void close() | 该方法用于关闭Socket连接，结束本次通信。在关闭Socket之前，应将与Socket相关的所有的输入输出流全部关闭，这是因为一个良好的程序应该在执行完毕时释放所有的资源。 |

# 13.2.2  Socket类

表中列举了Socket类的常用方法，其中getInputStream()方法和getOutputStream()方法分别用于获取输入流和输出流。

| 方法名称 | 功能描述 |
|---|---|
| InputStream getInputStream() | 该方法返回一个InputStream类型的输入流对象，如果该输入流对象是由服务器端的Socket返回，就用于读取客户端发送的数据，反之，用于读取服务器端发送的数据。 |
| OutputStream getOutputStream() | 该方法返回一个OutputStream类型的输出流对象，如果该输出流对象是由服务器端的Socket返回，就用于向客户端发送数据，反之，用于向服务器端发送数据。 |

# 13.2.2  Socket类

服务器端和客户端的数据传输过程

当客户端和服务器端建立连接后，数据以IO流的形式进行交互，从而实现通信。服务器端和客户端的数据传输过程，如下图所示。

# 13.2.3  简单的TCP通信

先定一个小目标！

# 13.2.3  简单的TCP通信

案例演示简单的TCP通信

下面通过一个TCP通信的案例进一步学习ServerSocket类和Socket类的用法。要实现TCP通信需要创建一个服务器端程序和一个客户端程序。具体步骤如下。

# 13.2.3  简单的TCP通信

public class TCPServer {
     public static void main(String[] args) throws Exception {
           Socket client = null;                             //声明Socket对象
           OutputStream os = null;                      //声明OutputStream对象
           //创建ServerSocket对象并指定端口号（7788）
           ServerSocket serverSocket = new ServerSocket(7788); 
           System.out.println("服务器正在运行，等待与客户端连接");
           client = serverSocket.accept();             //程序阻塞，等待客户端连接
           os = client.getOutputStream();            //获取客户端的输出流
           System.out.println("开始与客户端交互数据");
           // 当客户端连接到服务器端时，向客户端输出数据
           os.write(("北京欢迎你！").getBytes());
           Thread.sleep(5000);                           //模拟执行其他功能占用的时间
           System.out.println("结束与客户端交互数据");
           os.close();
           client.close();
     }
 }

步骤一：首先实现服务器端程序。代码如下所示：

# 13.2.3  简单的TCP通信

运行结果

运行代码，控制台显示的运行结果如下图所示。

从图的运行结果可以看出，控制台打印出了“服务器正在运行，等待与客户端连接”，并且控制台中的光标一直在闪动，这是因为accept()方法在执行时发生阻塞，直到客户端连接之后才会结束这种阻塞状态。

# 13.2.3  简单的TCP通信

步骤二：接下来编写客户端程序，并介绍如何通过客户端访问服务器端。代码如下所示：

public class TCPClient {
    public static void main(String[] args) throws Exception {
        Socket client = null;                               //声明Socket对象
        client = new Socket("localhost",7788);  //指定连接的主机端口号
        BufferedReader buf = null;  //声明BufferedReader对象，用于接收信息
        buf = new BufferedReader(
                new InputStreamReader(
                        client.getInputStream()              //取得客户端的输入流
                )
        );
        String str = buf.readLine();                        //读取信息
        System.out.println("服务器端输出内容:"+str);
        client.close();                                        //关闭Socket
        buf.close();                                            //关闭输入流
    }
}

# 13.2.3  简单的TCP通信

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 13.2.3  简单的TCP通信

服务器端控制台变化

在客户端创建的Socket对象成功读取服务器端发来的数据并打印在控制台后，同时服务器端程序会结束阻塞状态，并在控制台中打印出“开始与客户端交互数据”，然后向客户端发送数据“北京欢迎你！”，在服务器端休眠5秒钟后会在控制台打印出“结束与客户端交互数据”，本次通信才结束。如下图所示。

# 13.2.4  多线程的TCP网络程序

先定一个小目标！

# 13.2.4  多线程的TCP网络程序

多个用户访问同一个服务器的过程

很多服务器端程序都支持多线程，允许多个客户端同时访问，例如，门户网站可以被多个用户同时访问。
服务器端为每个客户端创建一个对应的Socket，并且开启一个新的线程使两个Socket建立专线进行通信。多个用户访问同一个服务器的过程如图所示。

# 13.2.4  多线程的TCP网络程序

案例演示多线程的TCP网络程序

下面根据多个用户访问同一个服务器的过程图所示的通信方式对13.2.3节中的服务器端程序，进行修改。具体步骤如下。

# 13.2.4  多线程的TCP网络程序

public class TCPServer {
      public static void main(String[] args) throws Exception {
              // 创建ServerSocket对象，监听指定的端口
              ServerSocket serverSocket = new ServerSocket(7788);
              // 使用while循环不停的接收客户端发送的请求
              while (true) {
                      // 调用ServerSocket的accept()方法等待客户端的连接
                      final Socket client = serverSocket.accept();
                      int port = client.getPort();//获取Socket对象与服务器端连接的端口号
                      System.out.println("与端口号为"+port+"的客户端连接成功！"); 
                      // 下面的代码在步骤二中完成，开启一个新的线程处理客户端发送的数据
              }
      }
}

步骤一：使用多线程的方式编写了一个服务器端程序。通过在while循环中调用accept()方法不停的接收客户端发送的请求。代码如下所示：

# 13.2.4  多线程的TCP网络程序

new Thread() {
                public void run() {
                    OutputStream os= null;  	             // 定义一个输出流对象
                    try {
                        os = client.getOutputStream(); // 获取客户端的输出流
                        System.out.println("开始与客户端交互数据");
                        os.write(("北京欢迎你！").getBytes());
                        Thread.sleep(5000);              // 使线程休眠5000毫秒
                        System.out.println("结束与客户端交互数据");
                        os.close();                        // 关闭输出流
                        client.close();                   // 关闭Socket对象
                    } catch (Exception e) {
                        e.printStackTrace();
                    }
                };
            }.start();

步骤二：创建一个线程并开启，处理客户端发送的数据。代码如下所示：

# 13.2.4  多线程的TCP网络程序

步骤三：为了验证服务器端程序是否实现了多线程，这里需要再创建两个与13.2.3节中相同的客户端程序，只需修改其类名即可。客户端程序创建完成之后，首先运行本节中的服务器端程序，之后连续运行3个客户端程序。

# 13.2.4  多线程的TCP网络程序

测试过程

在测试过程中，当运行第一个客户端程序时，服务器端马上就进行数据处理，打印出“与端口号为60351的客户端连接成功！”的信息（端口是随机的，可能不同），紧接着再运行第2个和第3个客户端程序，会发现服务端也立刻做出回应，同时启动的这3个客户端都能够接收到服务端响应的信息。测试结果如下图。

# 13.2.4  多线程的TCP网络程序

多线程的TCP网络程序测试结果

由图可知，通过多线程的方式，可以实现多个客户端程序对同一个服务器端程序的访问。

# UDP通信

13.3

# UDP是一种面向无连接的协议，因此在通信时发送端和接收端不用建立连接。UDP通信的过程就像是货运公司在两个码头间发送货物一样，DatagramPacket用于封装要发送的数据的“集装箱”，DatagramSocket用于完成数据的发送与接收的“码头”。

13.3  UDP通信

# 13.3.1  DatagramPacket类

先定一个小目标！

# 13.3.1  DatagramPacket类

DatagramPacket类用于封装UDP通信中发送或者接收的数据，DatagramPacket类对象也称为数据报对象。利用UDP通信时，发送端使用DatagramPacket类将数据打包，即用DatagramPacket类创建一个数据报对象，这个数据报对象包含有需要传输的数据、数据报的长度、IP地址和端口号等信息。

DatagramPacket类

# 13.3.1  DatagramPacket类

想要创建一个DatagramPacket对象，首先需要了解一下它的构造方法。在创建发送端和接收端的DatagramPacket对象时，使用的构造方法有所不同，接收端的构造方法只需要接收一个字节数组作为参数，用于存放接收到的数据；而发送端的构造方法不但要接收存放了发送数据的字节数组，还需要指定发送端IP地址和端口号。

DatagramPacket类的构造函数

# 13.3.1  DatagramPacket类

| 方法声明 | 功能描述 |
|---|---|
| DatagramPacket(byte[] buf,int length) | 用于创建一个接收端的数据报对象，buf数组用于接收发送端发送过来的数据报中的数据，接收长度为length。没有指定IP地址和端口号。这样的对象只能用于接收端，不能用于发送端。因为发送端一定要明确指出数据的目的地(IP地址和端口号)，而接收端不需要明确知道数据的来源，只需要接收到数据即可。 |
| DatagramPacket(byte[] buf,int length,InetAddress addr,int port) | 创建一个用于发送给远程系统的数据报对象，并将数组buf中长度为length的数据发送到地址为address、端口号为port的主机上。创建的数据报对象通常用于发送端。 |

# 13.3.1  DatagramPacket类

| 方法声明 | 功能描述 |
|---|---|
| DatagramPacket(byte[] buf,int offset,int length) | 该构造方法与第一个构造方法类似，同样用于接收端，只不过在第一个构造方法的基础上，增加了一个offset参数，该参数用于指定接收到的数据在放入buf缓冲数组时是从offset索引处开始的。 |
| DatagramPacket(byte[] buf,int offset,int length,InetAddress addr,int port) | 该构造方法与第二个构造方法类似，同样用于发送端，只不过在第二个构造方法的基础上，增加了一个offset参数，该参数用于指定一个从数组的offset索引处开始发送数据。 |

# 13.3.1  DatagramPacket类

DatagramPacket类的常用方法

讲解了DatagramPacket类的构造方法，下面对该类中的常用方法进行详细讲解，如表所示。

| 方法 | 功能描述 |
|---|---|
| InetAddress getAddress() | 该方法用于返回发送端或者接收端的IP地址，如果是发送端的DatagramPacket对象，就返回接收端的IP地址，反之，就返回发送端的IP地址 |
| int getPort() | 该方法用于返回发送端或者接收端的端口号，如果是发送端的DatagramPacket对象，就返回接收端的端口号；反之，就返回发送端的端口号 |

# 13.3.1  DatagramPacket类

表中列举了DatagramPacket类的四个常用方法及其功能，通过这四个方法，可以获取发送或者接收到的DatagramPacket数据报中的信息。

| 方法 | 功能描述 |
|---|---|
| byte[] getData() | 该方法用于返回将要接收或者将要发送的数据，如果是发送端的DatagramPacket对象，就返回将要发送的数据；反之，就返回接收到的数据 |
| int getLength() | 该方法用于返回接收或者将要发送数据的长度，如果是发送端的DatagramPacket对象，就返回将要发送的数据长度；反之，就返回接收到数据的长度 |

# 13.3.2  DatagramSocket类

先定一个小目标！

# 13.3.2  DatagramSocket类

DatagramSocket类用于在发送主机中建立数据报通信方式，提出发送请求，实现数据报的发送与接收。在创建发送端和接收端的DatagramSocket对象时，使用的构造方法也有所不同。

DatagramSocket类

# 13.3.2  DatagramSocket类

DatagramSocket类的构造方法

下面对DatagramSocket类中的构造方法进行讲解，如表所示。

| 方法声明 | 功能描述 |
|---|---|
| DatagramSocket() | 该构造方法用于创建发送端的DatagramSocket对象，在创建DatagramSocket对象时，并没有指定端口号，系统会分配一个没有被其他网络程序所使用的端口号 |
| DatagramSocket(int port) | 该构造方法既可用于创建接收端的DatagramSocket对象，又可以创建发送端的DatagramSocket对象，在创建接收端的DatagramSocket对象时，必须要指定一个端口号，这样就可以监听指定的端口 |
| DatagramSocket(int port,InetAddress addr) | 该构造方法用于在有多个IP地址的当前主机上，创建一个以laddr为指定IP地址、以port为指定端口的数据报连接 |

# 13.3.2  DatagramSocket类

DatagramSocket类的常用方法

除了构造方法，DatagramSocket类还提供了其他方法，用于实现UDP通信，如表所示。

| 方法声明 | 功能描述 |
|---|---|
| void receive(DatagramPacket p) | 该方法用于接收数据，并将接收到的数据保存到DatagramPacket数据报中，在接收到数据之前，receive()方法会一直处于阻塞状态，只有当接收到数据报时，该方法才会返回 |
| void send(DatagramPacket p) | 该方法用于发送DatagramPacket数据报，将数据报中包含的报文发送到所指定的IP地址主机 |
| void setSoTimeout(int timeout) | 设置传输数据时超时时间为timeout |
| void close() | 关闭数据报连接 |

# 13.3.2  DatagramSocket类

UDP连接注意事项

由于UDP连接是不可靠的通信方式，所以调用receive()方法时不一定能接收到数据，为了防止线程死掉，应该调用setSoTimeout()方法设置超时参数timeout()。另外，receive()方法和send()方法都可能产生输入、输出异常，因此都可能抛出IOException异常。

# 13.3.3  简单的UDP通信

先定一个小目标！

# 13.3.3  简单的UDP通信

UDP通信中数据报的发送过程

（1）创建一个用于发送数据报的DatagramPacket对象，使其包含如下信息。
要发送的数据；
数据报分组的长度；
发送目的地的主机IP地址和目的端口号。
（2）在指定的或可用的本机端口创建DatagramSocket对象。
（3）调用DatagramSocket对象的send()方法，以DatagramPacket对象为参数发送数据报。

# 13.3.3  简单的UDP通信

UDP通信中数据报的接收过程

（1）创建一个用于接收数据报的DatagramSocket对象，其中包含空白数据缓冲区和指定数据报分组的长度。
（2）在指定的或可用的本机端口创建DatagramSocket对象。
（3）调用DatagramSocket对象的receive()方法，以DatagramPacket对象为参数接收数据报，接收到的信息有。
收到的数据报分组。
发送端主机的IP地址。
发送端主机的发送端口号。

# 13.3.3  简单的UDP通信

UDP通信案例

要实现UDP通信需要创建一个发送端程序和一个接收端程序。在通信时只有接收端程序先运行，才能避免发送端发送数据时找不到接收端而造成数据丢失的问题。因此，首先需要完成接收端程序的编写，然后再完成发送端程序的编写。

# 13.3.3  简单的UDP通信

步骤一：首先需要完成接收端程序的编写。具体代码如下所示。

public class Receiver {
           public static void main(String[] args) throws Exception {
	byte[] buf = new byte[1024]; // 创建一个字节数组，用于接收数据
         	// 定义一个DatagramSocket对象，端口号为8954
	DatagramSocket ds = new DatagramSocket(8954);
         	// 定义一个DatagramPacket对象，用于接收数据
	DatagramPacket dp = new DatagramPacket(buf, buf.length);
	System.out.println("等待接收数据");
	ds.receive(dp);                 	 // 接收数据
         	/*调用DatagramPacket的方法获得接收到的信息包括数据的内容、长    
	度、发送的IP地址和端口号*/
	String str = new String(dp.getData(), 0, dp.getLength()) +
                          " from "+ dp.getAddress().getHostAddress() + ":" + dp.getPort();
	System.out.println(str); 		 // 打印接收到的信息
	ds.close();                 		 // 关闭数据报连接
        }
}

# 13.3.3  简单的UDP通信

接收端程序运行结果

运行代码，控制台显示的运行结果如下图所示。

从图可以看出，接收端程序运行后，程序一直处于阻塞状态，这是因为DatagramSocket的receive()方法在等待接收发送端发送过来的数据，只有接收到发送端发送的数据，该方法才会结束这种阻塞状态，程序才能继续向下执行。

# 13.3.3  简单的UDP通信

步骤二：实现了接收端程序之后，接下来编写发送端程序，用于给接收端发送数据。具体代码如下所示。

public class Sender {
           public static void main(String[] args) throws Exception {
	// 创建一个DatagramSocket对象
	DatagramSocket ds = new DatagramSocket(3000);
	String str = "hello world"; //要发送的数据
	byte[] arr = str.getBytes(); //将定义的字符串转为字节数组
         	/*创建一个要发送的数据报，数据报包括发送的数据，
           	数据的长度，接收端的IP地址以及端口号*/
	DatagramPacket dp = new DatagramPacket(arr, arr.length,
                           InetAddress.getByName("localhost"), 8954);
	System.out.println("发送信息");
	ds.send(dp); // 发送数据
	ds.close();  	// 释放资源
         }
}

# 13.3.3  简单的UDP通信

发送端程序运行结果

运行代码，控制台显示的运行结果如下图所示。

# 13.3.3  简单的UDP通信

接收端控制台变化

运行发送端程序后，接收端程序就会收到发送端发送的数据而结束阻塞状态，并打印接收的数据。

# 脚下留心

UDP程序所使用的端口号被占用时发生运行异常

需要注意的是，当UDP程序所使用的端口号被占用时，程序会抛出异常，如图所示。

# 脚下留心

UDP程序所使用的端口号被占用时发生运行异常

出现图中所示的情况，是因为在一台计算机中，一个端口号只能被一个应用程序占用，当我们编写的UDP程序所使用的端口号已经被其他的应用程序占用时，就会出现这种情况。遇到这种情况时，可以在命令行窗口输入netstat -ano命令来查看当前计算机端口的占用情况。

# 脚下留心

UDP程序所使用的端口号被占用时发生运行异常

netstat -ano命令运行结果：

在左图中，显示了所有正在运行的应用程序及它们所占用的端口号。想要解决端口号占用的问题，只需关掉占用端口号的应用程序或者使用一个未被占用的端口号重新运行程序即可。

# 13.3.4  多线程的UDP网络程序

先定一个小目标！

# 13.3.4  多线程的UDP网络程序

13.3.3节分别实现了发送端程序和接收端程序，当在接收端程序处在阻塞的状态下，运行发送端程序时，接收端程序会因为收到发送端发送的数据而结束阻塞状态，完成程序运行。实际上，发送端可以无限发送数据，接收端也可以一直接收数据，例如，聊天程序发送端可以一直发消息，接收端也可以一直接收消息，因此发送端和客户端都是多线程的。

多线程的UDP网络程序

# 13.3.4  多线程的UDP网络程序

案例演示多线程的UDP网络程序

接下来通过一个案例演示使用UDP通信方式实现多线程的UDP网络程序。具体步骤如下。

# 13.3.4  多线程的UDP网络程序

class Receive extends Thread {
    public void run() {
        try {
            //创建socket相当于创建码头
            DatagramSocket socket = new DatagramSocket(6666);
            //创建packet相当于创建集装箱
            DatagramPacket packet = new DatagramPacket(new byte[1024], 1024);
            while(true) {
                socket.receive(packet);//接收货物
                byte[] arr = packet.getData();
                int len = packet.getLength();
                String ip = packet.getAddress().getHostAddress();
                System.out.println(ip + ":" + new String(arr,0,len));
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

步骤一：创建接收端程序Receive类继承Thread类。代码如下所示：

# 13.3.4  多线程的UDP网络程序

class Send extends Thread {
    public void run() {
        try {
            DatagramSocket socket = new DatagramSocket();//创建socket相当于创建码头
            Scanner sc = new Scanner(System.in);
            while(true) {
                String str = sc.nextLine();
                if("quit".equals(str))
                    break;
                DatagramPacket packet = new DatagramPacket(str.getBytes(),
                           str.getBytes().length, InetAddress.getByName("127.0.0.1"), 6666);
                socket.send(packet);//发货
            }
            socket.close();
        }  catch (IOException e) {
            e.printStackTrace();
        }
    }
}

步骤二：创建发送端程序Send类继承Thread类。代码如下所示：

# 13.3.4  多线程的UDP网络程序

运行结果

运行代码，在控制台分别输入第一次发送、第二次发送和第三次发送并按回车键，控制台输出结果如下图所示。

# 本章小结

本章讲解了Java网络编程的相关知识。首先简要介绍了网络基础的相关知识，包括TCP/IP协议的四个层次、UDP协议与TCP协议、IP地址和端口号、InetAddress类和URL编程；然后讲解了TCP程序设计中相关的ServerSocket类和Socket类，并通过两个案例实现了简单的TCP通信和多线程的TCP通信；最后着重介绍了UDP程序设计相关的DatagramPacket类和DatagramSocket类，并通过两个的案例实现了简单的UDP通信和多线程的UDP通信。通过对本章的学习，读者能够对网络编程的底层原理有一个简单的了解，为以后的网络编程开发打下基础。

本

章

小

结
# 第12章  多线程

Java基础入门（第3版）

# 学习目标/Target

# 学习目标/Target

# 章节概述/ Summary

多线程是提升程序性能非常重要的一种方式，也是Java编程中的一项重要技术。在程序设计中，多线程就是指一个应用程序中有多条并发执行的线索，每条线索都被称作一个线程，它们会交替执行，彼此间可以进行通信。本章将针对Java中的多线程知识进行详细地讲解等。

# 目录/Contents

# 进程与线程

12.1

# 12.1.1  进程

先定一个小目标！

# 12.1.1  进程

进程是计算机中程序的一次运行活动，是系统进行资源分配和调度的基本单位，是操作系统结构的基础。虽说进程在程序执行时产生，但进程并不是程序。程序是“死”的，进程是“活”的，程序是指编译好的二进制文件，它存放在磁盘上，不占用系统资源，是具体的；而进程存在于内存中，占用系统资源，是抽象的。当一次程序执行结束之后，进程随之消失，进程所用的资源被系统回收。

进程（Process）

# 12.1.1  进程

一个单核的CPU，同一时刻只能处理一个进程，用户之所以认为同时会有多个进程在运行，是因为计算机系统采用了“多道程序设计”技术。所谓多道程序设计，是指计算机允许多个相互独立的程序同时进入内存，在内存的管理控制之下，相互之间穿插运行。

“多道程序设计”技术

# 12.1.1  进程

采用多道程序设计的系统，会将CPU的整个生命周期划分为长度相同的时间片，在每个CPU时间片内只处理一个进程。也就是说，在多个时间片上，系统会让多个进程分时使用CPU。虽然在同一个时间片中，一个CPU上只能处理一个进程，但CPU划分的时间片是非常微小的，且当下CPU运行速度极快，因此，在宏观上，可以认为计算机能并发执行多个程序、处理多个进程。

# 12.1.2  线程

先定一个小目标！

# 12.1.2  线程

每个运行的程序都是一个进程，在一个进程中还可以有多个执行单元同时运行，这些执行单元可以看作程序执行的一条条线程。每一个进程中都至少存在一个线程。代码按照调用顺序依次往下执行，没有出现两段程序代码交替运行的效果，这样的程序称作单线程程序。如果希望程序中实现多段程序代码交替运行的效果，则需要创建多个线程，即多线程程序。

线程

# 12.1.2  线程

多线程

多线程是指一个进程在执行过程中可以产生多个单线程，这些单线程程序在运行时是相互独立的，它们可以并发执行。多线程程序的执行过程如图所示。

图中所示的多条线程，看似是同时执行的，其实不然，它们和进程一样，也是由CPU轮流执行的，只不过CPU运行速度很快，因此给人同时执行的感觉。

# 线程的创建

12.2

# Java提供了3种多线程的创建方式: 
(1)继承javal.ang包中的Thread类，重写 Thread类的run()方法，在run()方法中实现多线程代码。 
(2)实现javal.ang.Runnable接口，在run()方法中实现多线程代码。 
(3)实现java.util.concurrent.Callable接口，重写call()方法,并使用 Future接口获取call()方法返回的结果。

12.2  线程的创建

# 12.2.1  继承Thread类创建多线程

先定一个小目标！

# 12.2.1  继承Thread类创建多线程

单线程案例

public class Example01 {
            public static void main(String[] args) {
 	MyThread01 myThread = new MyThread01(); // 创建MyThread01实例对象
 	myThread.run();                     // 调用MyThread01类的run()方法
 	while (true) {                          // 该循环是一个死循环，打印输出语句
 		System.out.println("Main方法在运行");
 	}
            }
 }
 class MyThread01 {
         public void run() {
 	while (true) {                          // 该循环是一个死循环，打印输出语句
 		System.out.println("MyThread类的run()方法在运行");
 	}
         }
 }

在学习多线程之前，先来看一个单线程程序的案例。具体代码如下所示。

# 12.2.1  继承Thread类创建多线程

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 12.2.1  继承Thread类创建多线程

运行结果分析

由上图可知，程序一直打印“MyThread类的run()方法在运行”，这是因为该程序是一个单线程程序，在调用MyThread01类的run()方法时，遇到定义的死循环中，循环会一直进行。因此，MyThread类的打印语句将被无限执行，而main()方法中的打印语句无法得到执行。如果希望代码两个while循环中的的println语句能够并发执行，就需要实现多线程。

# 12.2.1  继承Thread类创建多线程

线程类Thread

为了实现多线程，Java提供了一个线程类Thread，通过继承Thread类，并重写Thread类中的run()方法便可实现多线程。在Thread类中提供了一个start()方法用于启动新线程，新线程启动后，JVM会自动调用run()方法，如果子类重写了run()方法便会执行子类中的run()方法。

# 12.2.1  继承Thread类创建多线程

多线程案例

public class Example02 {
            public static void main(String[] args) {
 	MyThread02 myThread = new MyThread02(); // 创建MyThread02的线程对象
 	myThread.start(); // 开启线程
 	while (true) { // 通过死循环语句打印输出
 		System.out.println("main()方法在运行");
 	}
             }
 }
 class MyThread02 extends Thread {
           public void run() {
 	while (true) { // 通过死循环语句打印输出
 		System.out.println("MyThread类的run()方法在运行");
 	}
          }
 }

下面通过继承Thread类的方式来实现多线程。具体代码如下所示。

# 12.2.1  继承Thread类创建多线程

运行结果

运行代码，控制台显示的运行结果如下图所示。

由图可知，两个循环中的语句都有输出，说明程序实现了多线程。

# 12.2.1  继承Thread类创建多线程

单线程和多线程的区别

从图可以看出，单线程的程序在运行时，会按照代码的调用顺序执行，而在多线程中，main()方法和MyThread类的run()方法却可以同时运行，互不影响。

# 12.2.2  实现Runnable接口创建多线程

先定一个小目标！

# 12.2.2  实现Runnable接口创建多线程

通过继承Thread类实现了多线程，但是这种方式有一定的局限性。因为Java只支持单继承，一个类一旦继承了某个父类就无法再继承Thread类，比如学生类Student继承了Person类，那么Student类就无法再通过继承Thread类创建线程。

继承Thread类实现多线程的弊端

# 12.2.2  实现Runnable接口创建多线程

为了克服这种弊端，Thread类提供了另外一个构造方法Thread(Runnable target)，其中参数类型Runnable是一个接口，它只有一个run()方法。当通过Thread(Runnable target)构造方法创建线程对象时，只需为该方法传递一个实现了Runnable接口的对象，这样创建的线程将实现了Runnable接口中的run()方法作为运行代码，而不需要调用Thread类中的run()方法。

克服弊端的方式：实现Runnable接口创建多线程

# 12.2.2  实现Runnable接口创建多线程

class MyThread03 implements Runnable {
      public void run() {// 线程的代码段，当调用start()方法时，线程从此处开始执行
            while (true) {
	System.out.println("MyThread类的run()方法在运行");
            }
      }
}

步骤一：定义MyThread03类实现Runnable接口，重写了Runnable接口中的run()方法。代码如下所示：

下面通过一个案例演示如何通过实现Runnable接口的方式来创建多线程。具体步骤如下。

案例演示实现Runnable接口创建多线程

# 12.2.2  实现Runnable接口创建多线程

public class Example03 {
           public static void main(String[] args) {
	MyThread03 myThread = new MyThread03(); // 创建MyThread03的实例对象
	Thread thread = new Thread(myThread);    // 创建线程对象
	thread.start();          // 开启线程，执行线程中的run()方法
	while (true) {
		System.out.println("main()方法在运行");
	}
           }
}

步骤二：定义main()方法，创建MyThread03的实例对象，调用Thread类的构造方法将MyThread03类的实例对象作为参数传入，然后调用start()方法开启新线程执行MyThread03类中的代码，而主线程继续执行main()方法中的代码。代码如下所示：

# 12.2.2  实现Runnable接口创建多线程

运行结果

运行代码，控制台显示的运行结果如下图所示。

由图可知，main()方法和MyThread03类中run()方法都执行了，说明文件12-3实现了多线程。

# 12.2.3  实现Callable接口创建多线程

先定一个小目标！

# 通过Thread类和Runnable接口实现多线程时，需要重写run()方法，但是由于run()方法没有返回值，因此无法从新线程中获取返回结果。为了解决这个问题，Java提供了一个Callable接口，来满足这种既能创建新线程又可以有返回值的需求。

解决run()方法没有返回值的问题

12.2.3  实现Callable接口创建多线程

# 通过实现Callable接口的方式创建并启动线程的主要步骤如下

（1）创建一个Callable接口的实现类，同时重写Callable接口的call()方法。
（2）创建Callable接口的实现类对象。
（3）通过FutureTask线程结果处理类的有参构造方法封装Callable接口实现类对象。
（4）调用参数为FutureTask类对象的Thread有参构造方法创建Thread线程实例。
（5）调用线程实例的start()方法启动线程。

12.2.3  实现Callable接口创建多线程

# 案例演示实现Callable接口创建多线程

下面通过一个案例演示如何通过实现Callable接口的方式来创建多线程。具体步骤如下。

12.2.3  实现Callable接口创建多线程

# class MyThread04 implements Callable<Object> {
    // 重写Callable接口的call()方法
    public Object call() throws Exception {
        int i = 0;
        while (i++ < 5) {
            System.out.println(Thread.currentThread().getName()
                    + "的call()方法在运行");
        }
        return i;
    }
}

步骤一：定义MyThread04类实现Callable接口，重写Runnable接口中的call()方法。代码如下所示：

12.2.3  实现Callable接口创建多线程

# public class Example04 {
        public static void main(String[] args) throws InterruptedException,
            ExecutionException {
        MyThread04 myThread = new MyThread04(); // 创建Callable接口的实例对象
        //使用FutureTask封装MyThread04类
        FutureTask<Object> ft1 = new FutureTask<>(myThread);
        //使用Thread(Runnable target ,String name)构造方法创建线程对象
        Thread thread1 = new Thread(ft1, "thread");
        //调用线程对象的start()方法启动线程
        thread1.start();
        //通过FutureTask对象的方法管理返回值
        System.out.println(Thread.currentThread().getName()+ "的返回结果："+ ft1.get());
        int a=0;
        while (a++<5) {
            System.out.println("main()方法在运行");
        }
    }
}

步骤二：定义main()方法，创建Callable接口的实例，并调用有参的Thread()构造方法创建线程对象thread1；调用线程对象thread1的start()方法启动线程。代码如下所示：

12.2.3  实现Callable接口创建多线程

# 运行结果

运行代码，控制台显示的运行结果如下图所示。

由图可知，通过实现Callable接口的方式实现了多线程并带有返回结果。

12.2.3  实现Callable接口创建多线程

# FutureTask类的继承关系

Callable接口方式实现的多线程是通过FutureTask类来封装和管理返回结果的，FutureTask类的直接父接口是RunnableFuture。从左图可知，FutureTask本质是Runnable接口和Future接口的实现类，其中，Future接口用于管理线程返回结果，它共有5个方法。

12.2.3  实现Callable接口创建多线程

# Future接口的方法及说明

12.2.3  实现Callable接口创建多线程

| 方法声明 | 功能描述 |
|---|---|
| boolean cancel(boolean 
                mayInterruptIfRunning) | 用于取消任务，参数mayInterruptIfRunning表示是否允许取消正在执行却没有执行完毕的任务，如果设置true，则表示可以取消正在执行的任务 |
| boolean isCancelled() | 判断任务是否被取消成功，如果在任务正常完成前被取消成功，则返回 true |
| boolean isDone() | 判断任务是否已经完成，若任务完成，则返回true |
| V get() | 用于获取执行结果，这个方法会发生阻塞，一直等到任务执行完毕才返回执行结果 |
| V get(long timeout, TimeUnit unit) | 用于在指定时间内获取执行结果，如果在指定时间内，还没获取到结果，就直接返回null |

# 12.2.4  Thread类与Runnable接口实现多线程的对比

先定一个小目标！

# 12.2.4  Thread类与Runnable接口实现多线程的对比

通过继承Thread类和实现Runnable接口实现多线程方式会有一定的区别，下面通过一个应用场景来分析说明。

# 12.2.4  Thread类与Runnable接口实现多线程的对比

通过继承Thread类的方式创建多线程

假设售票厅有四个窗口可发售某日某次列车的100张车票，这时，100张车票可以看做共享资源，四个售票窗口同时售票，可以看作四个线程同时运行。为了更直观显示窗口的售票情况，可以调用Thread的currentThread()方法获取当前的线程的实例对象，然后调用getName()方法可以获取到线程的名称。

# 12.2.4  Thread类与Runnable接口实现多线程的对比

class TicketWindow extends Thread {
	private int tickets = 100;
	public void run() {
		while (tickets > 0) { // 通过while循环判断票数并打印语句
		Thread th = Thread.currentThread(); // 获取当前线程
		String th_name = th.getName(); // 获取当前线程的名字
		System.out.println(th_name + " 正在发售第 " + tickets-- + " 张票 ");
		}
	}
}

步骤一：定义TicketWindow类继承Thread类，重写Thread类中的run()方法。代码如下所示：

# 12.2.4  Thread类与Runnable接口实现多线程的对比

public class Example05 {
           public static void main(String[] args) {
	new TicketWindow().start(); // 创建并开启第一个线程对象TicketWindow 
	new TicketWindow().start(); // 创建并开启第二个线程对象TicketWindow 
	new TicketWindow().start(); // 创建并开启第三个线程对象TicketWindow 
	new TicketWindow().start(); // 创建并开启第四个线程对象TicketWindow 
           }
}

步骤二：定义main()方法，创建四个线程并开启四个线程对象。代码如下所示：

# 12.2.4  Thread类与Runnable接口实现多线程的对比

运行结果

运行代码，控制台显示的运行结果如下图所示。

由图可知，每张票都被打印了四次。出现这样现象的原因是四个线程没有共享100张票，而是各自出售了100张票。在程序中创建了四个TicketWindow对象，就等于创建了四个售票线程，每个线程中都有100张票，每个线程在独立地处理各自的资源。

# 12.2.4  Thread类与Runnable接口实现多线程的对比

通过实现Runnable接口的方式实现多线程

由于现实中铁路系统的票资源是共享的，为了保证资源共享，在程序中只能创建一个售票对象，然后开启多个线程去运行同一个售票对象的售票方法，简单来说就是四个线程运行同一个售票程序。接下来，通过实现Runnable接口的方式实现多线程的创建。使用构造方法Thread(Runnable target, String name)在创建线程对象时指定线程的名称。

# 12.2.4  Thread类与Runnable接口实现多线程的对比

class TicketWindow implements Runnable {
           private int tickets = 100;
           public void run() {
	while (tickets > 0) {
		Thread th = Thread.currentThread(); // 获取当前线程
		String th_name = th.getName(); // 获取当前线程的名字
		System.out.println(th_name + " 正在发售第 " + tickets-- + " 张票 ");
	}

           }
}

步骤一：定义TicketWindow类实现Runnable接口，重写Runnable接口中的run()方法。代码如下所示：

# 12.2.4  Thread类与Runnable接口实现多线程的对比

public class Example06 {
           public static void main(String[] args) {
	TicketWindow tw = new TicketWindow(); // 创建TicketWindow实例对象tw
	new Thread(tw, "窗口1").start(); // 创建线程对象并命名为窗口1，开启线程
	new Thread(tw, "窗口2").start(); // 创建线程对象并命名为窗口2，开启线程
	new Thread(tw, "窗口3").start(); // 创建线程对象并命名为窗口3，开启线程
	new Thread(tw, "窗口4").start(); // 创建线程对象并命名为窗口4，开启线程           
            }
}

步骤二：定义main()方法，创建了一个TicketWindow对象tw，并创建了四个线程，每个线程都去调用这个tw对象中的run()方法，这样就可以确保四个线程访问的是同一个tickets变量，共享100张车票。代码如下所示：

# 12.2.4  Thread类与Runnable接口实现多线程的对比

运行结果

运行代码，控制台显示的运行结果如下图所示。

# 12.2.4  Thread类与Runnable接口实现多线程的对比

Thread类与Runnable接口实现多线程的区别

Thread类创建多线程，无法保证多个线程对共享资源的正确操作，而Runnable接口可以保证多个线程对共享资源的正确访问。

# 12.2.4  Thread类与Runnable接口实现多线程的对比

小提示：使用Lambda表达式创建多线程

Thread t = new Thread(() -> {
            }
        });

Lambda表达式可以简化多线程的创建与调用过程，在创建线程时可以指定线程要调用的方法，格式如下。

# 12.2.4  Thread类与Runnable接口实现多线程的对比

案例演示使用Lambda表达式创建多线程

public class Main {
    public static void main(String[] args) {
        Thread t = new Thread(() -> {
            while (true){
                System.out.println("start new thread!");
            }
        });
        t.start(); // 启动新线程
    }
}
class MyThread extends Thread {
    public void run() {
        while (true) { // 通过死循环语句打印输出
            System.out.println("MyThread类的run()方法在运行");
        }
    }
}

# 12.2.5  后台线程

先定一个小目标！

# 12.2.5  后台线程

前台线程和后台线程是一种相对的概念，新创建的线程默认都是前台线程，如果某个线程对象在启动之前执行了setDaemon(true)语句，这个线程就变成一个后台线程。对Java程序来说，只要还有一个前台线程在运行，这个进程就不会结束，如果一个进程中只有后台线程运行，这个进程就会结束。

什么是后台线程

# 12.2.5  后台线程

案例演示程序只有后台线程的情况

下面通过一个案例演示当程序只有后台线程时就会结束的情况。具体步骤如下。

步骤一：定义DamonThread类实现Runnable接口，并重写run()方法。代码如下所示：

class DamonThread implements Runnable {
    public void run() {
        while (true) {
            System.out.println(Thread.currentThread().getName()+ "---在运行");
        }
    }
}

# 12.2.5  后台线程

public class Example07 {
    public static void main(String[] args) {
        // 判断是否为后台线程
        System.out.println("main线程是后台线程吗?"+ Thread.currentThread().isDaemon());
        DamonThread dt = new DamonThread();
        Thread thread = new Thread(dt, "后台线程");
        System.out.println("thread线程默认是后台线程吗?"+ thread.isDaemon());
        // 将线程thread线程对象设置为后台线程
        thread.setDaemon(true);
        thread.start();
        // 模拟主线程main的执行任务
        for (int i = 0; i < 5; i++) {
            System.out.println(i);
        }
    }
}

步骤二：定义main()方法，将线程thread对象设置为后台线程，启动thread线程，模拟主线程main的执行任务。代码如下所示：

# 12.2.5  后台线程

运行结果

运行代码，控制台显示的运行结果如下图所示。

注意：要将某个线程设置为后台线程，必须在该线程启动之前，也就是说setDaemon()方法必须在start()方法之前调用，否则后台线程设置无效。

# 线程的生命周期及状态转换

12.3

# 12.3  线程的生命周期及状态转换

先定一个小目标！

# 12.3  线程的生命周期及状态转换

线程生命周期

在线程整个生命周期中，基本状态一共有6种，分别是新建状态（New）、可运行（Runnable）、锁阻塞（Blocked）、无限等待（Waiting）、计时等待（Timed_Waiting） 、被终止（Teminated），线程的不同状态表明了线程当前正在进行的活动。

# 12.3  线程的生命周期及状态转换

线程生命周期中的五种基本状态

1．新建状态
创建一个线程对象后，该线程对象就处于新建状态。此时还没调用start()方法进行启动，和其他Java对象一样，仅仅由JVM为其分配了内存，没有表现出任何线程的动态特征。

2．可运行状态
可运行状态也称为就绪状态。当线程对象调用了start()方法后，该线程就进入就绪状态。处于就绪状态的线程位于线程队列中，此时它只是具备了运行的条件，能否获得CPU的使用权并开始运行，还需要等待系统的调度。

# 12.3  线程的生命周期及状态转换

3．锁阻塞状态
如果处于可运行的线程获得了CPU的使用权，并开始执行run()方法中的线程执行体，则该线程处于运行状态。一个线程启动后，它可能不会一直处于运行状态，当一个线程试图获取一个对象锁，而该对象锁被其他的线程持有，则该线程进入锁阻塞状态；当该线程持有锁时，该线程将变成可运行状态。

4.无限等待状态
一个线程在等待另一个线程执行一个（唤醒）动作时，该线程进入无限等待状态。进入这个状态后是不能自动唤醒的，必须等待另一个线程调用notify或者notifyAll方法才能够唤醒。

# 12.3  线程的生命周期及状态转换

5．计时等待状态
计时等待状态是具有指定等待时间的等待线程的线程状态。线程由于调用了计时等待的方法（Thread.sleep() 、Object.wait()、Thread.join()、LockSupport.parkNanos()、LockSupport.parkUntil()），并且指定了等待时间而处于计时等待状态。这一状态将一直保持到超时期满或者接收到唤醒通知。
6.被终止状态
被终止状态是终止线程的线程状态。线程因为run()方法正常退出而死亡，或者因为没有捕获的异常终止了run()方法而完成执行。

# 12.3  线程的生命周期及状态转换

在程序中，通过一些操作，可以使线程在不同状态之间转换，如图所示。

线程状态转换图

# 线程操作的相关方法

12.4

# 12.4.1  线程的优先级

先定一个小目标！

# 12.4.1  线程的优先级

线程的优先级

在应用程序中，如果要对线程进行调度，最直接的方式就是设置线程的优先级。优先级越高的线程获得CPU执行的机会越大，而优先级越低的线程获得CPU执行的机会越小。线程的优先级用1~10之间的整数表示，数字越大优先级越高。除了可以直接使用数字表示线程的优先级，还可以使用Thread类中提供的三个静态常量表示线程的优先级。

# 12.4.1  线程的优先级

Thread类的优先级常量

| Thread类的优先级常量 | 功能描述 |
|---|---|
| static int MAX_PRIORITY | 表示线程的最高优先级，值为10 |
| static int MIN_PRIORITY | 表示线程的最低优先级，值为1 |
| static int NORM_PRIORITY | 表示线程的默认优先级，值为5 |

# 12.4.1  线程的优先级

Thread类的setPriority(int newPriority)方法

程序在运行期间，处于就绪状态的每个线程都有自己的优先级，例如，主线程具有普通优先级。然而线程优先级不是固定不变的，可以通过调用Thread类的setPriority(int newPriority)方法进行设置，setPriority()方法中的参数newPriority接收的是1~10之间的整数或者Thread类的三个静态常量。

# 12.4.1  线程的优先级

案例演示不同优先级的两个线程的运行情况

下面通过一个案例演示不同优先级的两个线程在程序中的运行情况。具体步骤如下。

步骤一：定义MaxPriority类并实现Runnable接口。在MaxPriority中，使用for循环打印正在发售的票数。代码如下所示：

class MaxPriority implements Runnable {
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println(Thread.currentThread().getName() + "正在输出：" + i);
        }
    }
}

# 12.4.1  线程的优先级

class MinPriority implements Runnable {
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println(Thread.currentThread().getName() + "正在输出：" + i);
        }
    }
}

步骤二：定义MinPriority类并实现Runnable接口。在MinPriority中，使用for循环打印正在发售的票数。代码如下所示：

# 12.4.1  线程的优先级

public class Example08 {
    public static void main(String[] args) {
        // 创建两个线程
        Thread minPriority = new Thread(new MinPriority(), "优先级较低的线程");
        Thread maxPriority = new Thread(new MaxPriority(), "优先级较高的线程");
        minPriority.setPriority(Thread.MIN_PRIORITY); 	// 设置线程的优先级为1
        maxPriority.setPriority(Thread.MAX_PRIORITY); 	// 设置线程的优先级为10
        // 开启两个线程
        maxPriority.start();
        minPriority.start();
    }
}

步骤三：定义main()方法，创建两个线程，分别设置线程的优先级，然后开启线程。代码如下所示：

# 12.4.1  线程的优先级

运行结果

运行代码，控制台显示的运行结果如下图所示。

由图可知，优先级较高的maxPriority线程先运行了，运行完毕后优先级较低的minPriority线程才开始运行。所以优先级越高的线程获取CPU切换时间片的机率越大。

# 12.4.1  线程的优先级

使用线程优先级需要注意的是

虽然Java提供了10个线程优先级，但是这些优先级需要操作系统的支持，不同的操作系统对优先级的支持是不一样的，操作系统中的线程优先级不会和Java中线程优先级一一对应，因此，在设计多线程应用程序时，其功能的实现一定不能依赖于线程的优先级，而只能把线程优先级作为一种提高程序效率的手段。

# 12.4.2  线程休眠

先定一个小目标！

# 12.4.2  线程休眠

什么是线程休眠

线程休眠指让当前线程暂停执行，从运行状态进入阻塞状态，将CPU资源让给其他线程的一种调度方式，可以调用线程的操作方法sleep()来实现线程休眠，sleep()方法是java.lang.Thread类中定义的静态方法。使用sleep()方法时需要指定当前线程休眠的时间，传入一个long类型的数据作为休眠时间，单位为毫秒，并且任意一个线程的实例化对象都可以调用该方法。

# 12.4.2  线程休眠

案例演示使用sleep()方法实现线程休眠

下面通过一个案例演示sleep()方法在程序中的使用。具体步骤如下。

# 12.4.2  线程休眠

class SleepThread implements Runnable {
         public void run() {
	for (int i = 1; i <= 8; i++) {
	      if (i == 3) {
	            try {
		Thread.sleep(2000); // 当前线程休眠2秒
	            } catch (InterruptedException e) {
		e.printStackTrace();
	            }
	      }
	      System.out.println("SleepThread线程正在输出:" + i);
	      try {
	             Thread.sleep(500); // 当前线程休眠500毫秒
	      catch (Exception e) {
	             e.printStackTrace();
	      }
	}
         }
}

步骤一：定义SleepThread类并实现Runnable接口。重写run()方法，在run()方法中使用for循环打印线程输出语句；使用if判断当变量i=3时，调用sleep()方法线程休眠2000毫秒。代码如下所示：

# 12.4.2  线程休眠

public class Example09 {
         public static void main(String[] args) throws Exception {
         // 创建一个线程
         new Thread(new SleepThread()).start();
         for (int i = 1; i <= 8; i++) {
	if (i == 5) {
	        Thread.sleep(2000);  // 当前线程休眠2000毫秒
	}
	System.out.println("主线程正在输出:" + i);
	Thread.sleep(500); // 当前线程休眠500毫秒
         }
         }
}

步骤二：定义main()方法，使用new关键词创建SleepThread线程并启动，使用for循环打印主线程的输出语句，使用if判断当变量i=5时，线程休眠2000毫秒。代码如下所示：

# 12.4.2  线程休眠

运行结果

运行代码，控制台显示的运行结果如图所示。

由图可知，主线程输出2后，SleepThread类线程没有交替输出3，而是主线程接着输出了3和4，这说明了当i等于3时，SleepThread类线程进入了休眠状态。对于主线程也一样，当i等于5时，主线程会休眠2000毫秒。

# 12.4.2  线程休眠

使用sleep()方法需要注意的是

sleep()是静态方法，只能控制当前正在运行的线程休眠，而不能控制其他线程休眠。当休眠时间结束后，线程就会返回到就绪状态，而不是立即开始运行。

# 12.4.3  线程插队

先定一个小目标！

# 12.4.3  线程插队

什么是线程插队

线程插队指将某个线程插入到当前线程中，由两个线程交替执行变成两个线程顺序执行，即一个线程执行完毕之后再来执行第二个线程，可以通过调用线程对象的join()方法来实现线程插队。

# 12.4.3  线程插队

线程插队的执行过程

假设有两个线程，线程甲和线程乙。线程甲在执行到某个时间点的时候调用线程乙的join()方法，则表示从当前时间点开始CPU资源被线程乙独占，线程甲进入阻塞状态。直到线程乙执行完毕，线程甲进入就绪状态，等待获取CPU资源进入运行状态继续执行。

# 12.4.3  线程插队

使用join()方法案例演示

1 public static void main(String[] args) throws InterruptedException {
 2        Thread thread = new Thread(new JoinRunnable(),"thread");// 创建线程
 3        thread.start();                             // 开启thread线程
 4        for (int i = 1; i <= 5; i++) {
 5            System.out.println(Thread.currentThread().getName()+"输出："+i);
 6            if (i == 2) {
 7                thread.join(); 		// 调用join()方法
 8            }
 9        }
 10 }
 11 class JoinRunnable implements Runnable {
 12    public void run() {
 13        for (int i = 1; i <= 3; i++) {
 14            System.out.println(Thread.currentThread().getName()+"输出："+i);
 15        }
 16    }
 17 }

下面通过一个案例演示join()方法在程序中的使用。具体代码如下所示。

# 12.4.3  线程插队

运行结果

运行代码，控制台显示的运行结果如图所示。

由图可以看出，当main线程输入2以后，thread线程就开始执行，直到执行完毕，main线程才继续执行。

# 12.4.3  线程插队

Thread类的join(long millis)方法

Thread类除了提供一个无参数的线程插队join()方法外，还提供了带有时间参数的线程插队方法join(long millis)。当执行带有时间参数的join(long millis)进行线程插队时，必须等待插入的线程指定时间过后才会继续执行其他线程。

# 12.4.3  线程插队

join()和join(long millis)的区别

join()表示在被调用线程执行完成之后才能执行其他线程。join(long millis)则表示被调用线程执行millis毫秒之后，无论是否执行完毕，其他线程都可以和它来争夺CPU资源。

# 12.4.3  线程插队

使用join(long millis)方法案例演示

步骤一：上面案例main()方法中的join()方法改为join(long millis)方法，第7行代码修改如下所示：

thread.join(3000); // 调用join()方法并将参数设置为3000

# 12.4.3  线程插队

步骤二：上面案例JoinRunnable类中的第14行替换为如下所示的代码：

try {
 	Thread.currentThread().sleep(1500);
 } catch (InterruptedException e) {
 	e.printStackTrace();
 }
 System.out.println(Thread.currentThread().getName()+"输出："+i);

# 12.4.3  线程插队

运行结果

运行代码，控制台显示的运行结果如图所示。

# 12.4.3  线程插队

运行结果分析

由图可以看到当main线程执行到i=2时，thread线程插队到了main线程。Thread线程插队是通过调用join(3000)方法实现的。从插队开始thread线程独占CPU资源执行3000毫秒之后，main线程继续与thread线程抢占资源。因为thread线程每次执行会休眠1500毫秒，所以看到的结果是执行了两次thread线程之后，main线程再次进入就绪状态抢占CPU资源。

# 12.4.4  线程让步

先定一个小目标！

# 12.4.4  线程让步

什么是线程让步

线程让步是指在某个特定的时间点，让线程暂停抢占CPU资源的行为，即从运行状态或就绪状态到阻塞状态，从而将CPU资源让给其他线程使用。可以通过调用yield()方法来实现线程让步。

# 12.4.4  线程让步

线程让步的执行过程

假设有两个线程，线程甲和线程乙。线程甲和线程乙在交替执行，在某个时间点线程甲做出让步，让线程乙占用了CPU资源，执行其业务逻辑。线程乙执行完毕之后，线程甲会再次进入就绪状态，争夺CPU资源。

# 12.4.4  线程让步

案例演示使用yield()方法实现线程让步

线程让步可以使用yield()方法来实现，下面通过一个案例演示yield()方法在程序中的使用。具体步骤如下。

# 12.4.4  线程让步

class YieldThread extends Thread {
    // 定义一个有参的构造方法
    public YieldThread(String name) {
        super(name); 						// 调用父类的构造方法
    }
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println(Thread.currentThread().getName()+"---"+i);
            if (i == 2) {
                System.out.print("线程让步:");
                Thread.yield(); 	// 线程运行到此，作出让步
            }
        }
    }
}

步骤一：定义YieldThread类继承Thread类，然后定义一个有参的构造方法，重写run()方法，在run()方中使用if判断当变量i=2时，调用yield()方法让线程运行到此时作出让步。代码如下所示：

# 12.4.4  线程让步

public class Example12 {
    public static void main(String[] args) {
        // 创建两个线程
        Thread thread1 = new YieldThread("thread1");
        Thread thread2 = new YieldThread("thread2");
        // 开启两个线程
        thread1.start();
        thread2.start();
    }
}

步骤二：定义main()方法，创建两个线程并开启线程，两个线程优先级相同。代码如下所示：

# 12.4.4  线程让步

运行结果

运行代码，控制台显示的运行结果如图所示。

# 12.4.4  线程让步

运行结果分析

从上图的运行结果可以看出，当线程thread1输出2以后，会做出让步，线程thread2获得执行权，同样，线程thread2输出2后，也会做出让步，线程thread1获得执行权。

# 12.4.4  线程让步

yield()方法的弊端

通过yield()方法可以实现线程让步，让当前正在运行的线程失去CPU使用权，让系统的调度器重新调度一次，由于JVM默认采用抢占式调度模型，所有线程都会再次抢占CPU资源使用权，所以在执行线程让步后并不能保证立即执行其他线程，CPU可能会有一段空闲时间。

# 12.4.5  线程中断

先定一个小目标！

# 12.4.5  线程中断

什么是线程中断

线程中断就是线程在执行过程中，通过手动操作来停止该线程。例如当用户在执行一次操作时，因为网络问题导致延迟，则对应的线程对象就一直处于运行状态。如果用户希望结束这个操作，即终止该线程，就要使用线程中断机制了。

# 12.4.5  线程中断

线程中断的两个方法

public void interrupt()：表示中断当前线程对象。每个线程对象都是通过一个标志位来判断当前是否为中断状态。
public boolean isInterrupted()：表示用来获取当前线程对象的标志位的。该方法有true和false两个返回值，true表示清除了标志位，当前线程对象已经中断；false表示没有清除标志位，当前对象没有中断。

# 12.4.5  线程中断

当一个线程对象处于不同的状态时，中断机制也是不同的。下面通过案例来演示不同生命周期状态下的线程中断，首先演示线程新建状态（实例化线程对象，但并未启动线程）下中断线程，然后演示线程运行状态（实例化线程对象，并启动该线程）下中断线程。

# 12.4.5  线程中断

线程新建状态下中断线程

public class Example13 {
     public static void main(String[] args) {
         Thread thread=new Thread();
         thread.interrupt();//执行线程中断
         //向控制台打印当前线程是否中断
         System.out.println(thread.isInterrupted());
     }
 }

下面通过案例来演示线程新建状态下中断线程。具体代码如下所示。

# 12.4.5  线程中断

运行结果

运行代码，控制台显示的运行结果如图所示。

在图中可以看到控制台打印了false，表示当前线程并未中断。因为当前线程状态是未启动状态，不可能中断，不需要清除标志位，所以isInterrupted()的返回值为false。

# 12.4.5  线程中断

线程运行状态下中断线程

public class Example14 {
     public static void main(String[] args) {
        Thread thread = new Thread(new Runnable(){
             public void run() {
                 for (int i=0;i<10;i++){
                     if (i==5){
                         Thread.currentThread().interrupt();
                         //向控制台打印线程是否中断
                         System.out.println("thread线程是否已中断----"
  		+Thread.currentThread().isInterrupted());
                     }
                 }
             }
         }); 			// 创建MyThread的实例对象
         thread.start();		//启动thread对象
     }
 }

下面通过案例演示线程运行状态下中断线程，在循环输出语句中，当i=5时中断线程。具体代码如下所示。

# 12.4.5  线程中断

运行结果

运行代码，控制台显示的运行结果如图所示。

在图中可以看到控制台打印了true，表示thread线程已中断。

# 线程同步

12.5

# 12.5.1  线程安全

先定一个小目标！

# 12.5.1  线程安全

案例说明

假设售票厅有四个窗口可发售某日某次列车的100张车票，这时100张车票可以看做共享资源，在程序中只能创建一个售票对象，然后开启多个线程去运行同一个售票对象的售票方法，简单来说就是四个线程运行同一个售票程序。

# 12.5.1  线程安全

案例分析

上述售票案例中，极有可能碰到“意外”情况，例如一张票被打印多次，或者打印出的票号为0甚至负数。这些“意外”都是由多线程操作共享资源ticket所导致的线程安全问题。模拟上述所说的“意外”情况。假设四个窗口同时出售10张票，并在售票的代码中使用sleep()方法，令每次售票时线程休眠300毫秒。具体代码如下。

# 12.5.1  线程安全

class SaleThread implements Runnable {
         private int tickets = 10; 	// tickets表示总票数：10张票
         public void run() {
 	while (tickets > 0) {
 	         try {
 		Thread.sleep(300); //线程休眠300毫秒
 	         } catch (InterruptedException e) {
 		e.printStackTrace();
 	         }
 	         System.out.println(Thread.currentThread().getName() + "---卖
 		+"出的票"+ tickets--);
 	}
         }
 }

步骤一：定义SaleThread类并实现Runnable接口；定义私有int类型变量tickets，表示总票数，初始值为10；重写run()方法，在run()方法中使用while循环售票；调用sleep()方法使线程休眠300毫秒，用于模拟售票过程中线程的延迟；具体代码如下所示：

# 12.5.1  线程安全

public class Example15 {
            public static void main(String[] args) {
 	SaleThread saleThread = new SaleThread(); // 创建SaleThread对象
 	// 创建并开启四个线程
 	new Thread(saleThread, "线程一").start();
 	new Thread(saleThread, "线程二").start();
 	new Thread(saleThread, "线程三").start();
 	new Thread(saleThread, "线程四").start();
            }
 }

步骤二：定义main()方法，创建并开启四个线程，用于模拟四个售票窗口。具体代码如下所示：

# 12.5.1  线程安全

运行结果

运行代码，控制台显示的运行结果如图所示。

# 12.5.1  线程安全

运行结果分析

从上图可以看出，最后打印售出的票出现了0和负数，这种现象是不应该出现的，原因是在售票程序的while循环中调用了sleep()方法，出现了线程延迟。假设当票号减为1时，线程1获取了CPU执行权，出售1号票，对票号进行判断后，进入while循环，在售票之前调用sleep()方法进入休眠；线程1休眠之后，线程2获取了CPU执行权，会进行售票，由于此时票号仍为1，所以线程2也会进入循环。同理，线程3和线程4也会进入while循环。休眠结束后，四个线程都会继续售票，这样就相当于将票号减了四次，因此结果会出现0和负数这样的票号。

# 12.5.2  同步代码块

先定一个小目标！

# 12.5.2  同步代码块

线程安全问题其实就是由多个线程同时处理共享资源所导致的。要想解决线程安全问题，必须保证在任何时刻只能有一个线程访问共享资源。为了实现多个线程处理同一个资源，在Java中提供了同步机制。当多个线程使用同一个共享资源时，可以将处理共享资源的代码放在一个使用synchronized关键字修饰的代码块中，这个代码块被称作同步代码块。

# 12.5.2  同步代码块

同步代码块的语法格式

使用synchronized关键字创建同步代码块的语法格式如下。

synchronized(lock){
	操作共享资源代码块
}

在上面的代码中，lock是一个锁对象，它是同步代码块的关键，相当于为同步代码加锁。当某一个线程执行同步代码块时，其他线程将无法执行，进入阻塞状态。当前线程执行完后，再与其他线程重新抢夺CPU的执行权，抢到CPU执行权的线程将进入同步代码块，执行其中的代码。以此循环往复，直到共享资源被处理完为止。这个过程就好比一个公用电话亭，只有前一个人打完电话出来后，后面的人才可以打。

# 12.5.2  同步代码块

案例演示synchronized同步代码块

下面对12.5.1中的售票案例进行修改，将用于售票的代码放在synchronized同步代码块中。使用同步代码块解决线程安全的问题。具体如下。

# 12.5.2  同步代码块

class Ticket1 implements Runnable {
    private int tickets = 10; // 定义变量tickets，并赋值10
    Object lock = new Object(); // 定义任意一个对象，用作同步代码块的锁
    public void run() {
        while (true) {
            synchronized (lock) { // 定义同步代码块
                try {
                    Thread.sleep(300); // 经过的线程休眠300毫秒
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                if (tickets > 0) {
                    System.out.println(Thread.currentThread().getName()+ "---卖出的票" + tickets--);
                } else { // 如果 tickets小于0，跳出循环
                    break;
                }
            } } } }

步骤一：修改上节中的案例，将有关tickets变量的操作全部都放到同步代码块中。为了保证线程持续执行，将同步代码块放在死循环中，直到ticket<0时跳出循环。代码如下：

# 12.5.2  同步代码块

public class Example16 {
    public static void main(String[] args) {
        Ticket1 ticket = new Ticket1(); // 创建Ticket1对象
        // 创建并开启四个线程
        new Thread(ticket, "线程一").start();
        new Thread(ticket, "线程二").start();
        new Thread(ticket, "线程三").start();
        new Thread(ticket, "线程四").start();
    }
}

步骤二：定义main()方法，创建并开启四个线程，用于模拟四个售票窗口。代码如下所示：

# 12.5.2  同步代码块

运行结果

运行代码，控制台显示的运行结果如图所示。

从图可以看出，售出的票不再出现0和负数的情况，这是因为售票的代码实现了同步，之前出现的线程安全问题得以解决。

# 12.5.2  同步代码块

使用同步代码块注意事项

同步代码块中的锁对象可以是任意类型的对象，但多个线程共享的锁对象必须是相同的一个。“任意”说的是共享锁对象的类型。锁对象的创建代码不能放到run()方法中，否则每个线程运行到run()方法都会创建一个新对象，这样每个线程都会有一个不同的锁，每个锁都有自己的标志位，这样线程之间便不能产生同步的效果。

# 12.5.3  同步方法

先定一个小目标！

# 12.5.3  同步方法

同步方法的语法格式

除了修饰代码块，sychronized关键字同样可以修饰方法，被synchronized关键字修饰的方法为同步方法。同步方法和同步代码块一样，同一时刻，只允许一个线程调用同步方法。synchronized关键字修饰方法的具体语法格式如下：

synchronized 返回值类型 方法名([参数1,...]){ }

# 12.5.3  同步方法

案例演示synchronized同步方法

下面对12.5.2中的售票案例进行修改，在Ticket1类中定义一个同步方法saleTicket()，用于实现售票功能。使用同步方法解决线程安全的问题。具体如下。

# 12.5.3  同步方法

private synchronized void saleTicket() {
        if (tickets > 0) {
            try {
                Thread.sleep(300); // 经过的线程休眠300毫秒
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println(Thread.currentThread().getName() + "---卖出的票"
                    + tickets--);
        }
    }

步骤一：将售票代码抽取为售票方法saleTicket()，并用synchronized关键字修饰saleTicket()方法。代码如下所示：

# 12.5.3  同步方法

......//省略main方法，参考12.5.2即可
 // 定义Ticket1类实现Runnable接口
 class Ticket1 implements Runnable {
         private int tickets = 10;
         public void run() {
               while (true) {
 	 saleTicket(); // 调用售票方法
 	 if (tickets <= 0) {
 	       break;
 	 }
               }
         }
  }

步骤二：定义Ticket1类实现Runnable接口，在重写的run()方法中的while循环中调用抽取的售票方法saleTicket()。省略定义main()方法的步骤，参考12.5.2即可。具体代码如下所示：

# 12.5.3  同步方法

运行结果

运行代码，控制台显示的运行结果如图所示。

从图可以看出，同样没有出现0号和负数号的票，说明同步方法实现了和同步代码块一样的效果。

# 多学一招

同步方法的锁

读者可能会有这样的疑问：同步代码块的锁是自己定义的任意类型的对象，那么同步方法是否也存在锁？如果有，它的锁是什么呢？答案是肯定的，同步方法也有锁，它的锁就是当前调用该方法的对象，也就是this指向的对象。这样做的好处是，同步方法被所有线程所共享，方法所属的对象相对于所有线程来说是唯一的，从而保证了锁的唯一性。当一个线程执行同步方法时，其他的线程就不能进入该方法中，直到这个线程执行完同步方法为止，从而达到线程同步的效果。

# 多学一招

同步方法的锁

有时候需要同步的方法是静态方法，静态方法不需要创建对象就可以直接用“类名.方法名()”的方式调用。这时候读者就会有一个疑问，如果不创建对象，静态同步方法的锁就不会是this，那么静态同步方法的锁是什么？Java中静态方法的锁是该方法所在类的class对象，class对象在装载该类时自动创建，该对象可以直接用类名.class的方式获取。

# 多学一招

同步方法的锁

同步代码块和同步方法解决多线程问题有好处也有弊端。同步解决了多个线程同时访问共享数据时的线程安全问题，只要加上同一个锁，在同一时间内只能有一个线程执行。但是线程在执行同步代码时每次都会判断锁的状态，非常消耗资源，效率较低。

# 12.5.4  死锁问题

先定一个小目标！

# 12.5.4  死锁问题

什么是死锁

有这样一个场景：一个中国人和一个美国人在一起吃饭，美国人拿了中国人的筷子，中国人拿了美国人的刀叉，两个人开始争执不休：
中国人：“你先给我筷子，我再给你刀叉！”
美国人：“你先给我刀叉，我再给你筷子！”
……
结果可想而知，两个人都吃不到饭。这个例子中的中国人和美国人相当于不同的线程，筷子和刀叉就相当于锁。两个线程在运行时都在等待对方的锁，这样便造成了程序的停滞，这种现象称为死锁。

# 12.5.4  死锁问题

案例演示死锁问题

根据描述的中国人和美国人吃饭的案例，模拟死锁问题。具体如下。

# 12.5.4  死锁问题

class DeadLockThread implements Runnable {
    static Object chopsticks = new Object();    // 定义Object类型的chopsticks锁对象
    static Object knifeAndFork = new Object();  // 定义Object类型的knifeAndFork锁对象
    private boolean flag;                           // 定义boolean类型的变量flag
    DeadLockThread(boolean flag) { 	   // 定义有参的构造方法
        this.flag = flag;
    }

步骤一：定义DeadLockThread类实现Runnable接口，创建Chinese和American两个线程，分别执行run()方法中if和else代码块中的同步代码块。if中设置Chinese线程中拥有chopsticks锁，只有当Chinese线程获得knifeAndFork锁后才能执行完毕；else中设置American线程拥有knifeAndFork锁，只有获得American线程获得chopsticks锁后才能执行完毕。代码如下所示：

# 12.5.4  死锁问题

public void run() {
        if (flag) {
            while (true) {
                synchronized (chopsticks) {        // chopsticks锁对象上的同步代码块
                    System.out.println(Thread.currentThread().getName()+ "---if---chopsticks");
                    synchronized (knifeAndFork) { // knifeAndFork锁对象上的同步代码块
                        System.out.println(Thread.currentThread().getName()+ "---if---knifeAndFork");
                    }
                }
            }
        } else {
            while (true) {
                synchronized (knifeAndFork) {    // knifeAndFork锁对象上的同步代码块
                    System.out.println(Thread.currentThread().getName()+ "---else---knifeAndFork");
                    synchronized (chopsticks) { // chopsticks锁对象上的同步代码块
                        System.out.println(Thread.currentThread().getName()+ "---else---chopsticks");
                    }
                }
            }
        } } }

# 12.5.4  死锁问题

public class Example18 {
    public static void main(String[] args) {
        // 创建两个DeadLockThread对象
        DeadLockThread d1 = new DeadLockThread(true);
        DeadLockThread d2 = new DeadLockThread(false);
        // 创建并开启两个线程
        new Thread(d1, "Chinese").start();   // 创建开启线程Chinese
        new Thread(d2, "American").start(); // 创建开启线程American
    }
}

步骤二：定义main()方法，创建两个DeadLockThread对象，然后创建并开启两个线程。代码如下所示：

# 12.5.4  死锁问题

运行结果

运行代码，控制台显示的运行结果如图所示。

从图可以看出，两个线程都需要对方所占用的锁，但是都无法释放自己所拥有的锁，于是这两个线程都处于挂起状态，从而造成了死锁。

# 12.5.5  重入锁

先定一个小目标！

# 12.5.5  重入锁

重入锁的语法格式

重入锁（ReentrantLock）的作用类似于synchronized关键字，synchronized是通过JVM实现的，而重入锁通过JDK实现。顾名思义，重入锁指可以给同一个资源添加多个锁，并且释放锁的方式与synchronized也不同。synchronized的锁是线程执行完毕之后会自动释放的，而ReentrantLock的锁必须手动释放。重入锁的语法格式如下所示：

private ReentrantLock reentrantLock = new   
 ReentrantLock();
 reentrantLock.lock();		//加锁
 //需要锁的数据
 reentrantLock.unlock();		//释放锁

# 12.5.5  重入锁

案例演示重入锁

下面修改12.5.3中的案例，使用重入锁模拟多个窗口售票。具体如下。

# 12.5.5  重入锁

private  void saleTicket() {
        //调用lock()方法为票数加锁
        reentrantLock.lock();
        if (tickets > 0) {
            try {
                Thread.sleep(300); // 经过的线程休眠300毫秒
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println(Thread.currentThread().getName() + "---卖出的票"
                    + tickets--);
        }
        //调用lock()方法为票数释放锁
        reentrantLock.unlock();
    }

步骤一：定义一个同步方法saleTicket()，在saleTicket()方法中，调用lock()方法为票数加锁；调用lock()方法为票数释放锁。代码如下所示：

# 12.5.5  重入锁

class ReentrantLockTest implements Runnable {
    private int tickets = 10;
    private ReentrantLock reentrantLock = new ReentrantLock();
    public void run() {
        while (true) {
            saleTicket(); // 调用售票方法
            if (tickets <= 0) {
                break;
            }
        }
    }
 }

步骤二：定义ReentrantLockTest类实现Runnable接口，创建ReentrantLock类的对象reentrantLock；调用售票方法saleTicket()。代码如下所示：

# 12.5.5  重入锁

public class Example19 {
    public static void main(String[] args) {
        // 创建ReentrantLockTest对象
        ReentrantLockTest reentrantLockTest = new ReentrantLockTest(); 
        // 创建并开启四个线程
        new Thread(reentrantLockTest,"线程一").start();
        new Thread(reentrantLockTest,"线程二").start();
        new Thread(reentrantLockTest,"线程三").start();
        new Thread(reentrantLockTest,"线程四").start();
    }
}

步骤三：定义main()方法，创建ReentrantLockTest对象，然后创建并开启四个线程，模拟多个窗口售票。代码如下所示：

# 12.5.5  重入锁

运行结果

运行代码，控制台显示的运行结果如图所示。

从图可以看出，运行结果与使用synchronized的结果是一致的。如果读者需要在此基础上添加多把锁，只需要调用lock()方法即可。注意：使用重入锁是加了几把锁就必须释放几把锁，如果不释放会导致线程处于阻塞状态。

# 本章小结

本章详细介绍了多线程的基础知识，首先介绍进程与线程两个概念；其次介绍了线程创建的三种方式及各自优缺点，之后介绍了后台线程；接着讲解了线程的生命周期与状态转换；然后从线程的优先级、休眠、插队、让步和中断五方面讲解了线程的相关方法；最后从多线性的线程安全、同步代码块、同步方法和如何解决死锁问题几方面介绍了多线程的同步。通过本章的学习，读者可以对Java多线程有一个初步的认识，熟练掌握好这些知识，对以后的编程开发大有脾益。

本

章

小

结
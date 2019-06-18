# 多线程
## 1. 前传和定义:
&emsp;&emsp;&emsp;&emsp; 多线程是计算机在同一时间点可以同时执行多个任务。例如：边听音乐，边看电子书。在单核 cpu 系统中,操作系统会根据很小的时间间隔交替执行多个任务,像是应用程序就像在并行运行一样。但是多个 CPU 才能做到真正意义上的并发执行。       
   学习java时会使用 main 方法做一个启动程序的入口,代码会根据书写的逻辑进行执行,这种属于单线程的程序。在真实的互联网开发过程中，为了更快的相应用户，使用多线程进行处理。当页面调用后端服务时，后端服务直接将数据返回，后续其他的步骤，添加新加一个线程（子任务）去处理。

## 2. 线程和进程的区别:
&emsp;&emsp;&emsp;&emsp; 进程是一个应用程序在计算机上的一次执行活动。例如： 运行的音乐播放器，浏览器。运行一个进程，操作系统就启动了一个进程，进程加载程序代码，分配程序所用的资源环境，每个进程都有独立的代码和数据空间，进程可以由多条路径并发执行，并发执行多条路径称为多线程。
    线程是比进程更小的执行单位，多个线程共享进程的代码，数据空间， 但是每个线程都有独立的运行栈和程序计数器。  
&emsp;&emsp;&emsp;&emsp;进程是每个独立运行程序在计算器上的一次执行活动,线程是进程中一个执行路径,线程依赖进程而存在。
## 3. 并行和并发的区别:
&emsp;&emsp;&emsp;&emsp; 吃饭吃到一半，电话来了，一直等到吃完之后才能去接电话，这种只是单纯的程序。    
&emsp;&emsp;&emsp;&emsp; 吃饭吃到一半，电话来了，去接电话，等你接完电话在吃饭，这种是属于并发。   
&emsp;&emsp;&emsp;&emsp; 吃饭吃到一半，电话来了，边接电话边吃饭，这种是属于并行。   
&emsp;&emsp;&emsp;&emsp;并行是是否有能力同时处理任务的能力。

## 4. 线程的生命周期:
![avatar](./static/java-thread.jpg)

&emsp;&emsp;&emsp;&emsp; 新建状态:     
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 使用 new() 关键字和 Thread 类或者其子类建立一个线程对象后,该线程处在的状态就是`新建状态`。他保持这个状态直到调用 start() 这个方法。    
&emsp;&emsp;&emsp;&emsp; 就绪状态：    
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 当线程调用  start()  方法之后，该线程进入就绪状态，就绪状态的线程处于就绪队列中，等待 jvm 中的调度器进行调用。   
&emsp;&emsp;&emsp;&emsp; 运行状态：    
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 如果就绪状态中，jvm 中的调度器分配资源给了线程,就会调用 run() 方法,此时线程处于运行状态, 处于运行状态的线程最为复杂,他可以编程阻塞状态,就绪状态和死亡状态。     
&emsp;&emsp;&emsp;&emsp; 阻塞状态：    
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 如果一个线程执行了sleep（睡眠）、suspend（挂起）等方法，失去所占用资源之后，该线程就从运行状态进入阻塞状态。在睡眠时间已到或获得设备资源后可以重新进入就绪状态。可以分为三种：

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; &emsp;&emsp;&emsp;* 等待阻塞：运行状态中的线程执行 wait() 方法，使线程进入到等待阻塞状态。     
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; &emsp;&emsp;&emsp;* 同步阻塞：线程在获取 synchronized 同步锁失败(因为同步锁被其他线程占用)。
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; &emsp;&emsp;&emsp;* 其他阻塞：通过调用线程的 sleep() 或 join() 发出了 I/O 请求时，线程就会进入到阻塞状态。当sleep() 状态超时，join() 等待线程终止或超时，或者 I/O 处理完毕，线程重新转入就绪状态。  

&emsp;&emsp;&emsp;&emsp; 死亡状态：    
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 一个运行中的线程执行完任务或者其他条件终止任务之后进入死亡状态。


## 5. 线程的优先级别:
&emsp;&emsp;&emsp;&emsp; 每一个 Java 线程都有一个优先级，这样有助于操作系统确定线程的调度顺序。   
&emsp;&emsp;&emsp;&emsp; Java 线程的优先级是一个整数，其取值范围是 1        （Thread.MIN_PRIORITY ） - 10 （Thread.MAX_PRIORITY ）。                 
&emsp;&emsp;&emsp;&emsp; 默认情况下，每一个线程都会分配一个优先级 NORM_PRIORITY（5）。   
&emsp;&emsp;&emsp;&emsp; 具有较高优先级的线程对程序更重要，并且应该在低优先级的线程之前分配处理器资源。但是，线程优先级不能保证线程执行的顺序，而且非常依赖于平台。

## 6. 创建一个线程:
&emsp;&emsp;&emsp;&emsp; 实现 Runnable() 接口   
&emsp;&emsp;&emsp;&emsp; 继承thread类    
&emsp;&emsp;&emsp;&emsp; 通过 Callable 和 Future 创建线程

## 7. 实现 Runnable() :
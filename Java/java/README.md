# Java Guideline



[JavaDoc](https://docs.oracle.com/javase/8/docs/technotes/tools/windows/javadoc.html)

## Java基础

### 基本概念
#### 数据类型

**基本类型**

int, short, long, boolean, char, String

**包装类型**

Integer, Short, Long, Boolean

* [10个有关String的面试问题](http://www.importnew.com/9622.html)
    >注意String是不可变的，比较一定要用`equals()`方法
* [JAVA 中的 StringBuilder 和 StringBuffer 适用的场景是什么？](https://www.zhihu.com/question/20101840)
    >事实上，很少情况下会用到线程安全的`StringBuffer`
* [深入解析String#intern](https://tech.meituan.com/2014/03/06/in-depth-understanding-string-intern.html)
* [Java常量池详解之一道比较蛋疼的面试题](https://www.cnblogs.com/DreamSea/archive/2011/11/20/2256396.html)
    > Integer的比较要用`equals()`方法，而不能用`==`。

#### 内部类

* [java提高篇(八)----详解内部类](https://www.cnblogs.com/chenssy/p/3388487.html)

#### 接口/抽象类

设计模式建议我们面向接口编程。接口和抽象类也是在框架中经常见到的。

* [java提高篇(五)-----抽象类与接口](https://www.cnblogs.com/chenssy/p/3376708.html)
* [Java 中的接口有什么作用？](https://www.zhihu.com/question/20111251)

空接口，也就是标签接口。接口中虽然没有任何方法，但也是有意义的。如`Serializable`、`EventListener`等

* [Tag or marker interfaces in Java](https://beginnersbook.com/2016/03/tag-or-marker-interfaces-in-java/)
* [Tagging Interfaces in Java](https://stackoverflow.com/questions/1293152/tagging-interfaces-in-java)

>go语言中也有空接口 [11.9 空接口](https://www.kancloud.cn/kancloud/the-way-to-go/72528)

#### 其他
* [Java类/对象初始化及顺序](https://www.jianshu.com/p/cc60f9c6510c)

### 集合
* [由浅入深理解java集合(一)——集合框架 Collection、Map](https://www.jianshu.com/p/589d58033841)

常用的集合有4大类：`List`、`Set`、`Queue`、`Map`

#### List

**常用的List**

非线程安全：
* `ArrayList` ==> 相当于数组
* `LinkedList` ==> 相当于链表

线程安全：
* `CopyOnWriteArrayList`

**参考**
* [Java中的集合（二）：List](https://www.jianshu.com/p/c37a2106bf5b)


#### Set
**常用Set**

非线程安全：
* `HashSet`
* `TreeSet`

线程安全：
* `CopyOnWriteArraySet`

> `CopyOnWriteArraySet`的介绍见**Java并发编程**章节

**参考**
* [Java中的集合（三）：Set](https://www.jianshu.com/p/ed34fc3f23c9)

#### Map

**常用的Map**

非线程安全：
* `HashMap`
* `TreeMap`

线程安全：
* `ConcurrentHashMap`

> `ConcurrentHashMap`的介绍见**Java并发编程**章节

**参考**
* [JDK7与JDK8中HashMap的实现](http://www.importnew.com/23164.html)
    > JDK8中对`HashMap`的实现做了优化，提升了效率
* [如何线程安全的使用 HashMap](https://yemengying.com/2016/05/07/threadsafe-hashmap/)
    > 解释了`HashMap`为什么不是线程安全的
* [集合13-TreeMap使用场景简析](https://www.jianshu.com/p/dd746074f390)
    >`TreeMap`底层使用了红黑树，适合用在需要排序的场景

#### Queue

**常用的Queue**

非线程安全：
* `PriorityQueue`
    >优先队列，适合存储有优先级的数据

线程安全：
* `BlockingQueue` 
    >各种xxxBlockingQueue的接口
* `ArrayBlockingQueue`
    >应用广泛，如生产者-消费者模式，线程池
* `LinkedBlockingDeque`
    >应用广泛，如生产者-消费者模式，线程池
* `SynchronousQueue`
    >一个很奇怪，不存元素的阻塞队列
* `PriorityBlockingQueue` 
    >`PriorityQueue`的线程安全版本
* `DelayQueue`
    >延迟队列

**参考**
* [Java Queue](https://www.jianshu.com/p/efe9052c7ad9)
* [精巧好用的DelayQueue](https://www.cnblogs.com/jobs/archive/2007/04/27/730255.html)
* [深入 DelayQueue 内部实现](https://www.zybuluo.com/mikumikulch/note/712598)

### 动态代理

动态代理不仅有JDK自带的，还有第三方的，如CGLIB。需要知道原理和其不同。

动态代理在Spring框架中有非常广泛的应用

* [Java 动态代理作用是什么？](https://www.zhihu.com/question/20794107)
* [Java Proxy 和 CGLIB 动态代理原理](https://mp.weixin.qq.com/s/caEpFhjE6FnnvoGMCQpU0g)


### 反射

* [Java 反射机制应用实践](https://mp.weixin.qq.com/s/DuPaNtPWWNfhP-LP-oJO8A)
* [关于反射调用方法的一个log](https://rednaxelafx.iteye.com/blog/548536?from=singlemessage&isappinstalled=0)

### 泛型

使用泛型要注意有**类型擦除**的问题

遵守**PECS原则**，来限制泛型的类型

* [Java 泛型详解](https://mp.weixin.qq.com/s/HuSBGkJzBegwW-O0Scum7Q)

### ClassLoader

`ClassLoader`也是一个非常重要的概念

* [深入探讨 Java 类加载器](https://www.ibm.com/developerworks/cn/java/j-lo-classloader/index.html)
* [classloader使用与原理分析](https://liuzhengyang.github.io/2016/09/28/classloader/)
* [假笨说-据说99.99%的人都会答错的类加载的问题](https://mp.weixin.qq.com/s/uyj9UDxR3DfWD3ZCzJrJLQ)

### Java IO

常用到的IO主要分为文件IO和网络IO

网络IO一定要了解NIO，这是Java网络编程的根基

* [Java - IO](https://www.jianshu.com/p/7e23098de835)
* [Java - 网络IO](https://www.jianshu.com/p/fe15720a74fa)
* [Java - NIO](https://www.jianshu.com/p/9d4e89a1bf60)
* [JDK Epoll空轮询bug](https://www.jianshu.com/p/3ec120ca46b2)
* [深入浅出NIO之Channel、Buffer](https://www.jianshu.com/p/052035037297)

直接使用Java NIO进行编程会比较麻烦，既要考虑NIO的正确使用姿势，又要面对网络异常问题，如TCP半包/年包、断线重连、Epoll空轮询Bug等。所以，在需要使用Java进行网络编程时，首先要想到的不是自己去编码，而是用一些现成的网络库。**Netty**就是这样一个网络库，并有一统天下的趋势。



## Java 并发编程
![a0dc1216e0df65bd723a09d38474f0d3.png](evernotecid://BE5E7B4F-1D36-491E-96FC-FEC56D0BA75A/appyinxiangcom/953711/ENResource/p3673)


### 线程
知道怎么创建线程，使用线程是第一步要做的

跟线程相关的有几个类: `Thread`, `Runnable`, `Callable`, `Future`, `FutureTask`

* [Java - 线程 & 线程池](https://www.jianshu.com/p/a1a60974ae61)
* [Java中的Runnable、Callable、Future、FutureTask的区别与示例](https://blog.csdn.net/bboyfeiyu/article/details/24851847)
* [Java 守护线程概述](http://www.importnew.com/26834.html)

使用多线程，通常要响应中断的

* [详细分析 Java 中断机制](https://www.infoq.cn/article/java-interrupt-mechanism)


### 线程池

线程的创建和销毁比较耗时，频繁使用影响性能，这时候就需要已经创建了许多线程的线程池。

使用线程池，相关的类有：

`ThreadPoolExecutor`, `Executor`, `ExecutorService`, `Executors`

需要了解`ThreadPoolExecutor`构造函数每个参数都什么意义和作用

常用`Executors`创建线程池。但是阿里巴巴Java开发手册不建议这样。主要原因在于`Executors`创建的线程池总有各种各样的弊端。

![dbdf573ff818677c91ccc9f1037a99d0.png](evernotecid://BE5E7B4F-1D36-491E-96FC-FEC56D0BA75A/appyinxiangcom/953711/ENResource/p3675)


* [Java线程池](https://www.jianshu.com/p/f9dfab446af9)
* [Java多线程之Executor、ExecutorService、Executors、Callable、Future与FutureTask](https://www.cnblogs.com/zhrb/p/6372799.html)
* [阿里巴巴Java开发手册](http://techforum-img.cn-hangzhou.oss-pub.aliyun-inc.com/%E9%98%BF%E9%87%8C%E5%B7%B4%E5%B7%B4Java%E5%BC%80%E5%8F%91%E6%89%8B%E5%86%8C%28%E7%BB%88%E6%9E%81%E7%89%88%29.pdf)


### 线程安全容器
JUC(java.util.concurrent)包中提供了一些线程安全的容器

#### List
**`CopyOnWriteArrayList`**
>`CopyOnWriteArrayList`对读不加锁，对写先加锁，再复制，复制的时候不影响读，提高了效率

* [并发一枝花之 CopyOnWriteArrayList](http://www.importnew.com/27118.html)
* [CopyOnWriteArrayList详解](https://my.oschina.net/jielucky/blog/167198)

#### Map

`ConcurrentHashMap`
>JDK7中`ConcurrentHashMap`使用了分段锁的方法来保证线程安全，在JDK8中则是使用CAS + synchronized的方式。

`ConcurrentHashMap`在面试中会经常被用到。无论是分段锁的思想，还是后来的CAS无锁思想，都是很值得借鉴和学习的。

* [从ConcurrentHashMap的演进看Java多线程核心技术](http://www.jasongj.com/java/concurrenthashmap/)
* [谈谈ConcurrentHashMap1.7和1.8的不同实现](https://www.jianshu.com/p/e694f1e868ec)
* [深入浅出ConcurrentHashMap1.8](https://www.jianshu.com/p/c0642afe03e0)

`ConcurrentHashMap`的size计算也比较巧妙
* [ConcurrentHashMap 的size方法原理分析](https://zhuanlan.zhihu.com/p/40627259)

#### Set

`CopyOnWriteArraySet`

当然也可以依托于`ConcurrentHashMap`自己实现一个`ConcurrentHashSet`



#### Queue

`BlockingQueue`在生产者-消费者模型中经常被用到。

* [Java Queue](https://www.jianshu.com/p/efe9052c7ad9)
* [解读 Java 并发队列 BlockingQueue](http://www.importnew.com/28053.html)

虽然Java提供了诸多`BlockingQueue`的实现，但是LMAX公司开发的无锁化队列`disruptor`在性能是哪个远高于JDK

* [并发框架Disruptor译文](http://ifeve.com/disruptor/)
* [高性能队列——Disruptor](https://tech.meituan.com/2016/11/18/disruptor.html)
* [为什么Disruptor会那么快?](https://colobu.com/2014/12/22/why-is-disruptor-faster-than-ArrayBlockingQueue/)

#### Atomic
`i++`不是线程安全的。怎样才能获得线程安全的累加呢？

可以使用Atomic类。使用CAS操作确保线程安全，比使用锁的性能高出好多。

* [Java的Atomic类分析](https://blog.csdn.net/goodlixueyong/article/details/51339689)


#### LongAdder

CAS操作的一个缺点是，在并发很高的情况下，失败的概率很高，需要不断重试，导致比较大的消耗。Doug Lea大神又给我们提供了`LongAdder`这样性能更高的类。

* [从LONGADDER看更高效的无锁实现](https://coolshell.cn/articles/11454.html)


### 线程同步

#### 锁

线程同步最先想到的就是锁。

常用的有`synchronized`和`ReentrantLock`。还有实现锁的神级框架`AQS`

* [Java锁 - 导读](https://www.jianshu.com/p/39628e1180a9)

`synchronized`和`ReentrantLock`是学习锁的重点。而二者的比较会经常被提起：
>* `synchronized`能做的，`ReentrantLock`都能做，并且还能做更多。但是`synchronized`依然有用武之地
>* `ReentrantLock`相比`synchronized`的优势是可中断、公平锁、多个锁。这种情况下需要使用`ReentrantLock`。只要是`synchronized`能做到的，还是使用`synchronized`。

参考
* [关于synchronized和ReentrantLock之多线程同步详解](https://www.jianshu.com/p/96c89e6e7e90)

死锁

* [Java 程序死锁问题原理及解决方案](https://www.ibm.com/developerworks/cn/java/j-lo-deadlock/index.html)
* [如何通过编程发现Java死锁](http://www.importnew.com/15307.html)

`AbstractQueuedSynchronizer`(简写为`AQS`)是实现诸多锁，如`ReentrantLock`、`ReadWriteLock`、`CountDownLatch`、`Semaphore`等的基础框架，目的是提供通用的基础功能，如锁定状态、维护FIFO队列等。写的非常牛B(经得住全球coder进行code review的代码啊)，像Doug Lea致敬
* [【死磕Java并发】—–J.U.C之AQS（一篇就够了）](https://juejin.im/entry/5ae02a7c6fb9a07ac76e7b70)
* [AQS框架深入分析](https://blog.csdn.net/vernonzheng/article/details/8275624)

#### CAS

由于加锁和释放锁要切换到内核态，这是一个代价非常大的操作，导致加锁的性能通常不高。因此，一种无锁化的方法被设计了出来，即CAS。

> 锁与高并发是矛盾的。一般来讲，高并发的程序都是要摒弃锁的，像Redis的单线程模型、Nginx的多进程模型等。交易所这种并发量非常高的业务，一般也都是无锁化的

CAS是一种思想，不论是在Java中还是在其他的技术栈中，都有广泛的应用。Java中运用CAS的地方有`Atomic***`变量、JDK8中的`ConcurrentHashMap`等。

同时要注意，CAS也有一些问题，如`ABA`问题。不过这种问题都是容易解决的

* [Java中CAS的使用和实现分析](https://liuzhengyang.github.io/2017/05/11/cas/)
* [深入浅出CAS](https://www.jianshu.com/p/fb6e91b013cc)


#### volatile

`volatile`通常作为一种轻量级的锁的替代品，在性能上，比锁要高出一大截。

但是`volatile`毕竟不是锁。锁要解决的问题有三要素: `原子性`、`顺序性`和`可见性`。`volatile`并不能保证`原子性`，因此适用范围受到一定的限制。


`volatile`最典型的使用场景是实现线程安全的**DCL单例模式**。
* [单例模式 - Singleton Pattern](https://www.jianshu.com/p/f03ba52a4d0e)

在JSR-133中规定了`volatile`的规范，来保证`volatile`的语义。

需要理解`volatile`是如何保证`可见性`和`顺序性`的

* [volatile关键字的作用、原理](https://monkeysayhi.github.io/2016/11/29/volatile%E5%85%B3%E9%94%AE%E5%AD%97%E7%9A%84%E4%BD%9C%E7%94%A8%E3%80%81%E5%8E%9F%E7%90%86/)
* [JSR-133 PDF文档](http://ifeve.com/wp-content/uploads/2014/03/JSR133%E4%B8%AD%E6%96%87%E7%89%88.pdf)

### 线程通信

多线程时，有时会需要同步线程之间的状态，这就涉及到了线程间的通信。

线程间通信的的主要方式有：
* Object.wait()/Object.notify()
* Condition.await()/Condition.signal() 
* CountdownLatch 
* CyclicBarrier 
* Semaphore 

`Condition.await()/signal()`通常作为`Object.wait()/notify()`的上位替代者

参考
* [如何在 Java 中正确使用 wait, notify 和 notifyAll – 以生产者消费者模型为例](http://www.importnew.com/16453.html)
    >wait/notify在JDK源码中应用较多
* [什么时候使用CountDownLatch](http://www.importnew.com/15731.html)
* [Java并发编程：CountDownLatch、CyclicBarrier和Semaphore](https://www.cnblogs.com/dolphin0520/p/3920397.html)


### 并发框架

原来，程序员写一个并发的程序，只能用`ThreadPoolExecutor`。

在Java7中，Doug Lea给我们提供了方便使用的`ForkJoin`并发框架。

Java8中，使用stream，又有免费的`parallelStream`作为并发框架


* [聊聊并发（八）——Fork/Join 框架介绍](https://www.infoq.cn/article/fork-join-introduction)
* [jdk1.8-ForkJoin框架剖析](https://www.jianshu.com/p/f777abb7b251)
* [Java 8 parallel streams with individual thread pools](https://juejin.im/entry/58304932a0bb9f0067bde2be)
* [Common Fork Join Pool and Streams](https://dzone.com/articles/common-fork-join-pool-and-streams)
* [Custom Thread Pools In Java 8 Parallel Streams](https://www.baeldung.com/java-8-parallel-streams-custom-threadpool)

### 协程

[协程，高并发IO的终级杀器(1)](https://zhuanlan.zhihu.com/p/27519705)

## Java 异步编程

Java中有JDK提供的`Future`, `ForkJoin`, `CompletableFuture`, Guava提供的`ListenableFuture`等来实现异步编程

还有`RxJava`, `akka`等框架

* [浅谈Java异步编程](https://zhuanlan.zhihu.com/p/42470582)
* [Java并发 - Future模式](https://www.jianshu.com/p/82ce331b9dfe)
* [JAVA 拾遗--Future 模式与 Promise 模式](https://www.cnkirito.moe/future-and-promise/)

[HTTP服务异步化改造实践](https://mp.weixin.qq.com/s/EEPvF53CVOSRY7w65WOFqw)

Vert.x
Quasar
[次时代Java编程(一) Java里的协程](https://segmentfault.com/a/1190000005342905)
[初创团队选择 Vert.x 的避坑考虑和上手资料](https://zhuanlan.zhihu.com/p/33832486)


## Java 网络编程
![44f7390f5884fd6a514a3b5e5359f045.png](evernotecid://BE5E7B4F-1D36-491E-96FC-FEC56D0BA75A/appyinxiangcom/953711/ENResource/p3671)

Java网络编程是Java体系中的一个重点，而NIO则是Java网络编程的重点。

单纯的NIO使用起来比较复杂，对程序人员素质要求较高，高质量的网络框架是亟需的。`Netty`已经有一统江湖的趋势。

* [Java - 网络IO](https://www.jianshu.com/p/fe15720a74fa)
* [Java - NIO](https://www.jianshu.com/p/9d4e89a1bf60)


## Java 内存模型(JMM)

在JSR-133中规范了Java内存模型(Java Momery Model)。

理解JMM，需要了解几个概念：

* 指令重排
* 内存屏障
* Happens-Before

同时，JMM也对如下关键字做了规范：
* `volatile`
* `final`


参考

* [JSR-133 Java Memory Model - PDF文档](http://ifeve.com/wp-content/uploads/2014/03/JSR133%E4%B8%AD%E6%96%87%E7%89%88.pdf)
* [一文解决内存屏障](https://monkeysayhi.github.io/2017/12/28/%E4%B8%80%E6%96%87%E8%A7%A3%E5%86%B3%E5%86%85%E5%AD%98%E5%B1%8F%E9%9A%9C/)
* [Java内存模型之happens-before](https://www.cnblogs.com/chenssy/p/6393321.html)
* [JVM内存模型、指令重排、内存屏障概念解析](https://www.cnblogs.com/chenyangyao/p/5269622.html)

## Java 调试体系

调试(debug)是编程中经常用到的操作。

处理在开发时，运用IDE的debug模式，运行中的服务也可以被远程debug。

这其中的原理是什么？


**JPDA**
* [第 1 部分，JPDA 体系概览](https://www.ibm.com/developerworks/cn/java/j-lo-jpda1/index.html?ca=drs-)
* [JVMTI 和 Agent 实现](https://www.ibm.com/developerworks/cn/java/j-lo-jpda2/index.html)

**JDI**

* [使用JDI监听Java程序运行](http://liugang594.iteye.com/blog/1397811)
* [Java 调试接口（JDI）](https://www.ibm.com/developerworks/cn/java/j-lo-jpda4/index.html?ca=drs-)

**JVMTI**
* [基于 JVMTI 实现 Java 线程的监控](https://www.ibm.com/developerworks/cn/java/j-lo-jvmti/index.html)

**jstatd**

* [采用 jstatd 监控服务器](https://blog.csdn.net/renfufei/article/details/53187123)

**JMX**
* [JVisualVM 远程连接 JMX 和 jstatd](https://blog.csdn.net/keketrtr/article/details/52292113)

Java Attach
Java Agent
JPDA

`-Xrunjdwp:server=y,transport=dt_socket,address=10002,suspend=n`


## Java 问题定位

![17e6dfa7ee78f45f247f95a3e147660b.png](evernotecid://BE5E7B4F-1D36-491E-96FC-FEC56D0BA75A/appyinxiangcom/953711/ENResource/p3670)

### 问题诊断工具
**Java提供的命令**
* jps
* jinfo
* jstat
* jmap
* jhat
* jstack
* jdb

**Linux命令**
* ps
* top
* lsof
* netstat
* tcpdump
* dmesg
* iostat
* vmstat

* awk
* sed
* grep
* less
* tail


**工具**
* MAT
* JProfiler
* VisualVM
* BTrace
* zprofiler
* Arthas
* Greys
* vjtools
* javOSize
* zprofiler
* gpref


### 常见问题
* CPU飙高
* 内存泄漏
* 服务假死
* 死锁检查
* 频繁GC
* GC耗时长
* 进程消失
* 服务变慢

参考
* [Java 问题定位导读](https://github.com/my1free/qijin-tech-docs/tree/master/java/java/%E9%97%AE%E9%A2%98%E5%AE%9A%E4%BD%8D)


## Java术语简写

* JMI
* JIT
* JNI
* JMS
* RMI
* JMH
* JSR
* JCP
* AOT
* SPI


目前应用最为广泛的框架之一就是JMH，OpenJDK 自身也大量地使用 JMH 进行性能对比，如果你是做 Java API 级别的性能对比，JMH 往往是你的首选

* [Java微基准测试框架JMH](https://www.xncoding.com/2018/01/07/java/jmh.html)
* [[译]使用JMH进行微基准测试：不要猜，要测试！](https://www.hollischuang.com/archives/1072)

* [夸克开源项目分析--对软件开发生态的促进作用](https://mp.weixin.qq.com/s/iSonmEhOkbr4hoU4-xWc-g)



## Java开发手册

IDE插件

## Java测试手册

单元测试
集成测试




[TOC]

JavaDoc

## Java基础

### 基本概念
#### 数据类型

基本类型

int, short, long, boolean, char, String

包装类型

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
PECS原则
类型擦除

* [Java 泛型详解](https://mp.weixin.qq.com/s/HuSBGkJzBegwW-O0Scum7Q)

### Java IO


## Java 并发编程
![a0dc1216e0df65bd723a09d38474f0d3.png](evernotecid://BE5E7B4F-1D36-491E-96FC-FEC56D0BA75A/appyinxiangcom/953711/ENResource/p3673)



### 线程
### 线程池
Java并发 - Executor/ExecutorService/Executors区别和联系 
### 线程安全容器
JUC(java.util.concurrent)包中提供了一些线程安全的容器

#### List
**`CopyOnWriteArrayList`**
>`CopyOnWriteArrayList`对读不加锁，对写先加锁，再复制，复制的时候不影响读，提高了效率

#### Map

`ConcurrentHashMap`
>JDK7中`ConcurrentHashMap`使用了分段锁的方法提升并发，在JDK8中

#### Set

`CopyOnWriteArraySet`

当然也可以依托于`ConcurrentHashMap`自己实现一个`ConcurrentHashSet`



#### Queue

Java并发 - CopyOnWriteArrayList 

Java并发 - ConcurrentHashSet 
Java并发 - BlockingQueue

### 线程同步
锁
CAS
volatile

### 线程通信

Java并发 - wait/notify 
Java并发 - CountdownLatch 
Java并发 - CyclicBarrier 
Java并发 - Condition 
Java并发 - Semaphore 

### 并发框架
Java并发 - ForkJoin 
Java并发 - Stream
akka

## Java 异步编程

Java并发 - Future模式 
Java并发 - Promise 
Java并发 - Callback 
RxJava


## Java 网络编程
![44f7390f5884fd6a514a3b5e5359f045.png](evernotecid://BE5E7B4F-1D36-491E-96FC-FEC56D0BA75A/appyinxiangcom/953711/ENResource/p3671)



## Java 内存模型(JMM)

## Java 问题定位

![17e6dfa7ee78f45f247f95a3e147660b.png](evernotecid://BE5E7B4F-1D36-491E-96FC-FEC56D0BA75A/appyinxiangcom/953711/ENResource/p3670)

**命令**
* ps
* jps
* jstat
* jstack/pstack
jstack：适用于java进程，可以取到所以线程的堆栈dump 
  pstack：适用于所有linux进程，是对gdb的功能封装
* jmap
* jhat
* jinfo
* top
* lsof
* tcpdump

**工具**
* MAT
* vjtools
* JProfiler
* VisualVM
* Arthas
* Greys
* zprofiler
* BTrace

**问题**
* CPU飙高
* 内存泄漏
* 服务假死
* 死锁检查
* 频繁GC
* GC耗时长
* 进程消失

[Java 问题定位](https://github.com/my1free/qijin-tech-docs/tree/master/java/java/%E9%97%AE%E9%A2%98%E5%AE%9A%E4%BD%8D)

## Java 开发

IDE插件

### 开发

### 测试

## Java源码解读

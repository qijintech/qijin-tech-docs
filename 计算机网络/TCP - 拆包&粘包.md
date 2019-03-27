
## 什么是TCP拆包/粘包

![1b78a7b07ea4457c7bdd220369593883.png](evernotecid://BE5E7B4F-1D36-491E-96FC-FEC56D0BA75A/appyinxiangcom/953711/ENResource/p3721)
![03fb35823f352b423c69c4bda39325c6.png](evernotecid://BE5E7B4F-1D36-491E-96FC-FEC56D0BA75A/appyinxiangcom/953711/ENResource/p3722)
![bddc825acca9680c932286219c6556f2.png](evernotecid://BE5E7B4F-1D36-491E-96FC-FEC56D0BA75A/appyinxiangcom/953711/ENResource/p3723)

## TCP拆包/粘包的原因

缓冲区

每个 socket 被创建后，都会分配两个缓冲区，输入缓冲区和输出缓冲区
![cfdbf2d80c6986a4103df1fdc09bfc94.jpeg](evernotecid://BE5E7B4F-1D36-491E-96FC-FEC56D0BA75A/appyinxiangcom/953711/ENNote/p1033?hash=cfdbf2d80c6986a4103df1fdc09bfc94)

write()/send() 并不立即向网络中传输数据，而是先将数据写入缓冲区中，再由TCP协议将数据从缓冲区发送到目标机器。一旦将数据写入到缓冲区，函数就可以成功返回，不管它们有没有到达目标机器，也不管它们何时被发送到网络，这些都是TCP协议负责的事情。

MSS

>TCP有一个最大分段大小，用于对端TCP通告对端每个分段中能发送的最大TCP数据量。MSS的目的是告诉对端其重组缓冲区大小的实际值，从而避免分片。MSS经常设计成MTU减去IP和TCP首部的固定长度。以太网中使用IPv4MSS值为1460，使用IPv6的MSS值为1440（两者TCP首部都是20字节，但是IPv6首部是40字节，IPv4首部是20字节）


MTU
>许多网络有一个可由硬件规定的MTU。以太网的MTU为1500字节。有一些链路的MTU的MTU可以由认为配置。IPv4要求的最小链路MTU为68字节。这允许最大的IPv4首部（包括20字节的固定长度部分和最多40字节的选项部分）拼接最小的片段（IPv4首部中片段偏移字段以8个字节为单位）IPv6要求的最小链路MTU为1280字节。

[TCP/IP学习（四）TCP缓冲区大小及限制](https://blog.csdn.net/ysu108/article/details/7764461)

[TCP 粘包问题浅析及其解决方案](https://www.v2ex.com/t/478610?p=2)

* TCP包的大小超过缓冲区大小
* 超过MSS长度
* 超过MTU长度


TCP拆包/粘包的现象
发送的包大于缓冲区大小，会拆包
发送的包小于缓冲区大小，会粘包
大于MSS，会拆包
接收缓冲区不及时接收，会粘包

TCP拆包/粘包的现象


### Netty的解决方案

针对TCP拆包/粘包问题，Netty提供了完善的解决方案。

基本框架就是抽象类`ByteToMessageDecoder`



`DelimiterBasedFrameDecoder`
`LineBasedFrameDecoder`
`FixLengthFrameDecoder`
`LengthFieldBasedFrameDecoder`

DelimiterBasedFrameDecoder是基于消息边界方式进行粘包拆包处理的。

FixedLengthFrameDecoder是基于固定长度消息进行粘包拆包处理的。

LengthFieldBasedFrameDecoder是基于消息头指定消息长度进行粘包拆包处理的。

LineBasedFrameDecoder是基于行来进行消息粘包拆包处理的。

[Netty精粹之TCP粘包拆包问题](https://my.oschina.net/andylucc/blog/625315)

* [产生tcp粘包和拆包的原因](https://uule.iteye.com/blog/2429206)

* [Netty 粘包/拆包应用案例及解决方案分析](https://www.cnblogs.com/wenhongyu/archive/2018/08/21/9511887.html)
* [socket缓冲区以及阻塞模式](http://c.biancheng.net/cpp/html/3040.html)
* [MTU & MSS 详解记录](https://blog.51cto.com/infotech/123859)

[TOC]

## Redis 入门

### Redis 常用数据类型

* [Redis内部数据结构详解(1)——dict](https://mp.weixin.qq.com/s?__biz=MzA4NTg1MjM0Mg==&mid=2657261203&idx=1&sn=f7ff61ce42e29b874a8026683875bbb1&scene=21#wechat_redirect)
* [Redis内部数据结构详解(2)——sds](https://mp.weixin.qq.com/s?__biz=MzA4NTg1MjM0Mg==&mid=2657261213&idx=1&sn=0ddddf48929610a4155bd82794cad4fa&scene=21#wechat_redirect)
* [Redis内部数据结构详解(3)——robj](https://mp.weixin.qq.com/s?__biz=MzA4NTg1MjM0Mg==&mid=2657261237&idx=1&sn=380d183332d41d24ea6f88a54f533fc3&scene=21#wechat_redirect)
* [Redis内部数据结构详解(4)——ziplist](https://mp.weixin.qq.com/s?__biz=MzA4NTg1MjM0Mg==&mid=2657261265&idx=1&sn=e105c4b86a5640c5fc8212cd824f750b&scene=21#wechat_redirect)
* [Redis内部数据结构详解(5)——quicklist](https://mp.weixin.qq.com/s?__biz=MzA4NTg1MjM0Mg==&mid=2657261335&idx=1&sn=053d72a348be2e78040f3847f4092d92&scene=21#wechat_redirect)
* [Redis为什么用跳表而不用平衡树？](https://mp.weixin.qq.com/s?__biz=MzA4NTg1MjM0Mg==&mid=2657261425&idx=1&sn=d840079ea35875a8c8e02d9b3e44cf95#rd)

每个数据类型的底层实现

string
* sds: Simple Dynamic String
list
* 普通双向链表
* 压缩链表

set
* dict
* intset

sorted set
* skiplist
* ziplist

hash table
* dict
* ziplist

### Redis 高性能
高性能原理
benchmark数据

## Redis 高可用

### Redis 主从
### Redis 集群
### Redis 持久化

## Redis 集群

* Redis Cluster
* Codis
* twemproxy

## Redis 事务

## Redis Pub/Sub

## Redis 应用

分布式锁
排行榜

## Redis 开发与运维
* [阿里云Redis开发规范](https://yq.aliyun.com/articles/531067)


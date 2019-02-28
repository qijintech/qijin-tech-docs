
## 分析思路

1. 各个线程到达安全点的等待时间；
2. 从 GC Root 扫描对象，进行标记的时间；
3. 存活对象 copy 到 Survivor 以及晋升 Old Gen 到的时间；
4. GC 日志的时间。



## 可能的原因

* IO压力大
* 进程占用了SWAP
* 存活对象多
* 处理FinalReference时间过长

## 参考案例

**IO频繁导致的案例**
    
> 注：**一次JVM GC长暂停的排查过程**有人评论说文章可能没有找到最终原因，读者需要辩证地理解

* [一次JVM GC长暂停的排查过程](https://www.jianshu.com/p/8a4366a7f32d)
* [Eliminating Large JVM GC Pauses Caused by Background IO Traffic](https://engineering.linkedin.com/blog/2016/02/eliminating-large-jvm-gc-pauses-caused-by-background-io-traffic)

**处理FinalReference时间过长**
* [一次 Young GC 的优化实践（FinalReference 相关）](https://mp.weixin.qq.com/s/I3g-d1n7kdaAmmXb-dVNVg)
    > 虽然最终原因是RPC短连造成的，但是分析思路是可以借鉴和学习的

# 为什么使用MSE后客户端突然出现大量TIME\_WAIT堆积？

## Condition

在使用MSE，客户端突然出现大量的TIME\_WAIT堆积，但是使用自建Nacos却没有。

## Cause

客户端通过短连接链接SLB（服务器），而且客户端是连接的主动关闭方，同时并发比较大。

如果使用MSE之前客户端没有TIME\_WAIT堆积，而使用MSE后产生堆积，那么在访问模式不变的情况下，极有可能在使用MSE之前客户端存在TIME\_WAIT socket的快速回收或复用，那么可能是如下几个TCP内核参数问题：

-   `net.ipv4.tcp_tw_recycle = 1`
-   `net.ipv4.tcp_tw_reuse = 1`
-   `net.ipv4.tcp_timestamps = 1`

通过抓包查出由于引入SLB产生，SLB删除了TCP Option中的timestamps字段。

## Remedy

对于没有TCP timestamp信息的客户端，需要将TCP长连接替换短链接。

**说明：** 在解决问题时，对于TIME\_WAIT还需要关注如下几个限制条件：

-   源端口数量\(net.ipv4.ip\_local\_port\_range\)
-   TIME\_WAIT bucket数量（net.ipv4.tcp\_max\_tw\_buckets）
-   文件描述符数量（max open files）

如果TIME\_WAIT数量离源端口数量、TIME\_WAIT bucket数量和文件描述符数量的阈值较远，那么可以忽略该问题。

1.  

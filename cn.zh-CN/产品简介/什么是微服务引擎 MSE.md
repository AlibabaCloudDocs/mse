# 什么是微服务引擎 MSE {#concept_861832 .concept}

微服务引擎（Microservice Engine， 简称 MSE ）是微服务注册中心和配置管理的全托管式平台，提供高可用且免运维的服务注册和配置管理集群，如 ZooKeeper、Nacos 和 Eureka 等。

## 产品功能 {#section_m0u_f6t_je4 .section}

-   完全标准化的引擎使用

    MSE 中托管的引擎（如 ZooKeeper、Eureka 等）完全符合开源软件的标准使用，客户更改引擎接入点地址后，无需修改任务代码，即可使用。

-   数据管理

    提供可视化的数据查询和更新功能，包括数据的增加、删除、修改和查询。

-   监控

    提供可视化的引擎监控功能，包括连接数、TPS 和 QPS 等指标的监控。


## 应用场景 {#section_q6w_hiu_cq5 .section}

-   为 Dubbo 应用构建微服务注册中心 ZooKeeper

    如果正在使用 Dubbo 框架构建微服务系统，那么借助微服务引擎提供的 ZooKeeper 实例，可以实现微服务的注册和订阅。

-   实现分布式协调

    如果正在使用 HBase、Spark 或 Kafka 等开源软件，那么借助微服务引擎提供的 ZooKeeper 实例，可以实现分布式系统的协调。


## 问题反馈 {#section_58a_iaw_zkw .section}

如果您在使用 MSE 过程中有任何疑问，欢迎您扫描下面的二维码加入钉钉群进行反馈。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/697578/156818972350232_zh-CN.png)


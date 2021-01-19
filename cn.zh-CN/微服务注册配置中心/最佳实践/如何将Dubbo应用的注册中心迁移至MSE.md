# 如何将Dubbo应用的注册中心迁移至MSE

如果您的Dubbo应用已经部署在阿里云上并且尚未使用MSE注册中心，需将应用使用的注册中心迁移至MSE，并实现基本的服务注册与发现功能。本文为您介绍如何将Dubbo应用平滑迁移至MSE。

如果您的Dubbo应用已经部署到生产环境并且处于正常运行状态中，此时若想将应用使用的注册中心（例如Zookeeper、Nacos等）迁移到MSE，享受完整的MSE功能，那么在迁移过程中，保证业务的平稳运行不中断是第一要务，而保证应用平台运行不中断迁移到MSE即为平滑迁移。

**说明：** 如果您的应用尚未在生产环境中运行，或者您可以接受停机迁移，可直接使用MSE注册中心。

## 迁移方案

迁移应用有两种方案，切流迁移、双注册和双订阅迁移。这两种方案都可以保证您的应用正常运行且不中断地完成迁移。

**说明：** 本文为您介绍双注册和双订阅迁移方案。

-   切流迁移

    使用Dubbo将原有的服务注册中心切换到MSE，开发一套新的应用，最后通过SLB和域名配置来进行切流。该方案需要重新部署一套已有系统，代价较高。

-   双注册和双订阅迁移

    在应用迁移时同时接入两个注册中心（原有注册中心和EDAS注册中心），保证已迁移的应用和未迁移的应用之间能够相互调用。

    通过双注册和双订阅迁移应用的架构图如下：

    ![双注册和双订阅迁移架构图](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8383976951/p137911.png)

    -   已迁移的应用和未迁移的应用可以互相发现，从而实现互相调用，保证了业务的连续性。
    -   使用方式简单，只需要添加依赖，并修改一行代码，就可以实现双注册和双订阅。
    -   支持查看消费者服务调用列表详情，实时地查看迁移进度。
    -   支持在不重启应用的情况下，动态地变更服务注册的策略和服务订阅的策略，只需要重启一次应用就可以完成迁移。

## 迁移应用

1.  选择需要迁移的Dubbo应用。

    **说明：** 建议从最下层Provider开始迁移。但如果调用链路太复杂，比较难分析，也可以任意选一个应用进行迁移。

2.  在应用程序中添加依赖并修改配置 （双注册、双订阅）。

    为了能将您原来的注册中心迁移到MSE，您需要在您的应用程序中添加相关依赖并修改配置。

    1.  在pom.xml文件中添加`edas-dubbo-migration-bom`依赖。
        -   dubbo 2.6.x及以下版本：

            ```
            <dependency>
                <groupId>com.alibaba.edas</groupId>
                <artifactId>edas-dubbo-migration-bom</artifactId>
                <version>2.6.5.1</version>
                <type>pom</type>
            </dependency>
            ```

        -   dubbo 2.7.x及以上版本：

            ```
            <dependency>
                <groupId>com.alibaba.edas</groupId>
                <artifactId>edas-dubbo-migration-bom</artifactId>
                <version>2.7.0</version>
                <type>pom</type>
            </dependency>
            ```

    2.  在application.properties中添加注册中心的地址。

        本示例展示将本地的Zookeeper注册中心迁移到MSE的Zookeeper中。

        ```
        dubbo.registry.address = edas-migration://30.5.124.15:9999?service-registry=zookeeper://mse-e29fa500-p.zk.mse.aliyuncs.com:2181,zookeeper://localhost:2181&reference-registry=zookeeper://mse-e29fa500-p.zk.mse.aliyuncs.com:2181,zookeeper://localhost:2181
        ```

        **说明：** 如果是非Spring Boot应用，则在dubbo.properties或者对应的Spring配置文件中配置。

        -   `edas-migration://30.5.124.15:9999`是指注册中心的头部，不做更改。启动时，如果日志级别是WARN及以下，可能会出现一个WARN日志，因为Dubbo会对IP和端口做校验，可以忽略。
        -   `service-registry`是指服务注册的注册中心地址，默认会进行多注册。每个注册中心都是标准的Dubbo注册中心格式，用英文逗号（,）分隔。
        -   `reference-registry`是指服务订阅的注册中心地址，支持多注册或新老注册中心。每个注册中心都是标准的Dubbo注册中心格式，多个用英文逗号（,）分隔。
3.  重新部署应用。

4.  其它应用依照步骤[2](#2)和[3](#3)，依次完成应用迁移和部署。


## 结果验证

1.  查看服务注册结果。

    观察MSE中ZooKeeper服务注册结果。

    1.  登录[MSE注册中心控制台](https://mse.console.aliyun.com)。
    2.  在实例列表页面单击实例名称。
    3.  在实例详情页面左侧导航栏选择**数据管理**，查看实例**节点信息**。

        ![ZooKeeper服务注册](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9383976951/p138277.png)

    观察本地ZooKeeper服务注册结果。

    ![本地ZooKeeper服务注册](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9383976951/p138278.png)

2.  查看消费者调用结果。

    两个注册中心的服务提供者均可被调用。

3.  查看业务整体是否正常。


## 清理迁移配置

迁移完成后，删除原有注册中心的配置和迁移过程专用的依赖`edas-dubbo-migration-bom`。修改对应的注册中心地址，即将原有注册中心的配置删除，保证Consumer只从MSE订阅，Provider只在MSE注册。

**说明：** 当应用迁移完成之后，需要从注册中心配置中删除旧的配置中心，最后就变成了如下地址。

```
dubbo.registry.address = zookeeper://mse-e29fa500-p.zk.mse.aliyuncs.com:2181
```

虽然长期使用dubbo-migration依赖对您业务的稳定性没有影响，但增加了复杂性和出错率，推荐您在迁移完毕后清理掉，然后在业务量较小的时间分批重启应用。


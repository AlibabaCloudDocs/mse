---
keyword: [微服务, 服务发现, Nacos, Eureka]
---

# 管理服务（Eureka Nacos）

当您的Eureka和Nacos托管在MSE后，MSE会对注册在其上的服务进行管理。

-   [开通MSE](https://www.aliyun.com/product/mse)
-   [创建MSE实例](/cn.zh-CN/快速入门/微服务组件托管/购买并构建ZooKeeper引擎.md)
-   （可选）[创建命名空间](/cn.zh-CN/用户指南/微服务组件托管/管理命名空间（Nacos）.md)

## 查看服务

1.  登录[MSE管理控制台](https://mse.console.aliyun.com)。

2.  在左侧导航栏选择**注册配置中心** \> **实例列表**。

3.  在实例列表页单击已创建的MSE实例名称。

    ![MSE实例列表](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9991309951/p66590.png)

4.  在实例详情页面的左侧导航树单击**服务管理**，并在**服务管理**页面选择命名空间。

    在该命名空间下，您可以查看该Eureka或者Nacos上所有服务的信息，如服务名、执行该服务的实例列表、服务提供者的数量，同时您还可以单击操作列的**详情**，查看该服务的IP地址、端口和状态信息。

    ![MSE服务管理](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9991309951/p68289.png)



---
keyword: [微服务, 服务发现, ZooKeeper]
---

# 管理数据（ZooKeeper）

在使用引擎过程中，您的应用可以从引擎获取数据或将产生的数据存储到引擎中。

-   [开通MSE](https://www.aliyun.com/product/mse)
-   [创建MSE实例](/cn.zh-CN/快速入门/微服务注册配置中心/购买并构建ZooKeeper引擎.md)

ZooKeeper引擎的数据管理功能为应用提供了配置管理功能，支持应用从ZooKeeper中获取配置数据，支持将提供的服务、IP地址等信息存储到ZooKeeper中，形成统一的配置文件，实现了服务发现的能力。

1.  登录[MSE管理控制台](https://mse.console.aliyun.com)。

2.  在左侧导航栏选择**注册配置中心** \> **实例列表**。

3.  在实例列表页面的操作列单击**管理**。

4.  在**实例详情**页面左侧导航栏中单击**数据管理**。

5.  在数据管理页面右上角单击**新增节点**。

    引擎中默认包含ZooKeeper节点，ZooKeeper节点中默认包含一个子节点quota。

    **说明：** 应用中通过API创建的路径和数据也可以在数据管理页面查看。

6.  在新增节点对话框输入**节点路径**和**节点数据**，单击**确定**即可。

    ![MSE管理节点新增节点](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7991309951/p51225.png)


创建完成后，您可以返回数据管理页面查看节点和数据信息。


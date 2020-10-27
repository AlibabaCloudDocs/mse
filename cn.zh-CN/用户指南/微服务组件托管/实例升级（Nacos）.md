# 实例升级（Nacos）

本文介绍Nacos实例版本从1.1.3升级到1.2.1。

-   [开通MSE](https://www.aliyun.com/product/mse)
-   [创建MSE实例](/cn.zh-CN/快速入门/微服务组件托管/购买并构建ZooKeeper引擎.md)

## 操作步骤

**说明：**

-   实例升级持续时间10分钟左右，期间无法在控制台对该实例进行任何操作。
-   节点数量为3节点及以上的实例，各个节点会进行滚动发布，并自动完成数据同步，保证升级无损；节点数量为1节点和2节点的实例属于非高可用实例，升级无法做到无损。
-   建议在业务低峰期时进行升级，避免升级对业务造成影响。

1.  登录[MSE管理控制台](https://mse.console.aliyun.com)。

2.  在左侧导航栏选择**注册配置中心** \> **实例列表**。

3.  在实例列表页面选择待升级的Nacos实例，单击**操作**列的![升级](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6991309951/p143806.png)，选择**升级**。

4.  在确认升级对话框中单击**确认**。

    ![升级](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6991309951/p143807.png)

    返回实例列表页面，Nacos实例版本成功由1.1.3升级到1.2.1。



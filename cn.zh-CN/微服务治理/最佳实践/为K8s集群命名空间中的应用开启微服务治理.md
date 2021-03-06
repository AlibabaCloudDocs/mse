---
keyword: [开启微服务治理, 命名空间]
---

# 为K8s集群命名空间中的应用开启微服务治理

本文介绍通过MSE控制台为容器服务Kubernetes版（ACK）整个命名空间下的应用开启微服务治理。

-   [创建Kubernetes托管版集群](/cn.zh-CN/Kubernetes集群用户指南/集群/创建集群/创建Kubernetes托管版集群.md)
-   请确保您的MSE治理中心组件**ack-mse-pilot**在2021年05月12日之后安装，如果您之前已经安装过，请先卸载，再重新安装。相关操作，请参见[卸载并重新安装ack-mse-pilot](#section_oss_xwp_7tr)。

## 卸载并重新安装ack-mse-pilot

1.  登录[容器服务控制台](https://cs.console.aliyun.com)。

2.  在左侧导航栏选择**集群**，单击目标集群名称。

3.  在集群详情页面左侧导航栏选择**应用** \> **微服务治理**。

4.  在**微服务治理**页面单击**卸载**，在**卸载**对话框中单击**确认**。

    ![卸载MSE微服务治理组件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9480080261/p272836.png)

    MSE治理中心组件ack-mse-pilot卸载成功。

5.  在**微服务治理**页面单击**安装**，在**安装**对话框中单击**确认**。

    MSE治理中心组件ack-mse-pilot重新安装成功。


## 为命名空间中的应用开启微服务治理

1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **K8s集群列表**。

3.  在**K8s集群列表**页面搜索框列表中选择**集群名称**或**集群ID**，然后输入相应的关键字，单击![搜索图标](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9480080261/p272716.png)图标。

4.  单击目标集群**操作**列的**管理**。

5.  在**集群详情**页面命名空间列表区域，单击目标命名空间**操作**列下的**开启微服务治理**。

    ![开启微服务治理](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9480080261/p272718.png)

6.  在**开启微服务治理**对话框中单击**确认**。

    **说明：** 默认接入的应用名称为deployment的名称，如果您需要修改接入MSE的应用名称，可通过编辑应用的YAML文件进行修改。

    ```
    spec:
      template:
        metadata:
          annotations:
            msePilotCreateAppName:"<yourAppName>"   //替换为您实际使用的应用名称。
    ```

    您的应用在重启之后，就会自动接入到MSE微服务治理中心，可以在**应用列表**页查看到，并进行相应的治理功能。

7.  在**集群详情**页面命名空间列表区域，单击目标命名空间**操作**列下的**关闭微服务治理**。

    **说明：** 如果您想单独为某个应用关闭微服务治理，可以将msePilotAutoEnable这个参数设置为`off`。

    ```
    spec:
      template:
        metadata:
          annotations:
            msePilotAutoEnable:"off"
    ```

    该命名空间下应用的微服务治理功能将关闭。


## 相关操作

若您想创建新的命名空间，可在**集群详情**页面单击**创建命名空间**进行创建。

若您想修改命名空间的标签，可在**集群详情**页面单击目标命名空间**操作**列的**修改标签**进行修改。


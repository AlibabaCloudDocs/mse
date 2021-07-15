---
keyword: [微服务治理, 微服务应用]
---

# 关闭MSE微服务治理

MSE微服务治理商业化后，若您不再继续使用MSE服务治理中心，建议您及时关闭MSE微服务治理，避免MSE停止提供服务治理能力对您的应用造成影响。本文介绍如何关闭MSE微服务治理。

## 关闭流程

关闭MSE微服务治理包含以下步骤：

1.  [为已有应用关闭MSE微服务治理](#section_4yi_udb_o8a)
2.  [在ACK中卸载MSE治理中心组件](#section_nwc_1m2_q94)
3.  [在MSE中删除微服务应用](#section_59y_66b_mpd)

## 为已有应用关闭MSE微服务治理

1.  登录[容器服务控制台](https://cs.console.aliyun.com)。

2.  在左侧导航栏单击**集群**，然后在**集群列表**页面单击目标集群的集群名称。

3.  在集群信息左侧导航栏选择**工作负载** \> **无状态**。

4.  在**无状态**页面左上角选择**命名空间**，并在目标应用的**操作**列中单击**更多**，在列表中单击**查看Yaml**。

    ![无状态-查看 YAML](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1426640261/p99783.png)

5.  在**编辑YAML**对话框的**spec** \> **template** \> **metadata**中找到annotations，删除`msePilotAutoEnable: "on"`或者改为`msePilotAutoEnable: "off"`，然后单击**更新**。

    ```
    annotations:
      msePilotAutoEnable: "off"
      msePilotCreateAppName: "<your-deployment-name>"
    ```


## 在ACK中卸载MSE治理中心组件

1.  在集群信息页面左侧导航栏选择**应用** \> **Helm**。

2.  在**Helm**页面单击**mse-pilot**组件**操作**列下方的**删除**。

    ![删除MSE治理中心组件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6637262261/p279981.png)

3.  在**删除应用**对话框中单击**确定**。


## 在MSE中删除微服务应用

1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **应用列表**。

3.  在**应用列表**页面单击目标应用**操作**列下方的**删除**。

4.  在确认删除对话框中单击**确认**。


完成上述步骤后，您就为部署在容器服务Kubernetes版ACK中的应用关闭了MSE微服务治理能力。


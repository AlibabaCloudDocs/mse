# ACK微服务应用接入MSE治理中心

您可以将部署在容器服务Kubernetes版（ACK）中的Dubbo和Spring Cloud微服务应用接入MSE治理中心，使用MSE提供的一系列服务治理能力，大幅提升线上微服务的稳定性和开发效率。

-   [创建Kubernetes托管版集群](/cn.zh-CN/Kubernetes集群用户指南/集群/创建集群/创建Kubernetes托管版集群.md)
-   [创建命名空间](/cn.zh-CN/Kubernetes集群用户指南/命名空间与配额/创建命名空间.md)

## 接入流程

将ACK中的应用接入MSE治理中心包含以下步骤：

1.  [在ACK中安装MSE治理中心组件](#section_h93_vhn_6ss)。
2.  [为ACK授予MSE治理中心的访问权限](#section_7xx_blp_06o)。
3.  为微服务应用开启MSE微服务治理。
    -   [在创建新应用时开启MSE微服务治理](#section_07c_hhu_i9c)。
    -   [为已有应用开启MSE微服务治理](#section_v96_o5d_zaa)。

## 在ACK中安装MSE治理中心组件

在ACK中为目标集群安装MSE治理中心组件**ack-mse-pilot**，在该集群部署的应用即可接入MSE治理中心。

1.  登录[容器服务控制台](https://cs.console.aliyun.com)。

2.  在左侧导航栏单击**市场** \> **应用目录**。

3.  在**应用目录**页面搜索并单击ack-mse-pilot。

4.  在**ack-mse-pilot**页面右侧**集群**列表中选择集群，然后单击**创建**。

    **说明：** **命名空间**为**msc-pilot**，不可修改。

    ![创建mse组件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3692576161/p255560.png)

    安装MSE微服务治理组件大约需要2分钟，请耐心等待。

    创建成功后，会自动跳转到目标集群的**发布**页面，检查安装结果。如果出现以下页面，展示相关资源，则说明安装成功。

    ![Helm-发布-MSC Pilot](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8730698951/p100153.png)


## 为ACK授予MSE治理中心的访问权限

ACK中的应用要使用MSE治理中心，需要为ACK授予MSE治理中心资源的访问权限。

1.  使用阿里云账号登录[容器服务控制台](https://cs.console.aliyun.com)。

2.  在左侧导航栏单击**集群**。

3.  在**集群列表**页面单击目标集群的集群名称。

4.  在**集群信息**页面上方单击**集群资源**。

5.  在**集群资源**页签单击**Worker RAM角色**右侧的链接。

    ![基本信息-Worker RAM 角色](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8730698951/p99694.png)

6.  在RAM访问控制的**RAM角色管理**页面的**权限管理**页签单击目标权限策略名称链接。

    ![RAM角色管理](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8730698951/p99692.png)

7.  在目标角色的**权限策略管理**的页面的**策略内容**页签下方单击**修改策略内容**，并在右侧的**修改策略内容**面板中将以下内容添加到策略内容中，单击**确定**。

    ![修改策略内容](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5883394161/p99695.png)

    ```
    {
      "Action":"mse:CreateApplication",
      "Resource":"*",
      "Effect":"Allow"
    }
    ```


## 在创建新应用时开启MSE微服务治理

1.  登录[容器服务控制台](https://cs.console.aliyun.com)。

2.  在左侧导航栏单击**集群**，然后在**集群列表**页面单击目标集群的集群名称。

3.  在集群左侧导航栏选择**工作负载** \> **无状态**，然后在**无状态**页面左上角选择**命名空间**，在右上角单击**使用模板创建**。

    ![工作负载](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3692576161/p100159.png)

4.  在**使用模板创建**页面上选择**示例模板**，并在**模板**中将以下`annotations`添加到**spec** \> **template** \> **metadata**层级下，然后单击**创建**。

    ```
    annotations:
      msePilotAutoEnable: "on"
      msePilotCreateAppName: "<your-deployment-name>"
    ```

    **说明：** 需要将`<your-deployment-name>`替换为您实际使用的应用名称。

    创建一个无状态（Deployment）应用并开启MSE微服务治理的完整YAML示例模板如下：

    ```
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      labels:
        app: productserivce
      name: productserivce
      namespace: default
    spec:
      replicas: 1
      selector:
        matchLabels:
          app: productserivce
      template:
        metadata:
          annotations:
            msePilotAutoEnable: 'on'
            msePilotCreateAppName: productserivce
          labels:
            app: productserivce
        spec:
          containers:
            - image: >-
                registry.cn-hangzhou.aliyuncs.com/alibabacloud-microservice-demo/productservice
              imagePullPolicy: Always
              name: productserivce
              resources:
                requests:
                  cpu: 250m
                  memory: 512Mi
    ```


## 为已有应用开启MSE微服务治理

如果已经在容器服务Kubernetes版中部署了应用（包括有状态和无状态），则可以为有状态或无状态应用开启MSE微服务治理。有状态和无状态应用的开启步骤一致，本文仅以无状态应用为例介绍如何开启MSE微服务治理。

1.  登录[容器服务控制台](https://cs.console.aliyun.com)。

2.  在左侧导航栏单击**集群**，然后在**集群列表**页面单击目标集群。

3.  在集群左侧导航栏选择**工作负载** \> **无状态**，然后在**无状态**页面左上角选择**命名空间**，并在目标应用的**操作**列中单击**更多**，在列表中单击**查看Yaml**。

    ![无状态-查看 YAML](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3692576161/p99783.png)

4.  在**编辑YAML**对话框中将以下annotations添加到**spec** \> **template** \> **metadata** ，并单击**更新**。

    ```
    annotations:
      msePilotAutoEnable: "on"
      msePilotCreateAppName: "<your-deployment-name>"
    ```

    **说明：** 需要将`<your-deployment-name>`替换为您实际使用的应用名称。


完成上述步骤后，您就为部署在容器服务Kubernetes版中的应用开启了MSE微服务治理。登录[MSE治理中心控制台](https://mse.console.aliyun.com/#/msc/home)，即可使用MSE微服务治理对您的Spring Cloud和Dubbo应用进行服务治理，相关内容，请参见[使用指引](/cn.zh-CN/.md)。


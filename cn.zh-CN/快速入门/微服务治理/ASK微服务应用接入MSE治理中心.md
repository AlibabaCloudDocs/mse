# ASK微服务应用接入MSE治理中心

您可以将部署在阿里云Serverless Kubernetes（ASK）集群中的Spring Cloud和Dubbo应用接入MSE微服务治理中心，即可对应用进行治理，包括无损下线、离群实例摘除、服务查询、服务鉴权、服务测试和金丝雀发布，大幅提升线上微服务的稳定性和开发效率。

[创建Serverless Kubernetes集群](/cn.zh-CN/Serverless Kubernetes集群用户指南/快速入门/创建Serverless Kubernetes集群.md)

## 接入流程

将ASK集群中的应用接入MSE治理中心包含以下步骤：

1.  [在ASK集群中安装MSE微服务治理组件](#section_xs3_221_dpd)
2.  [为ASK集群授予MSE治理中心的访问权限](#section_xfd_bxc_674)
3.  为微服务应用开启MSE微服务治理。
    -   [在创建新应用时开启MSE微服务治理](#section_asc_whv_zpu)
    -   [为已有应用开启MSE微服务治理](#section_9ms_mf0_gjy)

## 在ASK集群中安装MSE微服务治理组件

在目标ASK集群中安装MSE治理中心组件**ack-mse-pilot**，在该集群部署的应用即可接入MSE治理中心。

1.  登录[容器服务控制台](https://cs.console.aliyun.com)。

2.  在左侧导航栏选择**市场** \> **应用目录**。

3.  在**应用目录**页面搜索并单击ack-mse-pilot。

4.  在**ack-mse-pilot**页面右侧集群列表中选择集群，然后单击**创建**。

    ![ask集群安装mse组件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6181915161/p246416.png)

    组件创建成功后，会自动跳转至目标集群的发布页面，显示当前组件版本信息。


## 为ASK集群授予MSE治理中心的访问权限

ASK集群中的应用要使用MSE治理中心，需要为ASK集群授予MSE治理中心资源的访问权限。

1.  使用阿里云账号登录[RAM访问控制控制台](https://ram.console.aliyun.com/overview)。

2.  在左侧导航栏选择**权限管理** \> **权限策略管理**，然后单击**创建权限策略**。

3.  在**新建自定义权限策略**页面填写**策略名称**，配置模式选择**脚本配置**，在**策略内容**中配置如下示例代码，然后单击**确定**。

    ![新建自定义权限策略](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6181915161/p246446.png)

    ```
    {
      "Statement": [{
        "Action":"mse:CreateApplication",
        "Resource": "*",
        "Effect": "Allow"
      }],
      "Version": "1"
    }
    ```

4.  在左侧导航栏单击**RAM角色管理**，在**RAM角色管理**页面单击**创建RAM角色**。

5.  在**创建RAM角色**面板进行如下配置。

    1.  在**选择类型**步骤中，选择**阿里云服务**，单击**下一步**。

    2.  **配置角色**步骤中，角色类型选择**普通服务角色**，填写**角色名称**，选择受信服务为**云服务器**，然后单击**完成**。

    3.  在**创建完成**步骤中，单击**为角色授权**。

    4.  在**添加权限**面板中，选择刚刚创建的自定义策略，然后单击**确定**。

6.  登录[容器服务控制台](https://cs.console.aliyun.com)。

7.  在左侧导航栏单击**集群**，在**集群列表**页面单击目标集群名称。

8.  在目标**集群信息**页面左侧导航栏选择**工作负载** \> **无状态**，命名空间选择**mse-pilot**，单击**mse-pilot-ack-mse-pilot pod**。

9.  在Pod详情页面，单击**查看Yaml**，在**编辑YAML**对话框中添加`k8s.aliyun.com/eci-ram-role-name: <刚刚创建的角色名>`到**spec** \> **template** \> **annotations**，并单击**更新**。

    ![更新YAML](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7181915161/p246484.png)


## 在创建新应用时开启MSE微服务治理

1.  登录[容器服务控制台](https://cs.console.aliyun.com)。

2.  在左侧导航栏单击**集群**，然后在**集群列表**页面单击目标集群的集群名称。

3.  在集群信息左侧导航栏选择**工作负载** \> **无状态**，然后在**无状态**页面左上角选择**命名空间**，在右上角单击**使用YAML创建资源**。

    ![工作负载](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1426640261/p100159.png)

4.  在**创建**页面上选择**示例模板**，并在**模板**中将以下`annotations` 添加到 **spec** \> **template** \> **metadata**层级下，然后单击**创建**。

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

2.  在左侧导航栏单击**集群**，然后在**集群列表**页面单击目标集群的集群名称。

3.  在集群信息左侧导航栏选择**工作负载** \> **无状态**，然后在**无状态**页面左上角选择**命名空间**，并在目标应用的**操作**列中单击**更多**，在列表中单击**查看Yaml**。

    ![无状态-查看 YAML](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1426640261/p99783.png)

4.  在**编辑YAML**对话框中将以下annotations添加到**spec** \> **template** \> **metadata** ，并单击**更新**。

    ```
    annotations:
      msePilotAutoEnable: "on"
      msePilotCreateAppName: "<your-deployment-name>"
    ```

    **说明：** 需要将`<your-deployment-name>`替换为您实际使用的应用名称。


完成上述步骤后，您就为部署在容器服务Kubernetes版中的应用开启了MSE微服务治理。登录[MSE治理中心控制台](https://mse.console.aliyun.com/#/msc/home)，即可使用MSE微服务治理对您的Spring Cloud和Dubbo应用进行服务治理，相关内容，请参见[使用指引](/cn.zh-CN/.md)。


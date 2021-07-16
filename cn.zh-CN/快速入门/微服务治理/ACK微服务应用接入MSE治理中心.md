# ACK微服务应用接入MSE治理中心

您可以将部署在容器服务Kubernetes版（ACK）中的Spring Cloud和Dubbo等微服务应用接入MSE治理中心，使用MSE提供的一系列服务治理能力，大幅提升线上微服务的稳定性和开发效率。

-   [创建Kubernetes托管版集群](/cn.zh-CN/Kubernetes集群用户指南/集群/创建集群/创建Kubernetes托管版集群.md)
-   [创建命名空间](/cn.zh-CN/Kubernetes集群用户指南/命名空间与配额/管理命名空间.md)

## 接入流程

将ACK中的应用接入MSE治理中心包含以下步骤：

1.  [在ACK中安装MSE治理中心组件](#section_h93_vhn_6ss)
2.  [为ACK授予MSE治理中心的访问权限](#section_7xx_blp_06o)
3.  [为ACK命名空间中的应用开启MSE微服务治理](#section_75l_shd_pvf)

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


## 为ACK命名空间中的应用开启MSE微服务治理

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


完成上述步骤后，您就为部署在容器服务Kubernetes版中的应用开启了MSE微服务治理。登录[MSE治理中心控制台](https://mse.console.aliyun.com/#/msc/home)，即可使用MSE微服务治理对您的Spring Cloud和Dubbo应用进行服务治理，相关内容，请参见[使用指引](/cn.zh-CN/.md)。


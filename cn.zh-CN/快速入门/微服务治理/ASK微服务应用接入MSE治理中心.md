# ASK微服务应用接入MSE治理中心

您可以将部署在阿里云Serverless Kubernetes（ASK）集群中的Spring Cloud和Dubbo应用接入MSE微服务治理中心，即可对应用进行治理，包括无损下线、离群实例摘除、服务查询、服务鉴权、服务测试和金丝雀发布，大幅提升线上微服务的稳定性和开发效率。

[创建Serverless Kubernetes集群](/cn.zh-CN/Serverless Kubernetes集群用户指南/快速入门/创建Serverless Kubernetes集群.md)

## 接入流程

将ASK集群中的应用接入MSE治理中心包含以下步骤：

1.  [在ASK集群中安装MSE微服务治理组件](#section_xs3_221_dpd)
2.  [为ASK集群授予MSE治理中心的访问权限](#section_xfd_bxc_674)
3.  [为ASK集群命名空间中的应用开启MSE微服务治理](#section_sz2_1gu_swv)

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

    ![更新YAML](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3717231261/p246484.png)


## 为ASK集群命名空间中的应用开启MSE微服务治理

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


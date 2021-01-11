---
keyword: [微服务, 服务发现]
---

# RAM授权访问注册配置中心

MSE支持阿里云账号给RAM用户授予MSE的操作权限，避免因暴露阿里云账号密钥造成的安全风险。本文介绍如何创建RAM用户并给RAM用户授权，授权后您就可以通过RAM用户使用MSE。

## 使用场景

某企业开通了微服务引擎MSE服务，由于员工工作职责不同，对资源操作所需权限也不同，现有如下需求：

-   鉴于安全或信任原因，不希望将云账号密钥直接透露给员工，期望可以为员工相应的账号授予权限。
-   用户账号只能在授权的前提下操作资源，不需要进行独立的计量计费，所有开销均计入企业账号名下。
-   随时可以撤销用户账号的权限，也可以随时删除其创建的用户账号。

## 使用说明

阿里云账号和RAM用户授权可以作用于控制台和OpenAPI操作。

## 步骤一：

使用阿里云账号登录RAM控制台并创建RAM用户。

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏选择**人员管理** \> **用户**。

3.  在**用户**页面单击**创建用户**。

4.  输入**登录名称**和**显示名称**。

5.  在**访问方式**区域选中**控制台访问**或**编程访问**。

    -   **控制台访问**：完成对登录安全的基本设置，包括自动生成或自定义登录密码、是否要求下次登录时重置密码以及是否要求开启多因素认证。

        **说明：** 自定义登录密码时，密码必须满足您在**人员管理** \> **设置**中设置的密码复杂度规则。关于如何设置密码复杂度规则，请参见[设置RAM用户密码强度](/cn.zh-CN/安全设置/密码/设置RAM用户密码强度.md)。

    -   **编程访问**：自动为RAM用户生成访问密钥（AccessKey），支持通过API或其他开发工具访问阿里云。
    **说明：** 为了保障账号安全，建议仅为RAM用户选择一种登录方式，避免RAM用户离开组织后仍可以通过访问密钥访问阿里云资源。

6.  单击**确定**。


## 步骤二：为RAM用户添加权限

在使用RAM用户之前，需要为其添加相应权限。

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏选择**人员管理** \> **用户**。

3.  在**用户**页面，找到需要授权的用户，单击**操作**列中的**添加权限**。

4.  在**添加权限**页面的**选择权限**区域，选择权限策略类型，在文本框中输入要添加的权限策略，单击搜索到的权限策略，然后单击**确定**。

    -   系统权限策略

        微服务引擎MSE目前支持两种粗粒度的系统权限策略。

        |权限策略名称|说明|
        |------|--|
        |AliyunMSEFullAccess|管理微服务引擎MSE的权限，等同于阿里云账号的权限，被授予该权限的RAM用户拥有控制台所有功能的操作权限。|
        |AliyunMSEReadOnlyAccess|微服务引擎MSE的只读权限，被授予该权限的RAM用户具有阿里云账号所有资源的只读权限。|

        **说明：** 建议给运维人员授予AliyunMSEFullAccess权限策略，由运维人员去创建和删除资源。给开发人员授予AliyunMSEReadOnlyAccess权限策略，可以查看这些资源，但是不能删除和创建。如果想更细粒度地控制开发人员的权限，您可使用以下自定义权限策略。

    -   自定义权限策略

        如果您需要更细粒度地授权，您可以通过创建自定义策略来进行访问控制。创建自定义策略的具体步骤，请参见[创建自定义策略](https://help.aliyun.com/document_detail/93733.html#task-glf-vwf-xdb)

        为了方便您自定义RAM权限策略，本文提供了微服务引擎MSE版的授权映射表。

        |Action名称|权限说明|是否为只读类权限|
        |--------|----|--------|
        |CreateCluster|创建集群|否|
        |DeleteCluster|删除集群|否|
        |ListClusters|查看集群列表|是|
        |QueryClusterDetail|更新集群详情|是|
        |RestartCluster|重启集群|否|
        |RetryCluster|重试集群|否|
        |UpdateCluster|更新集群|否|
        |CreateNacosConfig|创建Nacos配置|否|
        |DeleteNacosConfig|删除Nacos配置|否|
        |DeleteNacosConfigs|批量删除Nacos配置|否|
        |GetNacosConfig|查看Nacos配置|是|
        |GetNacosHistoryConfig|查看Nacos配置历史|是|
        |ListNacosConfigs|查看Nacos配置列表|是|
        |ListNacosHistoryConfigs|查看Nacos配置历史列表|是|
        |UpdateNacosConfig|更新Nacos配置|否|

    示例一：授予RAM用户对实例mse-cn-0pp1j8om80a的读写权限

    ```
    {
        "Version": "1",
        "Statement": [
                 {
                     "Action": [
                       "mse:*"
                                ],
                     "Resource": "acs:mse:*:*:instance/mse-cn-0pp1j8om80a",
                     "Effect": "Allow"
                 }
             ]
    }
    ```

    示例二：授予RAM用户对所有实例的读权限

    ```
     {
        "Version": "1",
         "Statement": [
                 {
                     "Action": [
                       "mse:List*",
                       "mse:Query*",
                       "mse:Get*"
                                ],
                     "Resource": "acs:mse:*:*:*",
                     "Effect": "Allow"
                 }
             ]
      }
    ```

5.  在**添加权限**的授权结果页面上，查看授权信息摘要，并单击**完成**。


## 后续操作

使用阿里云账号创建好RAM用户后，即可将RAM用户的登录名称及密码或者AccessKey信息分发给其他用户。其他用户可以按照以下步骤使用RAM用户登录控制台或调用API。

-   登录控制台
    1.  打开[RAM用户登录](https://signin.aliyun.com/login.htm)页面。
    2.  在**RAM用户登录**页面，输入RAM用户登录名称，单击**下一步**，并输入RAM用户密码，然后单击**登录**。

        **说明：** RAM用户登录名称的格式为`<$username>@<$AccountAlias>`或`<$username>@<$AccountAlias>.onaliyun.com`。**<$AccountAlias\>**为账号别名，如果没有设置账号别名，则默认值为阿里云账号的ID。

    3.  在**子用户用户中心**页面上单击有权限的产品，即可访问控制台。
-   调用API

    使用RAM用户的AccessKey调用API。在代码中使用RAM用户的AccessKey ID和AccessKey Secret即可。



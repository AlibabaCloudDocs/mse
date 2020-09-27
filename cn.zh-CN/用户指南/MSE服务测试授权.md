# MSE服务测试授权

服务测试功能需要创建一个服务消费者，调用您VPC中的服务提供者，从而测试服务提供者，所以需要有创建服务消费者实例的权限、访问指定VPC的权限和调用指定命名空间中指定应用的权限。本文介绍如何在RAM控制台对云账户或RAM子账号授予这些操作的权限。

服务测试的权限包括公共权限和子账号权限两部分。

-   公共权限：EDAS使用函数计算FC（Function Compute）服务账号的权限，该权限用于创建服务消费者实例。
-   子账号权限：子账号测试指定命名空间内指定服务的权限。

## 公共权限

为了服务测试功能，需要新增如下权限给**主账号**和**子账号**。所以示例中，将这些公共权限都添加给了AliyunMSEDefaultRole。

## 为MSE授予使用FC服务账号的权限

1.  登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏单击**RAM角色管理**。

3.  在**RAM角色管理**页面**创建RAM角色**右侧的本文框中输入AliyunMSEDefaultRole，然后在**RAM角色名称**列表中单击**AliyunMSEDefaultRole**。

4.  在**AliyunMSEDefaultRole**页面单击**信任策略管理**页签。

5.  单击**修改信任策略**，然后在**修改信任策略**面板中Service下增加`1405049854278833@fc.aliyuncs.com`配置，单击**确定**。

    ![修改信任策略](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/3368101061/p170278.png)

    修改后的信任策略如下：

    ```
    {
        "Statement": [
            {
                "Action": "sts:AssumeRole",
                "Effect": "Allow",
                "Principal": {
                    "Service": [
                        "mse.aliyuncs.com",
                        "1405049854278833@fc.aliyuncs.com" 
                    ]
                }
            }
        ],
        "Version": "1"
    }
    ```

    **说明：** `1405049854278833@fc.aliyuncs.com`是MSE调用FC（函数计算）的服务账号，由于需要连接到您的网络来实现服务测试功能，所以需要您添加这一步授权。

    修改完成后，返回**信任策略管理**页签，信任策略中即包含了FC服务账号配置。


## 创建测试服务的自定义权限策略并为子账号授权

子账号要测试服务，需要mse:TestService权限。

1.  登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏选择**权限管理** \> **权限策略管理** 。

3.  在**权限策略管理**页面单击**创建权限策略**。

4.  在**新建自定义权限策略**页面配置相关参数，然后单击**确定**。

    ![新建自定义权限策略](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/3368101061/p170288.png)

    |参数|描述|
    |--|--|
    |**策略名称**|输入策略名称。|
    |**备注**|输入策略备注信息。|
    |**配置模式**|选择**脚本配置**。|
    |**策略内容**|输入测试服务的自定义权限策略。|

    测试服务的自定义权限策略内容如下：

    ```
    {
        "Statement": [
            {
                "Action": [
                    "mse:TestService"
                ],
                "Effect": "Allow",
                "Resource": [
                    "acs:mse:$regionid:*:application/$applicationId"  
                ]
            }
        ],
        "Version": "1"
    }
    ```

    **说明：** $regionid和$applicationId请替换为实际的地域和应用。如果要测试所有地域和应用的服务，将$regionid和$applicationId替换为星号（\*）即可。（\*）表示用户ID，若不涉及跨账号授权，一般默认即可。

5.  为子账号授权创建的测试服务的自定义权限，详情请参见[为RAM用户授权](https://help.aliyun.com/document_detail/121945.html?spm=a2c4g.11186623.2.20.4e657876lnNB00#task-187800)。



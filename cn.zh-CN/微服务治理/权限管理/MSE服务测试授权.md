# MSE服务测试授权

服务测试功能需要创建一个服务消费者，调用您VPC中的服务提供者，从而测试服务提供者。本文介绍如何在RAM控制台对RAM用户授予这些操作的权限。

## 创建测试服务的自定义权限策略并为RAM用户授权

RAM用户要测试服务，需要mse:TestService权限。

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏选择**权限管理** \> **权限策略管理** 。

3.  在**权限策略管理**页面单击**创建权限策略**。

4.  在**新建自定义权限策略**页面配置相关参数，然后单击**确定**。

    ![新建自定义权限策略](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5295530161/p170288.png)

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

5.  为RAM用户授权创建的测试服务的自定义权限，请参见[为RAM用户授权](https://help.aliyun.com/document_detail/121945.html?spm=a2c4g.11186623.2.20.4e657876lnNB00#task-187800)。



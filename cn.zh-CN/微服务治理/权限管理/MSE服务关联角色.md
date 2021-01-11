---
keyword: [RAM角色, 服务关联角色]
---

# MSE服务关联角色

本文介绍MSE服务关联角色AliyunServiceRoleForMSE以及如何删除该角色。

MSE服务关联角色AliyunServiceRoleForMSE是MSE在某些情况下，为了完成自身的某个功能，需要获取其他云服务的访问权限而提供的RAM角色。更多关于服务关联角色的信息，请参见[服务关联角色](/cn.zh-CN/角色管理/服务关联角色.md)。

## AliyunServiceRoleForMSE应用场景

MSE需要访问[云服务器ECS](/cn.zh-CN/产品简介/什么是云服务器ECS.md)和[专有网络VPC](/cn.zh-CN/产品简介/什么是专有网络.md)云服务的资源时，可通过自动创建的MSE服务关联角色AliyunServiceRoleForMSE获取访问权限。

## AliyunServiceRoleForMSE权限说明

AliyunServiceRoleForMSE具备以下云服务的访问权限：



## 删除AliyunServiceRoleForMSE

如果您使用了MSE功能，然后需要删除MSE服务关联角色AliyunServiceRoleForMSE，例如出于安全考虑，需要删除该角色，则需要先明确删除后的影响：删除AliyunServiceRoleForMSE后，无法使用服务测试、服务压测功能。

删除AliyunServiceRoleForMSE的操作步骤如下：

1.  使用阿里云账号登录[RAM控制台](http://ram.console.aliyun.com)，在左侧导航栏中单击**RAM角色管理**。

2.  在RAM角色管理页面**创建RAM角色**右侧的搜索框中，输入**AliyunServiceRoleForMSE**，自动搜索到MSE的服务关联角色AliyunServiceRoleForMSE。

3.  在AliyunServiceRoleForMSE的**操作**列单击**删除**。

4.  在删除RAM角色对话框，单击**确定**。


## 常见问题

为什么我的RAM用户无法自动创建MSE服务关联角色AliyunServiceRoleForMSE？

您需要拥有指定的权限，才能自动创建或删除AliyunServiceRoleForMSE。因此，在RAM用户无法自动创建AliyunServiceRoleForMSE时，您需为其添加以下权限策略。

```
{
    "Statement": [
        {
            "Action": [
                "ram:CreateServiceLinkedRole"
            ],
            "Resource": "acs:ram:*:主账号ID:role/*",
            "Effect": "Allow",
            "Condition": {
                "StringEquals": {
                    "ram:ServiceName": [
                        "mse.aliyuncs.com"
                    ]
                }
            }
        }
    ],
    "Version": "1"
}
```

**说明：** 请将`主账号ID`替换为您实际的阿里云账号ID。

**相关文档**  


[服务关联角色](/cn.zh-CN/角色管理/服务关联角色.md)


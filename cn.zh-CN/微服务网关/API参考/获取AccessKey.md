# 获取AccessKey

您可以为阿里云账号和RAM用户创建一个访问密钥（AccessKey）。在调用阿里云API时您需要使用AccessKey完成身份验证。

AccessKey包括AccessKey ID和AccessKey Secret。

-   AccessKey ID：用于标识用户。
-   AccessKey Secret：用于验证用户的密钥。AccessKey Secret必须保密。

**警告：** 阿里云账号AccessKey泄露会威胁您所有资源的安全。建议使用RAM用户AccessKey进行操作，可以有效降低AccessKey泄露的风险。

1.  使用阿里云账号登录[阿里云管理控制台](https://home.console.aliyun.com/new?spm=a2c4g.11186623.2.13.b22b5f81PaDcNA#/)。

2.  将鼠标置于页面右上方的账号图标，单击**AccessKey 管理**。

3.  在**安全提示**页面，选择获取阿里云账号或者RAM用户的Accesskey。

    ![安全提示](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3458295951/p134371.png)

4.  获取账号AccessKey。

    -   获取阿里云账号AccessKey
        1.  在**安全提示**页面单击**继续使用AccessKey**。
        2.  在安全信息管理页面，单击**创建AccessKey**。
        3.  在手机验证页面，获取并填入**校验码**，单击**确定**。
        4.  在新建用户AccessKey页面，展开**AccessKey详情**，查看**AccessKey ID**和**AccessKey Secret**。可以单击**保存AK信息**，下载AccessKey信息。

            ![新建用户AccessKey](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3458295951/p134373.png)

    -   获取RAM用户AccessKey
        1.  在**安全提示**页面单击**开始使用子用户AccessKey**
            -   如果是未创建RAM用户，请在系统跳转的[RAM访问控制台](https://ram.console.aliyun.com/users/new)的创建用户页面，创建RAM用户，创建完成后会自动为RAM用户生成访问密钥（AccessKey）。详情请参见[创建RAM用户](https://help.aliyun.com/document_detail/93720.html)。
            -   如果是已创建RAM用户，继续执行后续步骤直接获取RAM用户的AccessKey。
        2.  登录[RAM访问控制台](https://ram.console.aliyun.com/users/new)，在左侧导航栏选择**人员管理** \> **用户**。
        3.  在**用户**页面搜索需要获取AccessKey的用户。
        4.  单击目标用户登录名称，在用户详情页认证管理页签下的用户 AccessKey区域，单击**创建 AccessKey**。
        5.  在创建 AccessKey页面，查看**AccessKey ID**和**AccessKey Secret**。

            您还可以单击**下载CSV文件**或者**复制**，完成对AccessKey信息的保存。

            ![创建 AccessKey](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3458295951/p134443.png)



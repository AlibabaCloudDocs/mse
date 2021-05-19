# 发布API

您需要发布API，以便其它服务访问网关中添加的服务。

已经为API添加路由和负载均衡策略，否则API将发布失败。具体操作，请参见[为API添加策略](/cn.zh-CN/微服务网关/Zuul用户指南/API管理/为API添加策略.md)。

## 操作步骤

1.  登录[微服务网关控制台](https://microgw.console.aliyun.com)。

2.  在顶部菜单栏选择地域。

3.  在左侧导航栏选择**网关管理**。

4.  在**网关详情**页面左侧导航栏单击**API管理**。

5.  在**API管理**页面单击API名称。

6.  在**API详情**页面左下角单击**保存并发布**。

    保存并发布该API后，会触发API发布流程，在**发布详情**对话框中可以查看API发布的进度和状态。

    ![发布详情](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7009957061/p190850.png)

    返回**API管理**页面，该API的**运行状态**为**已发布**。


## 结果验证

1.  在浏览器地址栏输入http://微服务网关绑定的EIP:80/demo/user/rest，按**enter**键，界面返回**Hello from \[8080\]!**。

    ![demo返回示例值](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8291446951/p128536.png)

    -   微服务绑定的EIP，即是网关入口SLB绑定的EIP。关于绑定EIP的详细操作，请参见[绑定EIP](https://help.aliyun.com/document_detail/86105.html?spm=a2c4g.11186623.6.573.59d96efcKeUHwT)。
    -   访问路径中的“/demo”只是示例，实际情况取决于您在路由策略中设置的path属性值。
    **说明：** 如果您需要访问设置了鉴权策略的服务，请参见[鉴权结果验证]()。



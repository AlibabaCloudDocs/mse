# 从EDAS关联服务

目前微服务网关支持从注册中心添加服务和从EDAS关联服务两种场景，本文介绍从EDAS关联服务的配置流程。

已经部署微服务（[微服务应用Demo](https://aliware-images.oss-cn-hangzhou.aliyuncs.com/csb/sc-microservice-example.zip)）到EDAS，请参见[部署应用到EDAS]()。

微服务部署到EDAS后，可采用从EDAS关联服务方案，免去在微服务网关侧添加注册中心和服务的步骤，提升服务发布效率。

如果您的微服务是部署到阿里云其他产品上，只能选用从注册中心添加服务的方案。

Kong网关不支持从EDAS关联服务。

## 绑定EDAS命名空间

1.  登录[微服务网关控制台](https://microgw.console.aliyun.com)。

2.  在顶部菜单栏选择地域。

3.  在左侧导航栏选择**网关管理**。

4.  在**网关管理**页面单击网关名称。

5.  在**网关详情**页面左侧导航栏单击**网关详情**。

6.  在**网关详情**页面**基本信息**区域，单击**绑定EDAS**。

    **说明：** Kong网关不支持从EDAS关联服务。

7.  在**绑定EDAS**对话框，选择目标EDAS命名空间，单击**确认**。

    ![绑定EDAS](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7197918061/p201266.png)

    绑定EDAS命名空间后，在**基本信息**区域显示**EDAS命名空间**的信息。

    ![基本信息-EDAS命名空间](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7197918061/p201267.png)


## 新建API

1.  在**网关管理**页面单击网关名称。

2.  在**网关详情**页面左侧导航栏单击**API管理**。

3.  在**API管理**页面左上角单击**新建API**。

4.  在**新建API**对话框设置API参数，然后单击**确认**。

    ![新建API](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0448670061/p169234.png)

    |参数|说明|
    |--|--|
    |**API名称**|仅限字母、数字和下划线（\_），最多64个字符，必须以字母开头。|
    |**API访问路径**|该API的访问路径，例如/order/query。|
    |**API中文名称**|API的中文名称，最多16个字符。|
    |**API描述**|API的描述信息。|
    |**关联的服务**|当您需要从EDAS关联服务时，此处无需设置。|


## 为API添加策略

1.  在**API管理**页面单击API名称。

2.  在**API详情**页面的**策略**区域确定目标链路，不同链路的策略作用范围不同。

    -   **请求处理**：网关接收到API请求后，最先执行的处理环节。
    -   **响应处理**：网关在生成API请求后，最后执行的处理环节。
    -   **后端请求处理**：网关在发起后端微服务的请求前，最后执行的处理环节。
    -   **后端响应处理**：网关在接收后端微服务的响应后，最先执行的处理环节。
    **说明：** 一般只需配置**请求处理**和**响应处理**两个环节，若涉及需特别强调时机差异处理时可配置后端处理。

3.  在目标链路内添加策略，您可以选择以下任一方式添加策略：

    添加策略包含**创建策略**和**选择已有策略**两种方式。

    **说明：**

    -   当您是从EDAS关联服务时，必须为API添加路由策略，否则API无法发布。
    -   当您是从EDAS关联服务时，为API添加策略时必须使用真实的serviceId。serviceId请从[EDAS控制台](https://edas.console.aliyun.com)的**微服务治理** \> **Spring Cloud** \> **服务查询**页面的目标命名空间下获取，该命名空间页面下的**服务名**即是serviceId。
    -   如果需要添加鉴权策略，则需要先创建凭证。具体操作，请参见[新建凭证]()。
    -   创建新策略
        1.  在目标链路区域单击**创建策略**。
        2.  在**创建策略**对话框选择策略类型，并设置策略信息，然后单击**确认**。

            ![创建新策略](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5677464061/p179923.png)

            |参数|说明|
            |--|--|
            |**策略名称**|仅限字母、数字和下划线（\_），最长255个字符，必须以字母开头。|
            |**策略别名**|易于辨识策略的别名信息。|
            |**策略类型**|根据需要选择策略，本示例选择**路由-ZUUL**。|
            |**启用状态**|策略的启用状态，默认开启。|
            |**策略配置**|根据需要配置策略，也可以在模板基础上配置其它参数。|

    -   选择已有策略
        1.  在目标链路区域单击**选择已有策略**。
        2.  在**已有策略**对话框选中目标策略，单击**确认**。

            ![选择已有策略](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5677464061/p179927.png)

        3.  在目标链路内单击策略名称，在**编辑策略**对话框中开启策略启用开关，然后单击**确认**。

            ![开启策略启用开关](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5677464061/p179932.png)

            **说明：** 选择已有策略，默认不启用该策略，未启用的策略携带![未启用标识](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4003564061/p179979.png)标识。如果需要启用，请开启**启用状态**开关。

4.  同一个链路中如果存在多条策略，鼠标悬停在策略名称上并移动出现的![移动按钮 ](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1898464061/p84983.png)图标，调整策略的优先级。


## 发布API

1.  在**网关详情**页面左侧导航栏单击**API管理**。

2.  在**API管理**页面单击API名称。

3.  在**API详情**页面左下角单击**保存并发布**。

    保存并发布该API后，会触发API发布流程，在**发布详情**对话框中可以查看API发布的进度和状态。

    ![发布详情](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7009957061/p190850.png)

    返回**API管理**页面，该API的**运行状态**为**已发布**。


## 结果验证

1.  在浏览器地址栏输入http://微服务网关绑定的EIP:80/demo/user/rest，按**enter**键，界面返回**Hello from \[8080\]!**。

    ![demo返回示例值](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8291446951/p128536.png)

    -   微服务绑定的EIP，即是网关入口SLB绑定的EIP。关于绑定EIP的详细操作，请参见[绑定EIP](https://help.aliyun.com/document_detail/86105.html?spm=a2c4g.11186623.6.573.59d96efcKeUHwT)。
    -   访问路径中的“/demo”只是示例，实际情况取决于您在路由策略中设置的path属性值。
    **说明：** 如果您需要访问设置了鉴权策略的服务，请参见[鉴权结果验证]()。



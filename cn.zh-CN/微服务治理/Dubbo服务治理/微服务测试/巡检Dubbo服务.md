---
keyword: [微服务, 服务治理, 服务巡检]
---

# 巡检Dubbo服务

目前，随着云原生技术的推广和普及，微服务化已成为趋势。但线上微服务接口可靠性却并不完善，无法实时感知异常，存在较大风险。本文介绍微服务巡检平台的相关操作，帮助您随时了解API或微服务接口的运行情况，降低服务风险。

云原生时代下应用微服务化是趋势，但企业如何保障线上微服务的可靠性，主动感知线上微服务异常，降低业务风险呢？微服务巡检平台帮助您对线上服务进行7\*24小时的秒级探测，实时了解服务的健康度，且当服务异常时及时告警，尽快恢复，降低损失。

## 创建服务巡检任务

1.  登录[MSE治理中心控制台](https://mse.console.aliyun.com/?spm=a2c4g.11186623.2.13.f90a6a60WiEx0N#/msc/home)。

2.  在左侧导航栏选择**微服务治理中心** \> **微服务测试** \> **服务巡检**。

3.  在顶部菜单栏选择**地域**，然后在**服务巡检**页面单击**创建巡检任务**。

4.  在**创建巡检任务**面板中设置相关参数，然后单击**确定**。

    ![dubbo服务巡检](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2905579061/p182409.png)

    |参数|描述|
    |--|--|
    |**服务巡检任务名称**|自定义服务巡检任务名称。|
    |**应用**|选择需要巡检的应用。|
    |**框架类型**|支持Spring Cloud和Dubbo框架。系统会根据所选应用自动识别其框架，也可以手动选择**Dubbo**。|
    |**服务**|选定应用中需要巡检的目标服务。|
    |**方法**|选定服务中需要巡检的方法。|
    |**请求参数**|设置请求参数。关于Dubbo服务的方法参数类型及配置方式，请参见[Dubbo参考示例](#section_wg1_alf_1dk)。|
    |**断言信息包含**|设置接口返回值信息。如果返回值含有一个特征，如返回值含有123，则格式为"123"；如果返回值含有多个特征，如同时含有123，abc，则格式为\["123","abc"\]。|
    |**巡检周期**|设置巡检周期，单位秒/分钟，可自定义选择。|
    |**报警触发条件**|当接口巡检异常时，告警触发的频率。|
    |**报警接收管理**|接收告警的联系人组。在左侧列中选中需要接手告警的联系人组，并单击**\>**，添加到右侧列表中。|
    |**报警通知方式**|报警通知方式包含**钉钉**、**短信**和**邮件**。|

    服务巡检任务创建成功后，返回**服务巡检**列表，查看相关信息，包括**巡检次数**、**可用率**、**平均响应时间**等。


## 相关操作

您还可以执行以下操作管理服务巡检。

-   任务运行：在服务巡检列表页面，单击**操作**列的**启动**，可重新启动该服务巡检任务。
-   更新配置：在服务巡检列表页面，单击**操作**列的**详情**，可重新编辑服务巡检任务。
-   暂停服务：在服务巡检列表页面，单击**操作**列的**暂停**，可暂停该服务巡检任务。
-   查看失败记录：在服务巡检列表页面，单击**操作**列的**失败记录**，可查看该服务巡检的监控详情。

## Dubbo参考示例

|方法|参数类型填写方式|参数填写方式|
|--|--------|------|
|String sayHello\(String name\);|\["java.lang.String"\]|\["hello, dubbo"\]|
|String helloBean\(HelloBean helloBean\);|\["com.alibaba.dubbo.api.DemoService"\]|\[\{"booleanValue":true,"helloSubValue":\{"booleanValue":false,"intValue":2,"stringValue":"subbean"\},"intValue":1,"stringValue":"bean"\}\]|
|String helloBean\(HelloBean helloBean1, HelloBean helloBean2\);|\["com.alibaba.dubbo.api.DemoService","com.alibaba.pts.dubbo.api.DemoService"\]|\[\{"booleanValue":true,"helloSubValue":\{"booleanValue":false,"intValue":2,"stringValue":"subbean"\},"intValue":1,"stringValue":"bean"\},\{"booleanValue":true,"helloSubValue":\{"booleanValue":false,"intValue":2,"stringValue":"subbean"\},"intValue":1,"stringValue":"bean"\}\]|
|String helloMap\(Map helloMap\);|\["java.util.Map"\]|\[\{"booleanValue":true,"helloSubValue":\{"booleanValue":false,"intValue":2,"stringValue":"subbean"\},"intValue":1,"stringValue":"bean"\}\]|
|String helloMap\(Map helloMap1, Map helloMap2\);|\["java.util.Map", "java.util.Map"\]|\[\{"booleanValue":true,"helloSubValue":\{"booleanValue":false,"intValue":2,"stringValue":"subbean"\},"intValue":1,"stringValue":"bean"\},\{"booleanValue":true,"helloSubValue":\{"booleanValue":false,"intValue":2,"stringValue":"subbean"\},"intValue":1,"stringValue":"bean"\}\]|
|String helloList\(List helloList\);|\["java.util.List"\]|\[\[1\]\]|
|String helloList\(List helloList1, List helloList2\);|\["java.util.List","java.util.List"\]|\[\[1\],\[1,2\]\]|
|String helloString\(String helloString\);|\["java.lang.String"\]|\[\[1\],\[1,2\],\[1,3\]\]|
|String helloString\(String helloString1, String helloString2\);|\["java.lang.String","java.lang.String"\]|\["hello, dubbo", "hello, dubbo"\]|
|String helloInt\(int helloInt\);|\["int"\]|\["hello, dubbo", "hello, dubbo"\]|
|String helloInt\(int helloInt1, int helloInt2\);|\["int","int"\]|\["1","2"\]|
|String helloBoolean\(boolean helloBoolean\);|\["boolean"\]|\["true"\]|
|String helloBoolean\(boolean helloBoolean1, boolean helloBoolean2\);|\["boolean","boolean"\]|\["true","false"\]|
|String helloVoid\(\);|\[\]|\[\]|

## 微服务测试用户交流群

如果您在微服务引擎MSE使用微服务测试过程中有任何疑问，欢迎您使用钉钉扫描下方的二维码或搜索钉钉群号31180380加入钉钉群进行反馈。

![微服务测试交流群](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9780389061/p181621.png)

